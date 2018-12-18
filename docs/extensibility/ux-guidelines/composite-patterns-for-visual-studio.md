---
title: Modelli compositi per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a751bcc54fe53f9c9582dab71e2f393e885d1480
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="composite-patterns-for-visual-studio"></a>Modelli compositi per Visual Studio
Modelli compositi combinano elementi di progettazione e l'interazione in configurazioni distinte. Alcuni dei più importanti compositi modelli in Visual Studio per quanto riguarda la coerenza includono:  
  
-   [Visualizzazione dei dati](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Per gli oggetti dell'interfaccia utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a>Visualizzazione dei dati  
  
### <a name="overview"></a>Panoramica  
 I grafici sono uno strumento visivo per aggregare e visualizzare i dati per migliorare il processo decisionale. Consentono agli utenti di affrontare una grande quantità di dati ma poco vale a dire vedere ciò che richiede attenzione e ciò che potrebbe essere necessario un'azione.  
  
 L'utente trarranno vantaggio da un grafico, se una delle seguenti condizioni sono vere:  
  
-   Consente il grafico agli utenti di identificare le attività che possono agire sul?  
  
-   Il grafico consentirà agli utenti di previsione conseguenze delle possibili modifiche?  
  
-   Il grafico consente agli utenti individuare le tendenze e identificare i modelli?  
  
-   Il grafico consentirà agli utenti di prendere decisioni migliori?  
  
-   Il grafico consente di rispondere a una domanda specifica che gli utenti potrebbero avere nel contesto specificato?  
  
#### <a name="general-rules-for-charts"></a>Regole generali per i grafici  
  
-   Chiaramente i dati di etichetta. Illustrazioni senza spiegazione sono semplicemente belle immagini.  
  
-   Avviare assi da zero per evitare le proporzioni di inclinazione. Le dimensioni della lunghezza e barra di linea sono importanti indicatori visivi per comprendere le relazioni tra i punti dati.  
  
-   Creare grafici, non infografiche. Infografiche sono artistiche rappresentazioni dei dati e l'obiettivo primario è storytelling visual. Grafici può (e deve) essere visivamente accattivanti, mentre i dati parlino da soli.  
  
-   Evitare di skeumorphism, grafici a barre grafici, hashmarks contrasto e altri ritocchi infografica.  
  
-   Non utilizzare effetti 3D come elemento decorativo. Utilizzarle solo se sono realmente integrale per il possibilità dell'utente di comprendere le informazioni.  
  
-   Evitare di utilizzare più linee e riempimenti, più di due colori possono rendere difficile da leggere e interpretare correttamente questo tipo di grafico.  
  
-   Non utilizzare un grafico (o qualsiasi illustrazione) come unico mezzo di capire il concetto o l'interazione con i dati. Questa operazione presenta difficoltà per gli utenti con problemi visivi.  
  
-   Non utilizzare grafici come gratuiti o decorativi elementi in una pagina. In altre parole, se un grafico non aggiunta che qualsiasi valore o la Guida di utenti a risolvere un problema, non utilizzarlo.  
  
### <a name="chart-types"></a>Tipi di grafico  
 Tipi di grafici utilizzati in Visual Studio includono grafici a barre, grafici a linee, un grafico a torta modificato noto come un grafico ad anello "grafico ad anello," sequenze temporali, a dispersione tracciati (detti anche "cluster grafici") e i diagrammi di Gantt. Ogni tipo di grafico è utile per la comunicazione di un tipo diverso di informazioni.  
  
### <a name="other-charting-considerations"></a>Altre considerazioni di creazione di grafici  
  
#### <a name="color"></a>Colore  
 È una tavolozza di colori definiti per l'utilizzo in Visual Studio di grafici specifica. La tavolozza è accessibile per i tipi principali di distinguere i colori possono essere distinti, anche se si utilizzano come sezioni molto breve del colore. È possibile utilizzare i colori in qualsiasi combinazione per qualsiasi tipo di grafico o diagramma nell'interfaccia utente. Non è necessario utilizzare tutti i sette colori se non è necessaria una quantità di colori distinti. Questi colori non sono stati progettati per essere utilizzato con tutti gli elementi in primo piano, in modo non si inserisce testo o icone nella parte superiore di questi colori. Questi tonalità deve essere hardcoded ed esposto alla personalizzazione dell'utente in **strumenti > Opzioni** (vedere [esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Campione|Esadecimale|RGB|  
|------------|---------|---------|  
|![Campione 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Campione BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Campione FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Campione 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Campione 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Campione 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Campione B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a>Per gli oggetti dell'interfaccia utente e la lettura  
 In questa sezione fornisce il contesto di visualizzazione, noto anche come visualizzazione Anteprima codice, un tipo di interfaccia utente per gli oggetti univoci a Visual Studio.  
  
### <a name="overview"></a>Panoramica  
  
-   Interfaccia utente per gli oggetti debba consentire all'utente ulteriori informazioni o interattività senza pregiudicare le loro attività principale.  
  
-   Il motivo principale per l'interfaccia utente per gli oggetti in Visual Studio è noto come "informazioni al momento di attenzione".  
  
-   Interfaccia utente per gli oggetti in Visual Studio è inline o a virgola mobile e sia durevole o temporaneo.  
  
    -   Visualizzazione Anteprima di codice, un tipo di interfaccia utente per gli oggetti in Visual Studio, è in linea e durevole.  
  
    -   CodeLens, un tipo di interfaccia utente per gli oggetti in Visual Studio, è temporaneo e mobili  
  
 Comprendere il funzionamento di un frammento di codice o la ricerca di informazioni dettagliate su questo codice, spesso richiede uno sviluppatore di cambiare contesto e passare ad altro contenuto o un'altra finestra. Questi turni contesto possono essere problematico, perché gli utenti possono perdere lo stato attivo per le attività originale, se gli utenti lasciano la finestra principale. Inoltre, recupero che back contesto originale può essere difficile, soprattutto se il passaggio di windows ha causato il codice originale venga nascosto da altra interfaccia utente.  
  
 Interfaccia utente per gli oggetti segue uno schema denominato "informazioni al momento di attenzione". Questi messaggi, le finestre popup e finestre di dialogo concedono agli utenti informazioni aggiuntive, rilevanti che aggiunge chiarimenti o interattività senza perdere lo stato attivo sul loro attività principale. Esempi di interfaccia utente dell'oggetto popup visualizzate quando un utente si posiziona il puntatore del mouse su un'icona nell'area di notifica, la sottolineatura ondulata rossa sotto una parola e la visualizzazione Anteprima introdotta in Visual Studio 2013.  
  
### <a name="decision-points"></a>Punti di decisione  
 All'interno di Visual Studio, esistono diversi modi per usare questo modello di informazioni al momento di attenzione. Scegliere il meccanismo di destra e implementarlo in modo coerenza e prevedibile è essenziale per l'esperienza complessiva. In caso contrario, gli utenti potrebbero venire visualizzati con un'esperienza incoerente o poco chiara che comporta un peggioramento lo stato attivo dal contenuto stesso.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relazioni tra schema e i dettagli del contenuto  
 Informazioni al momento di attenzione viene utilizzate per visualizzare una relazione tra il contenuto che l'utente è incentrata sul (il contenuto "master") e altre correlate contenuto (il contenuto "detail"). In questo modello, il contenuto del dettaglio è chiaramente correlato al contenuto, l'utente sta usando e può essere visualizzato vicino al contenuto master. Informazioni aggiuntive o informazioni che non possono essere riepilogate senza sovraccaricare il contenuto master devono seguire un altro modello, ad esempio una finestra degli strumenti.  
  
-   **Sempre** visualizzare il contenuto di dettaglio in prossimità del contenuto master.  
  
-   **Sempre** assicurarsi che il contenuto di dettaglio ancora consente all'utente di rimanere concentrati sul contenuto del master. Spesso, il modo migliore per ottenere questo risultato è per il rendering del contenuto di dettaglio come vicino del contenuto master come possibili. Questa operazione può essere eseguita per il rendering del contenuto di dettaglio in una finestra popup accanto al contenuto principale o eseguendo il rendering inline contenuto dettaglio sotto il contenuto principale.  
  
-   **Mai** utilizzare informazioni al momento di attenzione che accetta l'utente dal contenuto master. Se è necessario visualizzare il contenuto di dettaglio separatamente, esporre un'azione esplicita che consente all'utente di eseguire questa operazione.  
  
#### <a name="design-details"></a>Dettagli di progettazione  
 Dopo aver determinato che l'interfaccia utente per gli oggetti è la scelta giusta, sono disponibili quattro considerazioni di progettazione principale:  
  
1.  **Persistenza:** il contenuto deve essere permanente o temporaneo?   
    Gli utenti dovranno mantenere visibili per fare riferimento o interagire con le informazioni? O gli utenti dovranno riepilogo rapidamente le informazioni e quindi continuare con l'attività principale?  
  
2.  **Tipo di contenuto:** il contenuto sarà informativo, spostamento o utilizzabili?   
    L'utente necessita di ulteriori dettagli sul contenuto master? L'utente necessario completare un'attività che influisce sul contenuto master? O l'utente deve essere indirizzato a un'altra risorsa?  
  
3.  **Tipo di indicatore:** un indicatore ambiente ha senso?   
    Le informazioni è possono essere riepilogate in modo utile e visualizzate senza sovraccaricare il contenuto principale?  
  
4.  **I movimenti:** movimenti ciò che verrà utilizzato per richiamare e chiudere l'interfaccia utente?   
    Come verrà visualizzare il contenuto di dettaglio e inviarlo immediatamente l'utente? È il valore per l'aggiunta di un'azione, ad esempio il blocco per passare tra gli stati temporanei e permanenti?  
  
 Ognuno di questi punti di quattro decisione avrà un impatto sui componenti principali dell'interfaccia utente per gli oggetti.  
  
### <a name="on-object-ui-components"></a>Componenti dell'interfaccia utente per gli oggetti  
  
1.  Tipo di contenitore (Visualizzatore di contenuto)  
  
    -   Virgola mobile  
  
    -   Inline  
  
2.  Tipo di contenuto  
  
    -   Messaggio informativo: i dati che potrebbero essere statica o dinamica  
  
    -   Eseguibili: i comandi Modifica del contenuto master  
  
    -   Navigazione: collegamenti che accettano l'utente a un'altra finestra o applicazione, ad esempio MSDN  
  
3.  Movimenti  
  
    -   Chiamata  
  
    -   Licenziamento  
  
    -   Il blocco  
  
    -   Altre interazioni  
  
4.  Modello di persistenza e commit  
  
    -   Temporaneo  
  
    -   Durevole  
  
    -   Automatico  
  
    -   Su richiesta  
  
5.  Indicatori di ambiente (facoltativi)  
  
    -   Sottolineatura a zigzag  
  
    -   Icona smart tag  
  
    -   Altri indicatori di ambiente  
  
#### <a name="container-content-presenter-type"></a>Tipo di contenitore (Visualizzatore di contenuto)  
 Sono disponibili due opzioni principali disponibili per presentare il contenuto nel punto di attenzione:  
  
1.  **Inline:** un relatore inline, ad esempio la visualizzazione di anteprima che è stato introdotto nell'Editor di Visual Studio 2013 codice rende lo spazio per il nuovo contenuto spostando il contenuto esistente.  
  
    -   **Preferisce** relatori inline, se si prevede che gli utenti desiderano dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto presente.  
  
    -   **Evitare** relatori inline, se si prevede che gli utenti dovranno osservare le informazioni a cui è presente, quindi continuare con l'attività principale con interruzioni minime.  
  
2.  **Numeri reali:** relatore mobile viene posizionato più vicino al contenuto selezionato possibile ma non modifica il layout del contenuto esistente. Possono essere utilizzate diverse strategie, ad esempio la visualizzazione di un pannello mobile contenuto tramite il più vicino di spazio disponibile per il simbolo selezionato.  
  
    -   **Preferisce** mobile relatori se si prevede che gli utenti dovranno osservare le informazioni a cui è presente, quindi continuare con l'attività principale con interruzioni minime.  
  
    -   **Evitare** mobile relatori se si prevede che gli utenti dovranno dedicare una quantità significativa di tempo che fa riferimento a o l'interazione con il contenuto è presente.  
  
#### <a name="content-type"></a>Tipo di contenuto  
 Esistono tre tipi di contenuto che possono essere visualizzati all'interno di qualsiasi contenitore dell'interfaccia utente per gli oggetti. È possibile visualizzare qualsiasi combinazione di questi tipi di informazioni. Sono tre tipi:  
  
1.  **Messaggio informativo:** la maggior parte dell'oggetto contenitori dell'interfaccia utente visualizzerà un tipo di contenuto informativo. Il contenuto può rappresentare informazioni sullo stato attuale dell'ambiente o può rappresentare informazioni su uno stato potenziali future dell'ambiente. Ad esempio, può essere utilizzato per mostrare l'effetto di un comando specifico, ad esempio un'operazione di refactoring, sul codice esistente.  
  
    -   **Sempre** utilizzare la rappresentazione canonica di informazioni da visualizzare. Ad esempio, codice dovrebbe essere simile al codice, è stata completata con evidenziazione della sintassi e deve rispettare qualsiasi tipo di carattere e altre impostazioni di ambiente, che l'utente ha impostato.  
  
    -   **Sempre** prendere in considerazione che supporta operazioni sul contenuto di tipo informativo che sarebbe possibile se stesse informazioni viene presentate come contenuto master. Ad esempio, se la presentazione di codice esistente all'interno di un contenitore di interfacce utente per gli oggetti di considerare la possibilità di esplorare e modificare il codice di supporto.  
  
    -   **Sempre** è consigliabile utilizzare un colore di sfondo diverso se la presentazione di contenuto informativo che rappresenta uno stato futuro potenziale.  
  
2.  Eseguibili: alcuni contenitori di interfaccia utente per gli oggetti fornirà la possibilità di eseguire alcune azioni sul contenuto master, ad esempio eseguire un'operazione di refactoring.  
  
    -   **Sempre** posizionare i comandi utilizzabili separatamente dal contenuto informativo.  
  
    -   **Sempre** abilitare e disabilitare le azioni quando appropriato.  
  
    -   **Sempre** fare riferimento alle linee guida standard per la rappresentazione di comandi all'interno di finestre di dialogo.  
  
    -   **Sempre** mantenere minimo il numero di azioni che vengono esposte in un contenitore dell'interfaccia utente per gli oggetti in assoluto. L'interazione con l'interfaccia utente dell'oggetto deve essere un'esperienza semplice e veloce. L'utente non necessario impiegare energia sulla gestione di contenitore per gli oggetti dell'interfaccia utente stesso.  
  
    -   **Sempre** considerare come e quando un contenitore di interfacce utente per gli oggetti verrà chiuse o chiusa. Come procedura consigliata, qualsiasi azione che si conclude la finestra di dialogo tra lo schema e i dettagli del contenuto deve chiudere il contenitore dell'interfaccia utente per gli oggetti quando viene richiamata l'azione.  
  
3.  **Spostamento:** alcuni per gli oggetti contenitori dell'interfaccia utente includono i collegamenti che consentono all'utente a un'altra finestra o applicazione, ad esempio l'apertura di un articolo MSDN nel web browser dell'utente.  
  
    -   **Sempre** anteporre qualsiasi collegamento ipertestuale con "Aperto" in modo che gli utenti verranno non essere sorprendente esplorato alcuni altri contenuti.  
  
    -   **Sempre** separare i collegamenti dai collegamenti utilizzabili.  
  
#### <a name="ambient-indicators-optional"></a>Indicatori di ambiente (facoltativi)  
 Gli indicatori di ambiente possono essere complesso, inclusi testo presentate in un colore a contrasto dal resto del codice, o ovvia, include i simboli tickler come sottolineature a zigzag e icone di smart tag. Gli indicatori di ambiente comunicano la disponibilità di informazioni aggiuntive attinenti. Idealmente, forniscono informazioni utili anche senza la necessità di interagire con essi.  
  
-   **Sempre** posizionare un indicatore di ambiente in modo che non distrarre o sovraccarico dell'utente. Se non è possibile posizionare un indicatore di ambiente in modo, si consideri un'altra soluzione.  
  
-   **Sempre** posizionare l'indicatore di ambiente a più vicino possibile al contenuto che è correlato al.  
  
-   **Sempre** tenta di creare un indicatore che riepiloga le informazioni disponibili. Si consiglia di fornire un conteggio del numero di elementi di dati disponibili (ad esempio, "3 riferimenti" anziché semplicemente "Riferimenti") o pensare a un altro modo per riepilogare i dati.  
  
    -   In casi in cui i dati per un indicatore non sono sempre calcolati e visualizzati immediatamente fornire commenti e suggerimenti progressivo come vengono calcolati i valori. Si consideri, ad esempio, le modifiche che riflettono gli aggiornamenti ai dati disponibili, simili a quello che consente di aggiornare il riquadro in tempo reale di posta elettronica in Windows Phone come il numero di messaggi di posta elettronica non letta aumenta l'animazione.  
  
-   **Mai** aggiungere ulteriori indicatori a un utente può richiedere ragionevole per una determinata parte del contenuto. Gli indicatori di ambiente devono essere utili senza richiedere alcuna interazione da parte dell'utente. Gli indicatori di perdono i loro ambiente se richiedono overflow e altri controlli di gestione per importarli in vista.  
  
#### <a name="gestures"></a>Movimenti  
 Un aspetto fondamentale che consente all'utente di concentrarsi sul contenuto master è supportando i movimenti di destra per aprire e chiudere il contenuto di dettagli aggiuntivi.  
  
-   **Sempre** richiedono all'utente di eseguire alcuni movimenti esplicito per aprire i contenuti aggiuntivi. I movimenti di aprire comuni includono:  
  
    -   **Al passaggio del mouse:** le descrizioni comandi o un contenuto informativo non interattivo  
  
    -   **Comando esplicito:** relatore inline  
  
    -   **Fare doppio clic sull'indicatore di ambiente:** finestra popup CodeLens  
  
-   **Sempre** Elimina il contenuto di dettaglio ogni volta che l'utente preme il tasto Esc.  
  
-   **Sempre** prendere in considerazione il contesto dell'interfaccia utente per gli oggetti. Per contenuto relatori che consentono l'interazione all'interno del contenitore, valutare attentamente se si desidera visualizzare informazioni aggiuntive al passaggio del mouse, che è probabile che sia problematica per flusso di lavoro dell'utente.  
  
-   **Mai** visualizzare il contenuto al passaggio del mouse che sembra essere modificabile o invita l'interazione dell'utente. Questo comportamento può risultare frustrante per gli utenti se si tenta di spostare il cursore sul contenuto del dettaglio, come il comportamento per una descrizione comandi standard consiste nel chiudere immediatamente quando il cursore non è più sul master contenuto che l'ha prodotta.  
  
##  <a name="BKMK_SelectionModels"></a>Modelli di selezione  
  
### <a name="overview"></a>Panoramica  
 Un modello di selezione è il meccanismo utilizzato per indicare e confermare le operazioni su uno o più oggetti di interesse all'interno dell'interfaccia utente. Questo argomento vengono illustrati i modelli di interazione di selezione all'interno degli editor di documento di Visual Studio: editor di testo, aree di progettazione e modellazione superfici.  
  
 Gli utenti devono disporre di un modo per indicare a Visual Studio che stanno eseguendo e Visual Studio deve rispondere in modo prevedibile con commenti e suggerimenti per gli utenti sui quali opera su. Differenze o una comunicazione tra l'utente e l'interfaccia utente può comportare l'utente non osservando un'azione, che può avere conseguenze impreviste. Spesso, l'errore non viene notato fino a quando l'utente vede che un elemento manca o è stato modificato. Modelli di selezione sono pertanto una delle parti principali di progettazione dell'interfaccia utente. Sebbene i modelli di selezione in Visual Studio sono coerenti con Windows, vi sono piccole differenze.  
  
 In Visual Studio, come in Windows, modelli di selezione sono diversi a seconda del contesto in cui si verifica l'interazione. Selezioni possono verificarsi in quattro tipi di oggetti:  
  
-   Testo  
  
-   Oggetti grafici  
  
-   Elenchi e strutture  
  
-   Griglie  
  
 All'interno di questi oggetti, esistono tre tipi di selezioni:  
  
-   Contigue  
  
-   Non contigue  
  
-   Region  
  
#### <a name="scope"></a>Ambito  
 Il componente più importante della selezione è la garanzia che l'utente conosca la finestra lavorano (attivazione) e in cui lo stato attivo è disponibile (selezione). Visual Studio estende la funzionalità di gestione di finestra di Windows, ma lo schema di attivazione è lo stesso: l'interazione con una finestra Visualizza lo stato attivo alla finestra. Visual Studio include due indicatori per l'attivazione: uno per le finestre dei documenti e uno per le finestre degli strumenti.  
  
 Per le finestre di documento, la finestra attiva è indicata da una scheda della finestra documento proveniente all'inizio e la modifica del colore di sfondo:  
  
 ![Selezione della scheda attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  
  
 **Selezione della scheda attiva**  
  
 Finestre degli strumenti, la finestra attiva è indicata da una modifica il colore dell'area della barra del titolo della finestra degli strumenti:  
  
 ![Selezione della finestra degli strumenti attiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  
  
 **Finestra degli strumenti attiva che mostra la selezione primaria di un nodo**  
  
 ![Selezione della finestra degli strumenti inattiva in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  
  
 **Finestra di strumento inattivo, con latente selezione del nodo**  
  
 Quando è attiva una finestra, in base ai modelli di selezione descritti in questa sezione delle linee guida è indicato lo stato attivo.  
  
#### <a name="context"></a>Contesto  
 Visual Studio è stato progettato per mantenere sicuro concetto di contesto, tiene traccia di in cui l'utente sta utilizzando. Solo una finestra è attiva, se si tratta di una finestra del documento o degli strumenti. Tuttavia, la finestra di primo livello di documento mantiene sempre una selezione latente. Anche se lo stato attivo potrebbe essere in una finestra degli strumenti, la finestra del documento che era attivo ultimo consente di visualizzare una selezione, anche in uno stato inattivo. Questa operazione viene eseguita per mantenere il contesto dell'utente nel documento che sono la modifica, mostrarli che Visual Studio mantiene il proprio stato in modo che possano restituire e spostarsi facilmente tra le finestre degli strumenti e finestre di documento.  
  
### <a name="text-selection"></a>Selezione di testo  
 Editor di Visual Studio che sono strettamente testuali, ad esempio l'editor di testo incorporato, utilizzare lo stesso modello di selezione di testo e aspetto descritte nel [Mouse e puntatori](https://msdn.microsoft.com/en-us/library/dn742466.aspx) pagina di Windows User Experience interazione Guidelines in MSDN. Lo stato attivo nell'editor di testo è indicato da una barra verticale, definita punto di inserimento. Il punto di inserimento è un singolo pixel colorato, come l'inversa di tutti gli elementi presenti sottostante e spesso. Lampeggia in base al tasso di impostazione di **intermittenza del cursore** impostazione nel **velocità** scheda del **tastiera** applet del Pannello di controllo.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Selezione contigua e non contiguo  
 Selezione all'interno dell'editor di testo è contiguo. Di testo non contigui selezioni non sono consentite, ma devono essere risolti negli editor oggetto grafico. Quando il puntatore del mouse su un'area di testo, il cursore cambia in un cursore. Un solo clic posiziona il punto di inserimento nell'editor di testo in corrispondenza della posizione di clic. Tenendo premuto il pulsante del mouse viene avviata una selezione evidenziata e rilasciare il pulsante del mouse termina la selezione evidenziata.  
  
#### <a name="region-selection-box-selection"></a>Area selezione (finestra)  
 Visual Studio supporta selezioni per l'area nell'editor di testo e si tratta della selezione. Selezione della casella consente all'utente di selezionare un'area di testo che segue il flusso di testo normale. Come con la selezione di testo standard, la selezione deve essere contigua. Selezione della casella viene avviata tenendo premuto ALT mentre si trascina con il mouse. Selezione della casella può essere avviata anche tenendo premuto il tasto MAIUSC e Alt mentre utilizzando i tasti di direzione per indicare l'area di selezione. Selezione della casella viene utilizzato l'evidenziazione di selezione normale e Mostra il cursore del punto di inserimento lampeggiante alla fine dell'area di selezione.  
  
 ![Casella internazionali &#40; &#41; selezione in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  
  
 **Selezione area (casella) in Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Aspetto di selezione del testo  
 È possibile personalizzare i colori utilizzati per la selezione nell'editor attiva e inattiva. Per personalizzare l'aspetto visivo dell'editor, un utente può passare a **strumenti > Opzioni**e quindi cercare in **ambiente > tipi di carattere e colori > Editor di testo**.  
  
### <a name="graphical-selection"></a>Selezione di grafica  
  
#### <a name="interaction"></a>Interazione  
 Selezione di un oggetto grafico può essere complessa e dipende da numerosi fattori:  
  
-   **Modello di selezione principale dell'editor.** Editor che contengono gli oggetti grafici possono essere utilizzati anche per modificare testo o griglie. Ad esempio, l'editor potrebbe essere un editor di testo che supporta anche la posizione degli oggetti di grafici, ad esempio la finestra di progettazione XAML di Visual Studio. Il supporto di più tipi di oggetto può influire sulla modalità con cui l'utente seleziona gruppi costituiti da diversi tipi di oggetti.  
  
-   **Supporto per gli stati di selezione primaria e secondaria.** Un editor può fornire selezione primaria e secondaria stati in modo che gli oggetti possono essere modificati in contemporanea allineati tra loro, ridimensionare, e così via.  
  
-   **Supporto di modificando sul posto.** Editor possono anche consentire il contenuto dei rispettivi oggetti di grafiche per essere modificato. Ad esempio, un rettangolo potrebbe contenere anche il testo all'interno che può essere modificato dall'utente. Inoltre, che il testo potrebbe essere centrato o giustificato. La modifica sul posto richiede un livello più dettagliato dell'interazione dell'utente e pertanto richiede un set appropriato di segnali visivi per la presentazione di informazioni sullo stato all'utente.  
  
#### <a name="mouse-interaction"></a>Interazione del mouse  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic su un oggetto non selezionato|Seleziona l'oggetto e visualizza una linea tratteggiata e quadratini di ridimensionamento, se l'oggetto è ridimensionabile.|  
|Fare clic su un oggetto selezionato|Attiva la modifica sul posto se supporta l'oggetto. Facendo clic all'esterno dell'oggetto disattiva la modalità di modifica sul posto.|  
|Fare doppio clic su un oggetto|Apre il codice oggetto per la modifica e potrebbe inserire un gestore eventi predefinito, se appropriato.|  
|Riferimento a un oggetto|Sposta il puntatore fino al cursore di spostamento. L'aspetto dell'oggetto, ad esempio la luminosità o colore, potrebbe cambiare.|  
|Scegliere un handle di selezione|Sposta il puntatore fino al cursore di ridimensionamento. Per gli oggetti che supportano la rotazione, alcuni quadratini di ridimensionamento potrebbero cambiare il puntatore a un cursore Ruota come il puntatore è posizionato in modo diverso (ad esempio, spostata più lontani) rispetto all'handle di selezione.|  
|Trascinare|Anche se l'oggetto non è selezionata in precedenza, il puntatore fino al cursore di spostamento e sposta l'oggetto.|  
|Editor perde lo stato attivo|Disattiva la modalità di modifica sul posto, anche se l'oggetto conserva il contenuto e l'aspetto che aveva durante l'ultimo stato di selezione/operazione.|  
|Selezione oggetti|Indicato da un bordo, linea punteggiata o altro trattamento visivamente distinto per evidenziare il limite dell'oggetto.|  
|Ridimensionare un oggetto selezionato|Indicato da quadratini di ridimensionamento.<br /><br /> Un oggetto ridimensionabile con otto quadratini di ridimensionamento, che rappresenta ciascuna direzione in cui può essere ridimensionata. Un minor numero di handle possono essere utilizzati se l'oggetto può essere ridimensionata solo in determinate direzioni. Quando si ridimensiona un oggetto down in otto handle non è interattivi, quattro handle possono essere utilizzati. Le dimensioni di handle devono essere collegate alle metriche a bordo e il bordo di finestra con il **GetSystemMetrics** funzione API dimensioni proporzionalmente la risoluzione dello schermo.<br /><br /> ![Quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Ruotare un oggetto selezionato|![Punti di rotazione](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interazione della tastiera  
  
|Input|Risultato|  
|-----------|------------|  
|Scheda|Sposta l'indicatore di stato attivo tra l'ordine logico di oggetti nell'editor. È possibile da sinistra a destra o alto verso il basso in base alle **TabIndex** (o equivalente) valore della proprietà, ordine di creazione di un oggetto e lo scopo complessivo dell'editor. Maiusc + Tab inverte la direzione dell'indicatore di stato attivo.|  
|BARRA SPAZIATRICE|Attiva la modalità Panoramica mentre tasto di scelta rapida viene mantenuto. Input del mouse aggiuntivi è necessario per eseguire la traslazione alla posizione del riquadro di visualizzazione.|  
|CTRL+BARRA SPAZIATRICE|Attiva la modalità zoom mentre tasto di scelta rapida viene mantenuto. Input del mouse aggiuntive deve aumentare e diminuire il fattore di zoom.|  
|Ctrl + Alt + segno meno|Consente di ridurre il fattore di zoom di un livello.|  
|Ctrl + Alt + segno più|Aumenta il fattore di zoom di un livello.|  
|MAIUSC o Ctrl|Aggiunge l'oggetto al gruppo di selezione. CTRL consente inoltre di rimuovere gli oggetti singolarmente dal gruppo di selezione.|  
|INVIO|Esegue il comando predefinito per l'oggetto (in genere aprire o modificare).|  
|F2|Attiva la modifica sul posto per l'oggetto.|  
|Tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, incrementi minimi (ad esempio, 1 pixel alla volta)|  
|CTRL + tasti di direzione|Sposta gli oggetti selezionati nella direzione del tasto premuto, con incrementi di dimensioni maggiori (ad esempio, 10 pixel alla volta)|  
|MAIUSC + freccia chiavi|Ridimensiona gli oggetti selezionati in direzione, incrementi minimi (ad esempio, 1 pixel alla volta)|  
|CTRL + MAIUSC + tasti di direzione|Ridimensiona gli oggetti selezionati nella direzione corrispondente, con incrementi di dimensioni maggiori (ad esempio, 10 pixel alla volta)|  
  
 Quando gli utenti modificano i controlli sul posto, potrebbe essere utile per gli oggetti ridimensionare automaticamente con l'input dell'utente. Ad esempio, se l'utente modifica un controllo etichetta, quindi l'etichetta di aumento delle dimensioni per visualizzare il testo digitato solo dall'utente. Se questa non operazione viene eseguita, l'utente deve ridimensionare il controllo manualmente dopo la modifica del testo. Se l'utente dispone di molti controlli, questa diventa un rote e attività compromessa.  
  
#### <a name="graphical-containers"></a>Contenitori di grafici  
 In alcuni casi, editor grafici forniscono contenitori per altri oggetti di grafiche, ad esempio il controllo Panel Windows Form o il controllo di Layout di griglia nella finestra di progettazione HTML. Se l'editor fornisce contenitori per altri oggetti di grafiche, il modello di selezione seguente deve essere usato per solo il contenitore (gli oggetti all'interno di seguire il contenitore il modello standard, come descritto in precedenza):  
  
|Input|Risultato|  
|-----------|------------|  
|Fare clic sul contenitore|Seleziona l'oggetto contenitore senza direttamente selezionare uno degli oggetti contenuti. Il contenitore può essere spostato e/o ridimensionato con standard del mouse e tastiera (come descritto in precedenza). Gli oggetti contenuti vengono spostati in relazione al contenitore, ma gli oggetti contenuti non vengono ridimensionati a meno che non siano selezionati anche direttamente.|  
|Passa il mouse sull'area di limiti del contenitore|Diventa il cursore di spostamento, che indica che il contenitore può essere spostato il mouse.|  
|Trascinare l'area del bordo del contenitore|Modifica il mouse fino al cursore di spostamento e sposta il contenitore (e gli oggetti contenuti all'interno). Il contenitore non può essere spostato senza prima selezionato con un solo clic.|  
|Fare clic su un oggetto all'interno del contenitore|Deseleziona il contenitore (se selezionata) e seleziona solo l'oggetto selezionato.|  
|MAIUSC + clic o Ctrl + clic su un oggetto indipendente e/o di un contenitore|Aggiunge l'oggetto selezionato a un gruppo di selezione o la selezione esistente. Se l'oggetto selezionato è già un membro del gruppo di selezione, verrà rimosso dal gruppo di selezione.|  
  
 Gli oggetti contenuti devono essere conforme al modello di selezione di base, come descritto nella sezione precedente. Da Progettazione Windows Form di test di usabilità, gli utenti previsto accesso trasparente per gli oggetti contenuti senza effettuare dei passaggi coinvolti (imposti dall'oggetto di contenimento).  
  
#### <a name="disjoint-and-region-selections"></a>Non contigue e le selezioni di area  
 Editor oggetto grafico devono supportare selezioni non contigue. Si noti che questo grafico non mostra l'aspetto del controllo per Visual Studio. Vedere [aspetto Selezione oggetto grafico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) di specifiche dettagliate di visual.  
  
 ![Non contigue e area selettori](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  
  
 **Selezione non contiguo**  
  
 Editor grafici deve anche fornire le selezioni di area con un indicatore di selezione del tipo di selezione. Se l'editor grafico supporta altri tipi di oggetto (ad esempio testo), quindi selezioni area potrebbero non essere possibile in base a vincoli di tali altri tipi di oggetto.  
  
 ![Selezione](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  
  
 **Selezione di testo scorrevole**  
  
#### <a name="primary-and-secondary-selections"></a>Selezioni primari e secondari  
 Alcuni editor oggetto grafica consente all'utente di modificare o allineare gli oggetti nei gruppi. In questo caso, il concetto di selezioni primarie e secondarie deve essere introdotto. La selezione primaria è l'oggetto a cui tutti gli altri oggetti rispondono per le operazioni di gruppo. L'oggetto selezionato dall'utente prima di tutto diventa il controllo primario e selezioni successive diventano le selezioni secondarie. La selezione primaria ha un trattamento visual distinto dalle selezioni secondarie per indicare quale oggetto primario:  
  
 ![Selezione primaria e secondaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  
  
 **Selezione primaria con due selezioni secondarie**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a>Aspetto di selezione di oggetti grafici  
 Quadratini di ridimensionamento sono quadratini disegnati in un modello rettangolare intorno al rettangolo di selezione dell'oggetto. Il grafico seguente vengono illustrati esempi dei vari stati che può disporre di un oggetto grafico con handle di ridimensionamento e aspetto modifica sul posto. Le dimensioni degli handle devono essere collegate al bordo della finestra e l'utilizzo di metriche di bordo di **GetSystemMetrics** API.  
  
|Stato|Aspetto|Dettagli su Visual|  
|-----------|----------------|--------------------|  
|**Non selezionato**|Impostazione predefinita|![Stato del pulsante predefinito](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState")||  
|**Selezione primaria**|Ridimensionabili|![Selezione primaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize")|![Selezione primaria con ridimensionare gli handle &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713 12_PrimaryResizeZoom")|  
|**Selezione primaria**|Non ridimensionabile|![Selezione primaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize")|![Selezione primaria senza ridimensionare gli handle &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713 14_PrimaryNoResizeZoom")|  
|**Selezione primaria**|Bloccato|![Selezione primaria bloccata](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked")|![Selezione primaria bloccata &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713 16_PrimaryLockedZoom")|  
|**Selezione secondaria**|Ridimensionabili|![Selezione secondaria con quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize")|![Selezione secondaria con ridimensionare gli handle &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713 18_SecondaryResizeZoom")|  
|**Selezione secondaria**|Non ridimensionabile|![Selezione secondaria senza quadratini di ridimensionamento](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize")|![Selezione secondaria senza quadratini &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713 20_SecondaryNoResizeZoom")|  
|**Selezione secondaria**|Bloccato|![Selezione secondaria bloccata](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked")|![Selezione secondaria bloccata &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713 22_SecondaryLockedZoom")|  
|**Attivo dell'interfaccia utente**|Impostazione predefinita|![Lo stato attivo dell'interfaccia utente](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive")|![Interfaccia utente nello stato attivo &#40; ingrandito &#41; ] (../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713 24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Visualizzazione di modelli di selezione  
  
#### <a name="tree-view"></a>Visualizzazione albero  
 Selezione di una visualizzazione albero viene visualizzato con una semplice evidenziazione. Se l'utente fa clic sul nome di un nodo o a un'icona di nodo, viene selezionato il nodo. Le icone triangolari a sinistra del nodo di espandere o il controllo struttura ad albero di contratto ma non influenzano la selezione dell'utente, con una sola eccezione: dopo la compressione di un nodo padre quando la selezione è su un elemento figlio di tale nodo, la selezione si sposta all'elemento padre.  
  
 ![Visualizzazione ad albero tipica in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  
  
 **Visualizzazione ad albero tipica in Visual Studio**  
  
 Visualizzazioni dell'albero possono supportare selezioni contigue e non contigue, anche su più livelli nell'albero. Contigui o non contigui nei nodi dell'albero visibile è necessario effettuare le selezioni multiple. Se si comprime un nodo, la selezione non contiguo andrà persa e il nodo che è stato compresso Ottiene la selezione. In questo modo, l'utente può visualizzare i nodi che saranno interessati da un'operazione. Quando i nodi sono compressi, diventa chiaro quali nodi potrebbero risentirne.  
  
 Quando è selezionato un nodo padre, applicare l'operazione per l'elemento padre, in presenza di casi in cui è utile per un'operazione da applicare al padre e i relativi figli. In questo caso, fornire un'interfaccia utente aggiuntiva durante l'operazione, ad esempio una casella di controllo o finestra di dialogo di conferma per rendere esplicito l'opzione "Applica a tutti i figli" all'utente.  
  
##### <a name="renaming"></a>Ridenominazione  
 Se i nodi dell'albero supportano la ridenominazione, ridenominazione deve essere eseguita sul posto. L'operazione sul posto deve essere lo standard in tutti i controlli struttura ad albero in Visual Studio. Specificare un comando di ridenominazione che immediatamente attiva la modalità di modifica sul posto, con la selezione di testo che copre l'intero nome del nodo, pronto per accettare l'input dell'utente. Se il nodo rappresenta un file, il nome del file deve contenere l'estensione. La selezione evidenziata deve includere solo il corpo del nome file e non l'estensione.  
  
|Input|Risultato|  
|-----------|------------|  
|INVIO (tasto)|Esegue il commit dell'operazione di ridenominazione|  
|Tasto ESC|Annulla l'operazione di ridenominazione|  
|Facendo clic all'esterno dell'area di modifica sul posto|Esegue il commit dell'operazione di ridenominazione|  
|Annulla|Fornire facile annullamento per annullare l'operazione di ridenominazione|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Selezione all'interno di elenchi e i controlli griglia  
 Il concetto chiave selezione nell'elenco è che è basato su righe, il che significa che quando la selezione viene effettuata all'intera riga è selezionato come unità. Al contrario, griglie possono consentire a celle specifiche da selezionare senza influire su qualsiasi altro aspetto della riga. Griglie potrebbero contenere anche una gerarchia di righe nidificate (ad esempio una rapida TreeGrid) che consentono l'intera rami della gerarchia selezionati e deselezionati interagendo con le righe padre. Negli elenchi di selezione viene visualizzata per un colore di evidenziazione semplice per l'intera riga di dati. Lo stato attivo viene visualizzato per un singolo pixel punteggiato bordo la riga modificabile corrente o la cella (riga se tutte le celle sono di sola lettura).  
  
> [!NOTE]
>  **Lo stato attivo** e **selezione** sono concetti diversi. *Lo stato attivo* è un'indicazione dell'interfaccia utente è assegnato l'elemento per ricevere input diretto in modo non esplicito in un altro oggetto, mentre *selezione* fa riferimento allo stato di inclusione di un oggetto in un set di oggetti su cui successivi possono eseguire operazioni.  
  
 Le selezioni negli elenchi possono essere contigui, non contiguo, o area geografica. Quando selezioni multiple sono consentite, contigui e non contiguo selezione sempre deve essere supportate, mentre il supporto per le selezioni area (casella) è facoltativo. Selezioni area vengono avviate mediante il trascinamento nello spazio vuoto del corpo dell'elenco.  
  
|Object|Selection|  
|------------|---------------|  
|List|Contigue|Sempre supportate (quando sono consentita la selezione multipla).|  
|List|Non contigue|Sempre supportate (quando sono consentita la selezione multipla).|  
|List|Region|Supporto facoltativo. Avviata trascinando il puntatore del mouse nello spazio vuoto del corpo dell'elenco.|  
  
 Fare clic su una sola volta in un elenco selezionare la riga in cui si è verificato il clic. Se l'utente di fare clic su una cella di elenco che supporta la modifica sul posto, la cella viene attivata anche immediatamente per la modifica sul posto. In caso contrario, l'intera riga immediatamente sia selezionata e Mostra evidenziazione.  
  
 Trascinare nel corpo elenco effettua una delle tre operazioni:  
  
-   Avvia una selezione per area, se l'elenco supporta e il mouse verso il basso nello spazio vuoto  
  
-   Avvia un'operazione di trascinamento della selezione se la cella dell'elenco o la riga supporta da un'origine di trascinamento  
  
-   Seleziona la riga corrente  
  
##### <a name="in-place-editing"></a>La modifica sul posto  
 Quando è consentita la modifica sul posto, sono disponibili due modelli di base: selezione di controllo e proprietà semplice modifica. Un controllo di modifica semplice, il contenuto è evidenziato e pronto per l'input non appena viene attivata la modifica sul posto dell'utente. Dove è implementato un selettore di proprietà, il pulsante che richiama la selezione di proprietà viene visualizzato una volta che viene attivata la modalità di modifica sul posto e la selezione corrente non sia più evidenziata. Il pulsante di selezione deve essere allineata a destra della cella. Per esempi di modificando sul posto, vedere il **finestra proprietà** e **elenco attività** in Visual Studio.  
  
##### <a name="keyboard-support"></a>Supporto per la tastiera  
 Supporto per la tastiera per la selezione in elenchi e le griglie vengono applicate le convenzioni standard di Windows:  
  
-   Tasti di direzione esplorare l'elenco, selezionare ogni riga o cella, come lo stato attivo viene spostato.  
  
-   MAIUSC + freccia consente di eseguire una selezione contigua la direzione dei tasti di direzione.  
  
-   CTRL + tasti di direzione seguita da abilitare o disabilitare la barra spaziatrice tra l'aggiunta e rimozione di elementi dell'elenco dalla selezione, la creazione di una selezione non contiguo.  
  
-   Per le griglie che contengono le gerarchie annidate, il tasto freccia destra espande una riga padre e il tasto freccia sinistra comprime uno.  
  
-   Il tasto Tab sposta lo stato attivo tra le celle nella riga corrente, se le celle sono modificabili.  
  
-   Il tasto INVIO esegue il comando predefinito sull'elemento nell'elenco (spesso **aprire**).  
  
-   Il tasto F2 attiva la modifica sul posto per la cella attualmente selezionata.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a>Persistenza e il salvataggio delle impostazioni  
  
### <a name="overview"></a>Panoramica  
 Anche se ogni componente del software in Visual Studio è in genere responsabile per il proprio stato e la persistenza, Visual Studio Salva automaticamente le impostazioni in alcuni casi, ad esempio con posizioni e le dimensioni di finestra. Nella tabella seguente è una combinazione di impostazioni che richiedono un utente esplicito o programmato azione da intraprendere e le impostazioni salvate automaticamente.  
  
|Object|Gli elementi da salvare|Quando salvare|Percorso di salvataggio|  
|------------|------------------|------------------|-------------------|  
|Oggetto selezionabile (ad esempio, una riga di codice)|Un punto di interruzione su una riga di codice<br /><br /> Un collegamento utente associato alla riga di codice|Quando il progetto viene salvato|Il **opzioni utente (con estensione suo)** file per il progetto|  
|Finestra di dialogo|La posizione della finestra di dialogo, se è stato spostato<br /><br /> La vista che l'utente dell'ultimo utilizzo nella finestra di dialogo|Quando si chiude la finestra di dialogo<br /><br /> Quando la sessione di Visual Studio termina|In memoria<br /><br /> Nel Registro di sistema **HKEY_Current_User**|  
|Window|Le dimensioni e la posizione della finestra|Quando si chiude la finestra<br /><br /> Quando viene modificata la modalità di Visual Studio<br /><br /> Quando la sessione di Visual Studio termina|Il **opzioni utente (con estensione suo)** file per il progetto<br /><br /> File di opzioni personalizzate per le impostazioni della finestra|  
|Document|La selezione corrente nel documento<br /><br /> La visualizzazione del documento<br /><br /> L'ultimo diverse posizioni visitato dall'utente|Quando il documento viene salvato|Il **opzioni utente (con estensione suo)** file per il progetto|  
|Progetto|Riferimenti ai file<br /><br /> Riferimenti a directory sul disco<br /><br /> Riferimenti agli altri software<br /><br /> Componenti<br /><br /> Informazioni sullo stato relative al progetto stesso|Quando il progetto viene salvato|Il file di progetto|  
|Soluzione|Riferimenti ai progetti<br /><br /> Riferimenti ai file|Quando viene salvata il progetto o soluzione|Il **soluzione (sln)** file|  
|Le impostazioni in **strumenti > Opzioni**|Personalizzazioni tastiera<br /><br /> Personalizzazioni della barra degli strumenti<br /><br /> Combinazioni di colori|Quando il **strumenti > Opzioni** finestra di dialogo viene chiusa<br /><br /> Quando la sessione di Visual Studio termina|Nel Registro di sistema **HKEY_Current_User**|  
  
 Ciò che l'utente sta eseguendo e quando vengono effettuate operazioni, determina se un'impostazione venga salvata in memoria (durante la sessione), salvata su disco (in più sessioni come un'impostazione del Registro di sistema), come parte del file di progetto o soluzione stessa, come parte di **soluzione Opzioni (con estensione suo)** file o le impostazioni personalizzate di un file che solo tale componente software è a conoscenza. Nella tabella precedente sono diversi eventi in corrispondenza del quale è possano salvare le impostazioni. Tuttavia, esistono altre volte in cui si consiglia di salvare lo stato:  
  
-   Quando l'utente modifica posizione all'interno di una finestra o finestra di dialogo  
  
-   Quando l'utente trasferisce lo stato attivo a un'altra finestra  
  
-   Quando l'utente passa dalla progettazione alla modalità di debug  
  
-   Quando l'utente si disconnette il proprio account  
  
-   Quando il computer entra in sospensione o arresto  
  
-   Quando il disco rigido/computer sta per essere riformattata e configurare di nuovo  
  
### <a name="window-configurations"></a>Configurazioni di finestre  
 Una configurazione di finestre è la presentazione di base dell'ambiente di sviluppo: si tratta di uno schema composto l'elenco di finestre degli strumenti presente e il modo in cui sono posizionati. Per windows gestiti dall'IDE (windows IDE), informazioni sul layout vengono resi persistenti per utente, pertanto quando si avvia un utente dell'IDE, il layout della finestra viene visualizzato lo stesso come quando si ha terminato di Visual Studio. Lo stato e la posizione dell'IDE windows è persistente in un file di opzioni personalizzate in formato XML. Le finestre degli strumenti che vengono create dai pacchetti caricati nell'IDE di rendere persistenti le informazioni sullo stato nel Registro di sistema e possono o non sia per ogni utente.  
  
#### <a name="profile-specific-layouts"></a>Layout per il profilo  
 Ogni profilo include layout delle finestre dello strumento, organizzati in modo familiare agli utenti specifici per sviluppatori (agli sviluppatori di Visual C++ che venga visualizzato il **Esplora** sul lato sinistro dell'IDE, mentre gli sviluppatori c# che venga visualizzato il  **Esplora soluzioni** a destra). Layout di finestra per il profilo vengono caricati dopo che l'utente sceglie un profilo all'avvio. Un autore del pacchetto deve determinare il layout di finestra più adatto per l'esperienza del cliente, i relativi, sapendo che le modifiche apportate dall'utente per la configurazione di finestre quindi vengono rese persistenti.  
  
##  <a name="BKMK_TouchInput"></a>Input tocco  
 Gli utenti stanno utilizzando prodotti di sviluppo Microsoft nei dispositivi di tocco. Tuttavia, esistono barriere che rendono difficile usare gli strumenti di sviluppo nei dispositivi di tocco. Gli utenti si aspetta di ricevere dei prodotti per fornire un'esperienza di tocco affidabile e precisa. Lo scopo di queste linee guida è informare decidere quali funzionalità di tocco per incorporare e promuovere un'esperienza coerente tocco in Visual Studio e prodotti correlati.  
  
### <a name="levels-of-experience"></a>Livelli di esperienza  
 I seguenti livelli di esperienza servono per fungono da Guida per aiutare i team a decidere quali funzionalità di tocco per offrire in base al relativo livello desiderato di interesse di un investimento in contatto.  
  
-   Il **esperienza base** è per i team che vogliono fornire toccano funzionalità pertanto non vi sono termina dei messaggi non recapitabili in tutto il lavoro.  
  
-   Il **ottimizzato esperienza** è destinata ai team che desidera funzionalità più comuni di tocco (ad esempio quelli disponibili in genere nelle applicazioni browser internet).  
  
-   Il **elevati esperienza** è per i team che desiderano aggiungere tali funzionalità come i movimenti o altre funzionalità facoltative che rendono le applicazioni a primo tocco descrittivo.  
  
||Esperienza di base|Esperienza ottimizzata|Esperienza con privilegi elevato|  
|-|----------------------|--------------------------|-------------------------|  
|Consente agli utenti di...|Correzione di codice e soluzione/progetto a livello di lettura senza strade|Eseguire attività di manutenzione, refactoring che e navigazione|Operano in un'esperienza coerente, intuitiva e semplice con confidenza|  
|Editor|Panoramica di tocco e la selezione<br /><br /> Barra di scorrimento tocco per passare e premere + trascinare|Zoom indietro avanti<br /><br /> Scorrimento rapido<br /><br /> Selection<br /><br /> Semplice utilizzo dei menu di scelta rapida||  
|Finestre degli strumenti superiore|Panoramica di elenco<br /><br /> Selezione di elementi<br /><br /> Barra di scorrimento tocco per passare e premere + trascinare|Selezione e lo scorrimento di un elemento semplice||  
|Windowing||Ridimensionare finestra<br /><br /> Barra di accesso rapido||  
|Documenti||Semplificare la navigazione tra file aperti||  
|Movimenti||Verificare i movimenti comuni funzionino nell'IDE|Azioni basate su movimento<br /><br /> Il supporto di trascinamento e rilascio e finestre di progettazione|  
|Altre considerazioni|||Tastiera su schermo personalizzata|  
  
#### <a name="gestures"></a>Movimenti  
 I movimenti di forniscono agli utenti un collegamento ai comandi che richiedono un'interazione più complessa. Fare riferimento alle linee guida di Windows in [movimenti tocco comuni per applicazioni Desktop](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), seguire queste linee guida per la maggior parte dei movimenti, tra cui i movimenti semplici, ad esempio mediante panoramica e zoom.