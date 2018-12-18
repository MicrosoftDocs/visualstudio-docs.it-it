---
title: Essentials UX per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9d04da421b3b59609269b4f91a487d22adc80e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ux-essentials-for-visual-studio"></a>Essentials UX per Visual Studio
## <a name="best-practices"></a>Procedure consigliate  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Essere coerente all'interno dell'ambiente di Visual Studio.  
  
-   Seguire esistente [modelli di interazione](interaction-patterns-for-visual-studio.md) all'interno della shell.  
  
-   Progetta le funzionalità siano coerenti con il linguaggio visual della shell e [requisiti di prodotti](evaluation-tools-for-visual-studio.md).  
  
-   Utilizzare i controlli e i comandi condivisi quando sono presenti.  
  
-   Comprendere la gerarchia di Visual Studio e come stabilisce contesto e l'interfaccia utente di unità.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilizzare il servizio di ambiente per i tipi di carattere e colori.  
  
-   Interfaccia utente deve rispettare corrente [tipo di carattere ambiente](fonts-and-formatting-for-visual-studio.md) impostazione a meno che non è esposto per la personalizzazione nella pagina tipi di carattere e colori nella finestra di dialogo Opzioni.  
  
-   Elementi dell'interfaccia utente è necessario utilizzare il [VSColor Service](colors-and-styling-for-visual-studio.md), uso condivisi i token di ambiente o i token di specifiche funzionalità.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendere coerente con il nuovo stile e tutte le immagini.  
  
-   Seguire i principi di progettazione di Visual Studio per le icone, icone e altri elementi grafici.  
  
-   Non inserire testo in elementi grafici.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Da una prospettiva incentrata sull'utente di progettazione.  
  
-   Creare il flusso di attività prima le singole funzionalità all'interno di esso.  
  
-   Acquisire familiarità con gli utenti e rendono le informazioni nella specifica esplicita.  
  
-   L'interfaccia utente di esaminare, valutare un'esperienza completa, nonché i dettagli.  
  
-   Progettare l'interfaccia utente in modo che rimanga funzionale e accurato, indipendentemente dalle impostazioni locali o di linguaggio.  
  
## <a name="screen-resolution"></a>Risoluzione dello schermo  
  
### <a name="minimum-resolution"></a>Risoluzione minima  
 - La risoluzione minima per Visual Studio Dev14 è **1280x720**. Ciò significa che è *possibili* a utilizzare Visual Studio questa risoluzione, sebbene non sia un'esperienza utente ottimale. Non è possibile garantire che tutti gli aspetti sia utilizzabili con risoluzioni inferiori 1280x720.  
  
 - La risoluzione di destinazione per Visual Studio è **1366 x 768**. Questa è la soluzione più bassa in cui ti assicuriamo un *buona* esperienza utente.

 - Altezza della finestra iniziale deve essere **inferiore a 700 pixel**, in modo da adattarlo la risoluzione minima di 96 DPI della cornice dell'IDE.
  
### <a name="high-density-displays"></a>Display ad alta densità  
 Interfaccia utente in Visual Studio deve funzionano correttamente in DPI tutti i fattori che Windows supporto di ridimensionamento: 150%, 200% e % 250.  
  
## <a name="anti-patterns"></a>Anti-pattern  
 Visual Studio contiene molti esempi dell'interfaccia utente che il nostro linee guida e procedure consigliate. Favorire la coerenza, gli sviluppatori spesso prestito da modelli di progettazione dell'interfaccia utente del prodotto simile a ciò che sta creando. Si tratta di un buon approccio che consente a unità di coerenza per l'interazione dell'utente e la progettazione di visual, in alcuni casi fornite funzionalità con alcuni dettagli che non soddisfano nostre linee guida a causa dei vincoli di pianificazione o l'esclusione di assegnazione di priorità. In questi casi, non è desiderabile che i team di copiare uno di questi "anti-pattern" in quanto essi proliferazione dell'interfaccia utente non valido o non coerenti all'interno dell'ambiente di Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>I campi o le impostazioni necessarie visualizzate in stato di errore per impostazione predefinita  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
  
-   Avvisare gli utenti che siano aggiunti un elemento che deve essere configurato.  
  
-   Attirare l'attenzione dell'utente per le aree che richiedono l'input.  
  
#### <a name="anti-pattern-solution"></a>Anti-pattern della soluzione  
 Non appena l'utente ha avviato un'azione e prima che l'attività è stata completata, inserire immediatamente arresto critico icone accanto le aree che richiedono una configurazione.  
  
#### <a name="example-manifest-designer-declarations"></a>Esempio: Le dichiarazioni di progettazione del manifesto  
 Aggiunta di una dichiarazione all'elenco immediatamente lo colloca in uno stato di errore, viene mantenuto finché l'utente imposta le proprietà necessarie.  
  
 In questo caso, è un problema aggiuntivo perché l'icona utilizzata per l'avviso contiene un "&times;" icona, quindi sull'icona Rimuovi comune può essere usato accanto a esso. Di conseguenza, l'interfaccia utente usa un pulsante Rimuovi, un controllo più inefficace.  
  
 ![Immissione dell'interfaccia utente in uno stato di errore per impostazione predefinita è un anti-modello di Visual Studio. ] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti modello")<br />Immissione dell'interfaccia utente in uno stato di errore per impostazione predefinita è un anti-modello di Visual Studio.
  
#### <a name="alternatives"></a>Alternative  
 Una soluzione migliore per questo problema, è possibile:  
  
-   Consentire all'utente di aggiungere una dichiarazione senza avviso e quindi spostare immediatamente impostare le proprietà dell'elemento.  
  
-   Aggiungere l'icona di avviso (triangolo gold) quando lo stato attivo viene spostato dall'elemento di, ad esempio per aggiungere un'altra dichiarazione all'elenco o per tentare di modificare le schede nella finestra di progettazione.  
  
-   Se l'utente tenta di modificare le schede prima di impostare le proprietà di qualsiasi dichiarazione, pop una finestra di dialogo che spiega che l'applicazione non verrà compilato (o qualsiasi le implicazioni) finché non vengono risolti gli avvisi. Se l'utente chiude la finestra di dialogo e sostituisce le tabulazioni comunque, un'icona (critica o avviso, a seconda dei casi) viene aggiunto alla scheda dichiarazioni.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Più clic per chiudere l'interfaccia utente  
  
#### <a name="feature-team-goals"></a>Funzionalità degli obiettivi del team  
 Non consentire all'utente di ignorare l'interfaccia utente senza prima di visualizzare il testo di spiegazione.  
  
#### <a name="anti-pattern"></a>Anti-pattern  
 Il team di inserimento di collegamenti video in varie posizioni nell'interfaccia utente di Visual Studio decise rispetto al pattern comune del "&times;" Chiudi spiegazione pulsante e una descrizione come specificato da UX e invece implementato un elenco a discesa e collegamento "Non mostrare più".  

#### <a name="example-video-links-in-team-explorer"></a>Esempio: collegamenti video in Team Explorer
Forzare l'utente di leggere il testo esplicativo prima della chiusura dell'interfaccia utente è un anti-pattern in Visual Studio. I collegamenti a video, progettati correttamente devono visualizzare una descrizione comando con informazioni aggiuntive al passaggio del mouse e fare clic su di "&times;" deve chiudere il messaggio senza necessità di ulteriore interazione.


 ![Esplicativo testo anti &#45; modello di &#45; corretto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modello di collegamento video non corretto
  
#### <a name="result"></a>Risultato  
 Anziché un semplice pulsante Chiudi (un solo clic), l'utente è costretto a utilizzare due clic distinti per semplicemente chiudere l'interfaccia utente in ogni punto in cui vengono visualizzati i collegamenti video.  
  
#### <a name="alternatives"></a>Alternative  
 La progettazione corretta per questa situazione, è possibile seguire il modello comune per Visual Studio, Office e Internet Explorer: al passaggio del mouse, l'utente può visualizzare la descrizione della descrizione e un solo clic consente di nascondere l'interfaccia utente.  
  
 ![Esplicativo testo anti &#45; modello di &#45; corretto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti modello corretto")<br />Modello corretto collegamento video
  
### <a name="using-command-bars-for-settings"></a>Utilizzo delle barre dei comandi per le impostazioni  
 **Nella figura** rappresenta l'anti-pattern: inserimento di un'impostazione di sotto di un pulsante di comando che si applica solo al comando. In questo esercizio, sono disponibili comandi oltre ad avviare il debug, come visualizzazione nel Browser, Avvia senza eseguire debug ed Esegui istruzione, che rispetta l'impostazione selezionata.  

  ![R: figura Comando anti-pattern della barra](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-modello-FigureA")<br />R: figura Comando barra anti-pattern
  
 Indesiderabili leggermente migliori, ma è ancora, è l'inserimento di impostazioni di questo tipo in barre degli strumenti, come illustrato nella **Figura B**. Mentre i pulsanti di menu combinato richiede meno spazio e di conseguenza un miglioramento rispetto a discesa, entrambe le progettazioni usano ancora una barra degli strumenti per alzare di livello un elemento che non è realmente un comando.  
 
 ![Figura b: una situazione migliore, ma comunque un anti-pattern della barra dei comandi](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-modello-FigureB")<br />Figura b: migliore, ma comunque un anti-pattern della barra dei comandi
 
  Nell'approccio corretto nel **figura C**, l'impostazione è collegata a una serie di comandi. È presente alcuna impostazione globale e si passa semplicemente tra quattro comandi. Questo è l'unico caso in cui i comandi nella barra degli strumenti sono accettabili. 

 ![Figura c: correggere l'utilizzo di pattern barra dei comandi di Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-modello-FigureC")<br />Figura c: corretto utilizzo di pattern barra dei comandi di Visual Studio
   
### <a name="control-anti-patterns"></a>Anti-pattern di controllo  
 Per alcuni anti-pattern sono semplicemente corretto utilizzo o la presentazione di un controllo o un gruppo di controlli.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sottolineatura utilizzata come etichetta di gruppo, non è un collegamento ipertestuale  
 Sottolineare il testo deve essere utilizzato solo per i collegamenti ipertestuali.  
  
 **Non valido:**    
 ![Testo sottolineato che non è un collegamento ipertestuale è un anti-modello di Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Testo sottolineato che non è un collegamento ipertestuale è un anti-modello di Visual Studio.
  
 **Buona:**   
 ![Applicato lo stile corretto, testo collegamento ipertestuale non viene visualizzato solo nel tipo di carattere ambiente. ] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Applicato lo stile corretto, testo collegamento ipertestuale non viene visualizzato solo nel tipo di carattere ambiente.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Fare clic su una casella di controllo, viene generata una finestra di dialogo popup  
 Scegliere la casella di controllo "Abilita Desktop remoto per tutti i ruoli" della procedura guidata "Pubblica l'applicazione Azure" immediatamente viene visualizzata una finestra di dialogo popup, un anti-modello di Visual Studio. Inoltre, il campo casella di controllo non viene riempita con una casella di controllo dopo la selezione, un'altra interazione anti-pattern.  
  
 ![Aprire una finestra di dialogo al termine fare clic su una casella di controllo un anti-pattern Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Aprire una finestra di dialogo al termine fare clic su una casella di controllo un anti-pattern Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Collegamenti ipertestuali per anti-pattern  
 Nell'esempio seguente contiene due anti-pattern.  
  
1.  Primo piano rosso accensione al passaggio del mouse significa che il colore corretto condiviso dal servizio di tipo di carattere non è in uso.  
  
2.  "Ulteriori informazioni" non è il testo appropriato per un collegamento a un argomento concettuale. Obiettivo dell'utente è non per altre informazioni, che consiste nel comprendere le implicazioni di propria scelta.  
  
 ![Verrà ignorato il servizio di colore e l'utilizzo di "Ulteriori informazioni" per i collegamenti ipertestuali sono anti-pattern Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Verrà ignorato il servizio di colore e l'utilizzo di "Ulteriori informazioni" per i collegamenti ipertestuali sono anti-pattern Visual Studio.  
  
 **Migliore soluzione:** porre la domanda facendo clic sul collegamento si chiede di specificare l'utente.  
  
-   Come funzionano i servizi di Microsoft Azure?  
  
-   Quando è necessario un progetto di servizi mobili di Azure?  
  
#### <a name="using-click-here-for-links"></a>Usa "Fare clic qui" per i collegamenti  
 Collegamenti ipertestuali devono essere autodescrittivi. È un anti-pattern da usare "Fare clic qui" o qualsiasi variazione simile.  
  
 **Problema:** "Fare clic qui per istruzioni su come creare un nuovo progetto."
  
 **Buona:** "Come creare un nuovo progetto?"