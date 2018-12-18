---
title: Testo dell'interfaccia utente e la Guida di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 697c794d17f3004b0f37e668ff67afb703490e18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ui-text-and-help-for-visual-studio"></a>Testo dell'interfaccia utente e la Guida di Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a> Testo dell'interfaccia utente e la terminologia  
 Testo comprensibile è fondamentale per effettivo dell'interfaccia utente. Gli utenti di software tendono a leggere le etichette in primo luogo, vale a dire quelli più rilevanti per il completamento dell'attività in questione. Viene letto il testo statico con minore frequenza. Piano per gli utenti di avviare le sessioni di lavoro con un'analisi rapida della finestra intera, seguito da una lettura dell'interfaccia utente in questo ordine approssimativo:  
  
1.  Controlli interattivi nel centro  
  
2.  Eseguire il commit di pulsanti  
  
3.  Controlli interattivi disponibili in altri casi  
  
4.  Istruzioni principali  
  
5.  Spiegazioni aggiuntive  
  
6.  Titolo della finestra  
  
7.  Altro testo statico nel corpo principale  
  
### <a name="usage-patterns-for-ui-text"></a>Modelli di utilizzo per il testo dell'interfaccia utente  
  
#### <a name="title-bar-text"></a>Testo della barra del titolo  
 Testo della barra del titolo deve corrispondere il comando che ha generato l'interfaccia utente.  
  
#### <a name="instructional-text-helper-text"></a>Testo esplicativo (testo di supporto)  
 In alcune finestre di dialogo, è utile fornire importanti istruzioni principali per illustrare i valori nella finestra o nella pagina. Ciò è talvolta detta "testo di supporto".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Scrittura di regole di stile per il testo di supporto  
  
-   Non viene illustrata l'ovvio. A meno che sia assolutamente necessario, non includere il testo esplicativo.  
  
-   Testo informativo viene sempre posizionato nella parte superiore della finestra di dialogo e fare riferimento all'attività in corso.  
  
-   Precisamente spiegare agli utenti hanno bisogno per svolgere. Evitare la ridondanza e comunicazione eccessivo.  
  
-   Esaminare ogni finestra ed eliminare le istruzioni e le parole duplicate.  
  
-   Mantenere il testo esplicativo breve. Se altre informazioni necessarie per determinati utenti o gli scenari, quindi fornire un collegamento a un argomento online concettuale dettagliato.  
  
-   Scrivere il testo in modo che ogni parola contiene peso e non è necessaria.  
  
-   Seguire esistente linee guida Microsoft per [testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [stile e tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Istruzioni aggiuntive  
 Le istruzioni aggiuntive forniscono informazioni aggiuntive che consente all'utente di comprendere i controlli o raggruppamenti di controllo. Questo può anche includere il testo di suggerimento necessario per comprendere il formato è previsto il controllo di input. Utilizzare le istruzioni aggiuntive con cautela. Per i casi in cui è probabile che l'utente non sarà completamente la consapevolezza delle conseguenze la scelta che si tratta di riserva li.  
  
 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Testo supplementare in Visual Studio**  
  
 ![Testo supplementare in Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Testo supplementare in Visual Studio**  
  
#### <a name="infotips"></a>Infotip  
 Spesso, il testo esplicativo potrebbe risultare troppo lungo per posizionare sul posto nell'interfaccia utente o potrebbe essere utile solo per i nuovi utenti, ad esempio disordine agli utenti esperti di questa. In questo caso, il testo esplicativo/informativo deve essere inserito come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati in prossimità di controlli che sono correlati a e deve utilizzare l'icona di finestra popup specifico, è ancora non intrusivo evidenti.  
  
 ![Finestra popup in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Regole di stile di scrittura per Infotip  
  
-   Scrivere Infotip come frasi intere. Tali sviluppatori richiedono verbi specifici, normale e la punteggiatura finale.  
  
-   Utilizzare gli Infotip per completare l'istruzione principale o informazioni. Se si utilizza soltanto parole diverse per ridefinire l'idea principale, non occorre una finestra popup.  
  
-   Mantenere Infotip breve e semplice. Usare parole molto brevi e normale, il linguaggio naturale che supporta e incoraggia l'utente.  
  
-   Seguire esistente linee guida Microsoft per [testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [stile e tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Etichette del controllo  
 Etichette del controllo devono essere breve, conciso e seguire il [materiale sussidiario per il Desktop di Windows per i controlli](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Per ulteriori informazioni sulla posizione all'interno dell'interfaccia utente e di controllo del formato etichetta, fare riferimento a [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Collegamenti della Guida  
 I collegamenti della Guida possono essere posizionati all'interno del testo esplicativo oppure nel corpo dell'interfaccia utente. Possono essere forniti collegamenti alla Guida in linea o avviare le finestre di dialogo interni.  
  
##### <a name="visual-style-rules-for-help-links"></a>Regole di stile di visualizzazione per i collegamenti della Guida  
  
-   Utilizzare i colori ambiente corretto per i collegamenti ipertestuali. Un collegamento ipertestuale correttamente con stile non lampeggia brevemente rosso quando si fa clic. Se viene visualizzato questo errore, è un'indicazione che non vengono utilizzati i colori di ambiente.  
  
-   Sottolineature devono essere utilizzate solo al passaggio del mouse o quando il collegamento viene incorporato in un paragrafo.  
  
-   Per informazioni più dettagliate sugli stili visivi e interazione per i collegamenti ipertestuali, vedere i pulsanti e collegamenti ipertestuali.  
  
##### <a name="writing-style-rules-for-help-links"></a>Scrittura di regole di stile per i collegamenti della Guida  
  
-   Quando si avvia le finestre di dialogo, mantenere gli standard per i puntini di sospensione: nessun puntini di sospensione per lo spostamento, quindi sui puntini di sospensione se l'attività richiede un'interfaccia utente aggiuntiva.  
  
     ![Collegamento alla Guida in Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **I puntini di sospensione (...) in un collegamento alla Guida indica che l'attività richiede un'interfaccia utente aggiuntiva.**  
  
-   Collegamenti non devono iniziare con "Informazioni", che non è intenzione dell'utente. L'utente desidera rispondere a domande specifiche, non riceve una formazione generale.  
  
-   Guida di frase collega in modo che essi porre la domanda che l'argomento risponderà.  
  
     Non corretto:  
     "Per saperne di più sui prezzi di servizi mobili di Azure"  
  
     Correggere:  
     "Quali opzioni di determinazione dei prezzi sono disponibili per servizi mobili di Azure?"  
  
-   Non utilizzare mai *fare clic su...*  per il testo del collegamento.  
  
-   Non collegare mai solo la parola "qui". Questo rappresenta un problema per alcuni lettori dello schermo, che verranno voice solo le parole con collegamento ipertestuale.  
  
     Non corretto:  
     "Informazioni su servizi mobili di Azure **qui**"  
  
     Correggere:  
     "Quali opzioni di determinazione dei prezzi sono disponibili per servizi mobili di Azure?"  
  
-   Per ulteriori informazioni sullo stile di scrittura corretti per i collegamenti della Guida, vedere il [materiale sussidiario per Desktop di Windows per la Guida](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Testo di suggerimento  
 Testo di suggerimento viene visualizzato come filigrana all'interno di un controllo o sotto il controllo. La formattazione corretta verrà applicata utilizzando il token VSColors appropriato, `Environment.GrayText`.  
  
 Può essere visualizzato in una serie di moduli.  
  
-   Al posto l'etichetta del controllo:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   Con un verbo, fornendo istruzioni:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   Con il testo che indica una voce:  
  
     ![Testo in Visual Studio l'hint](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>Testo della filigrana  
 In un'area di progettazione vuota, il testo deve indicare di operazioni da eseguire, nonché di fornire i collegamenti per aprire altre finestre correlati, se appropriato:  
  
 ![Applicare la filigrana testo in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Esempio di testo della filigrana in Visual Studio**  
  
### <a name="common-terminology"></a>Terminologia comune  
  
|Termine|Descrizione|Commento|  
|----------|-----------------|-------------|  
|Accedi / disconnettersi|Verbi utilizzati come sinonimi con il web per la rappresentazione di autenticazione in una proprietà di web. All'interno di client, una volta come una nozione di primo livello viene usata per la firma e la connessione utente IDE, che rappresenta un'identità di livello superiore che fornisce funzionalità di livello superiore, ad esempio roaming e licenze che non sono disponibili in tutte le altre connessioni.|L'utente di IDE è l'unica funzionalità che deve rappresentare una richiesta di accesso / Disconnetti verbo, in quanto rappresenta l'utente di primo livello IDE.|  
|Connettere / disconnettere|Utilizzare in posizioni in cui una funzionalità mantiene una singola connessione a un servizio online.|Esplora server, in cui è possibile avere solo una connessione di Azure attiva alla volta, è riportato un esempio di connessione o disconnessione.|  
|Aggiungi o Rimuovi|Non distruttive. Utilizzare durante l'aggiunta o rimozione di un elemento da un elenco.|La finestra di dialogo Gestione connessione TFS elenco server è un esempio di Aggiungi/Rimuovi.|  
|Eliminare|Distruttivi. Usare solo quando l'elemento viene rimosso verrà definitivamente rimossi o eliminato dal disco.|"Delete" è in genere richiede un prompt dei comandi se il risultato è l'eliminazione di un file dal disco.|  
  
## <a name="error-messages"></a>Messaggi di errore  
  
### <a name="overview"></a>Panoramica  
 Si verificano errori. L'impostazione di limitazioni sulle operazioni che è possibile eseguire l'utente è sensibile innanzitutto di evitare che i messaggi di errore evitabili. Tuttavia, quando si verifica un errore, un messaggio di errore ben scritta possibile un lungo andare nel ridurre il problema. I messaggi di errore sono senza dubbio uno dei principali tipi di notifica all'utente che, in quanto sono sincroni e indicare un problema che deve essere risolto. I messaggi di errore scritta male lasciano gli utenti nel propria per stabilire la causa degli errori e le possibili soluzioni.  
  
 Gli utenti potrebbero smettere di riguardo all'utilizzo eccessivo o confondere i messaggi di errore, per consentire i messaggi solo necessario scrittura che aggiunge valore all'utente. Se il messaggio è semplicemente una notifica, quindi utilizzare una presentazione alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Regole per la creazione di un messaggio di errore  
  
-   Durante la costruzione di messaggi di errore, scegliere il livello di errore appropriato per il gruppo di destinatari. L'obiettivo riepiloghi semplici che forniscono all'utente di un'azione può richiedere, se applicabile. Non tutto ciò che l'utente non è necessario conoscere lo stato.  
  
-   Fornire assistenza costruttivo. È facile leggere e agire su un messaggio di errore contenente l'istruzione.  
  
-   Non utilizzare una doppia negativi.  
  
-   Eseguire entrambi un processo automatico e manuale grammatica e ortografia controllare eventuali messaggi di errore che scrittura.  
  
-   Per i messaggi di errore complessi, evitare di comunicazioni sequenziale. Non utilizzare mai un aggancio F1 per il messaggio di errore. Il messaggio stesso dovrebbe essere sufficiente.  
  
-   Utilizzare l'icona corretta.  
  
-   Rendere domande facili da comprendere e utilizzare i pulsanti che sono disponibili opzioni chiare, ad esempio "Delete" e "Annulla".  
  
-   Per gli avvisi, specificare chiaramente la conseguenza di procedere sarà. I pulsanti devono indicare la conseguenza.  
  
-   Per gli errori, viene descritto ciò che gli utenti possono eseguire per risolvere il problema. I pulsanti devono essere azioni o pronunciare "Chiudi". Non usare un pulsante "OK" per un messaggio di errore.  
  
-   Alcune domande durante la costruzione di un messaggio di errore:  
  
    -   L'utente può scoprire come risolvere il problema con l'errore solo?  
  
    -   L'utente utilizza il vocabolario stesso a questo errore?  
  
    -   È ambigua in questo errore o condivisi in diverse situazioni? In questo caso, come guidare gli utenti alla soluzione che necessarie?  
  
#### <a name="build-errors"></a>Errori di compilazione  
 Poiché Visual Studio è uno strumento di sviluppo software, molti dei suoi componenti dispongono di una compilazione, la conversione o passaggio per convertire il lavoro degli sviluppatori in formato binario codifica. Queste conversioni possono causare errori quando il compilatore non è in grado di elaborare i file creati in modo non corretto o quando le opzioni del compilatore non sono state impostate correttamente.  
  
 Gli utenti di Visual Studio possono dedicare un numero elevato di ore di sviluppo per la risoluzione degli errori di compilazione. Aumenta il tempo di risoluzione degli errori esistono dipendenze o quando i messaggi di errore vengono ridotte scritti, che può rendere difficile scoprire l'origine dell'errore.  
  
 Gli errori di compilazione migliori sono quelli che non si verificano in primo luogo, motivo per cui Visual Studio fornisce funzionalità Completamento automatico e zigzag IntelliSense. Convalida dello schema e gli strumenti analoghi forniscono lo stesso tipo di commenti e suggerimenti. Questi meccanismi in modo proattivo le istruzioni per l'utente per la costruzione di codice corretto, riducendo la probabilità di errori di compilazione.  
  
 Visual Studio fornisce una finestra degli strumenti in cui gli utenti possono leggere e spostarsi tra gli errori che si è verificato nella finestra del documento. Tasti di scelta rapida vengono forniti in modo che l'utente può rapidamente passare grandi quantità di codice e passare direttamente alla posizione del problema. Visual Studio consente anche di ogni errore di compilazione essere associati a un particolare ID parola chiave/contesto della Guida in modo che l'utente può accedere direttamente a un argomento della Guida che fornisce informazioni più dettagliate sull'errore.  
  
 Scrivere gli errori di compilazione chiaro, conciso:  
  
-   **Usare un linguaggio semplice** che spiega il problema con gergo del compilatore o addirittura nessuna. Il testo di un errore di compilazione non deve essere eccessivamente tecnico.  
  
-   **Descrive le possibili cause.** Ad esempio, "manca un virgola tra le proprietà e il valore di ' (proprietà): (valore)" dichiarazione. "  
  
-   Fornire dettagli sulle potenziali correzioni. Se non c'è spazio sufficiente, dettagli aggiuntivi possono essere messi in argomento della Guida corrispondente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componenti di un messaggio di errore ben scritti  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilizzare il servizio di finestra di dialogo della shell per i messaggi di errore.  
 Utilizzo del servizio della finestra di dialogo shell consente di controllare l'aspetto del messaggio, i tipi di carattere, in particolare, senza modifiche rilevanti per i singoli elementi. Utilizzare il **IErrorInfo** meccanismi e li segnala utilizzando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Scegliere una presentazione di notifica efficace e appropriato.  
 Utilizzare una finestra di dialogo modale con un avviso critico se è richiesto un intervento immediato per evitare la perdita di dati (notifica sincrono). Icone critiche sono riservate per le situazioni in cui la chiusura del messaggio senza lettura può determinare conseguenze negative. Perdita di dati è una situazione critica che richiede un intervento a livello di allarme. Utilizzo eccessivo di icona critico desensitizes agli utenti di importanza. Se il messaggio di errore informativo in natura, prendere in considerazione alternative per una finestra di dialogo modale (notifica asincrona).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Viene fornita una spiegazione pulita, concisa del motivo per cui si è verificato il problema anziché una spiegazione.  
 Gli utenti con i dettagli tecnici nella spiegazione di sovraccaricare renderà più probabile ignorare i messaggi di errore. Esempi di buone messaggistica:  
  
-   "Impossibile aprire il file richiesto".  
  
-   "Impossibile connettersi a Internet."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornire informazioni su come risolvere il problema.  
 Utente suggerimenti su come risolvere il problema. Se non sono disponibili suggerimenti, essere accurato con l'utente. Fornire collegamenti diretti a origini online alternative, ad esempio il supporto tecnico o il supporto della community. Provare a indirizzare gli utenti a specifiche informazioni online relative al problema. Per un ID di errore, prendere in considerazione la connessione degli utenti a un thread di discussione sull'errore specifico. Esempi di buone messaggistica:  
  
-   "Assicurarsi che si è connessi a Internet e riprovare l'operazione."  
  
-   "Assicurarsi che il file esista e di disporre dell'autorizzazione per aprirlo."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Scrivere un messaggio breve e per il punto.  
 Può inviare una notifica di un messaggio di errore, diagnosticare e offrono una soluzione ma comunque essere ignorato se è prolisso. Una soluzione consiste nell'utilizzare la diffusione progressiva con un pulsante di dettagli. Ad esempio, fornisce una breve descrizione, soluzione e quindi inserire ulteriori dettagli in un pulsante di dettagli. Se si sceglie di altre informazioni sull'errore, è possibile farlo.  
  
 La lingua del messaggio deve essere:  
  
-   **Dominio appropriato.** Utilizzare language di comprendere l'utente. Anche se i clienti sono sviluppatori, spesso non hanno il contesto e la terminologia che è disponibile.  
  
-   **Attributo specifico.** Evitare formulazione vagamente e assegnare i nomi e posizioni degli oggetti coinvolti. Ad esempio, un messaggio di errore ad esempio"carattere non valido" non è utile. Il carattere? "File non trovato". Il file?  
  
-   **Cortesia.** Non incolpare l'utente o farlo sentire stupido. Evitare ostile o offensive language (kill, esecuzione, terminare, irreversibile, non valida). Evitare di testo in maiuscolo, che viene spesso considerato come shouting e non come leggibili. Non usare umorismo.  
  
-   **Correggere.** Utilizzare la grammatica e ortografia corretta (anche in alfa). Errori di digitazione sono imbarazzante e poco professionale.  
  
-   **In base al contesto appropriato.** Utilizzare il testo del pulsante appropriato. Evitare il pulsante "OK" e quindi usare "Continue" o "Yes/No".  
  
### <a name="error-message-examples"></a>Esempi di messaggi di errore  
  
|Good|Non valido|  
|----------|---------|  
|"Il numero composto non è più in servizio. Controllare il numero e chiamare di nuovo o comporre 0 per l'operatore."|-"Errore (449): numero non valido"<br />-"L'eccezione non gestita di errore indica che l'operazione è stata completata".<br /><br /> ![Messaggio di errore non valido in Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Accedere alla Guida  
  
### <a name="overview"></a>Panoramica  
 Oltre alla documentazione di MSDN, un utente di Visual Studio include diversi punti di accesso per assistere l'utente mentre nell'interfaccia utente. Per garantire che i punti di accesso disponibili in modo coerente, è necessario sfruttare la Guida in linea offerti dall'ambiente di team di funzionalità. I punti di accesso sono:  
  
-   **Testo esplicativo e supplementare nelle finestre di dialogo.** Testo statico che fornisce una direzione o una spiegazione, sia nell'interfaccia utente di area o disponibile al passaggio del mouse sull'icona finestra popup.  
  
-   **F1 Guida** (solo editor). All'interno dell'editor di Visual Studio, un utente può considerare attendibile che in qualsiasi momento, se si preme F1 verrà visualizzato un argomento della Guida specifiche per la selezione corrente. Verificare che gli argomenti associati F1 siano appropriate e informativi.  
  
-   **Collegamenti ipertestuali agli argomenti della Guida.** Un collegamento ipertestuale all'interno di una finestra di dialogo, una finestra degli strumenti o area di progettazione che avvia un argomento per assistere l'utente ulteriori informazioni su una tecnologia, funzionalità o le informazioni su come eseguire un'attività.  
  
-   **Meccanismi UI helper, ad esempio gli smart tag e le finestre di dialogo di creazione.** Questi meccanismi di assistere l'utente per la comprensione di un elemento dell'interfaccia utente o un'attività, ad esempio smart tag o finestre di dialogo Generatore di facilitare.  
  
-   **Guida dell'interfaccia utente pulsanti** (obsoleto). Un indicatore visibile nella barra del titolo che fornisce l'accesso per l'argomento della Guida F1 correlato.  
  
### <a name="text"></a>Testo  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Testo esplicativo e aggiuntivo nelle finestre di dialogo  
 Nelle finestre di dialogo che supportano attività complesse, potrebbe essere necessario fornire il testo esplicativo entro l'interfaccia utente, spesso nella parte superiore della finestra di dialogo o in prossimità di controlli complessi. Vedere [dell'interfaccia utente testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sulla scrittura di stile.  
  
#### <a name="infotips"></a>Infotip  
 Spesso, testo esplicativo potrebbe essere troppo lungo per collocare nella posizione desiderata nell'interfaccia utente oppure potrebbe essere utile solo per i nuovi utenti, ad esempio disordine agli utenti esperti di questa. In questo caso, il testo esplicativo/informativo deve essere inserito come descrizione comando in una finestra popup.  
  
 Infotip devono essere posizionati in prossimità di controlli che sono correlati a e deve utilizzare l'icona di finestra popup specifico, è ancora non intrusivo evidenti.  
  
 ![Finestra popup in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Esempio di una finestra popup in Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Meccanismi di Guida interattive  
  
#### <a name="f1-help"></a>F1 Guida  
 F1 Guida in linea è necessario un editor o l'area di progettazione, ma non altrove nell'ambiente di Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Collegamenti ipertestuali agli argomenti della Guida  
 Collegamenti ipertestuali possono essere utilizzati per eseguire un'azione, passare all'interno dell'IDE o avviare la Guida in un browser. Vedere [dell'interfaccia utente testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) per informazioni dettagliate sulla lingua e 07.10.01 pulsanti e collegamenti ipertestuali per le linee guida visivi e layout.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Pulsanti [?] nella finestra di dialogo barre del titolo (deprecate)?  
 La maggior parte, i pulsanti della Guida [?] nella barra del titolo delle finestre di dialogo sono deprecati. Argomenti dell'interfaccia utente non fanno più parte del modello di documento e potrebbe pertanto non essere presente un argomento corrispondente a cui collegarsi. In pratica, il pulsante della barra del titolo è lo stesso risultato F1 Guida in linea e che non è più necessario nelle finestre di dialogo. In alcuni casi, comunque utilizzabile come un indicatore che sia disponibile, informazioni concettuali o procedurale anche se i collegamenti ipertestuali vengono utilizzati più comunemente nell'interfaccia utente più recente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Finestre di dialogo create tramite l'ambiente  
 Molte finestre di dialogo della shell vengono creati tramite il **VBDialogBoxParam** (funzione). Questa funzione condivisa è stata aggiornata per facilitare lo spostamento le **Guida** pulsante nella finestra di dialogo per la **?** pulsante mantenendo un'architettura che è a ritroso compatibile ed estensibile.  
  
 In particolare, il **VBDialogBoxParam** funzione esamina il modello di finestra di dialogo per un pulsante, il cui ID è **IDHELP** (9) o un'etichetta **Guida** o **& Guida**. Se viene trovato un pulsante della Guida, è nascosta e la **WS_EX_CONTEXTHELP** stile viene aggiunta alla finestra di dialogo, posiziona il **?** pulsante nella barra del titolo della finestra di dialogo.  
  
 Quando viene creata la finestra di dialogo, si inserisce la procedura di finestra di dialogo in uno stack e richiama la finestra di dialogo con una procedura di finestra di dialogo pre-elaborazione denominata **DialogPreProc**. Quando il **?** pulsante Invia un **WM_SYSCOMMAND** di **SC_CONTEXTHELP** alla finestra di dialogo. Il **DialogPreProc** acquisisce questo comando e le modifiche a un **WM_HELP** messaggio, che viene passato per la procedura di finestra originale.  
  
 La maggior parte delle finestre di dialogo Creazione ambiente dispone di un pulsante della Guida nella finestra di dialogo. Quando viene visualizzata la finestra di dialogo, il pulsante Guida è nascosta automaticamente e solo il **?** funzionamento del pulsante. Se il **?** pulsante mai rimosse o modificato in Windows, questa soluzione consente di spostare rapidamente ai pulsanti della Guida originali.  
  
 Questa soluzione quattro presupposti che potrebbe causare errori:  
  
-   Pulsante della Guida della finestra di dialogo è **IDHELP** (9).  
  
-   La finestra di dialogo l'aspetto corretto quando il pulsante Guida è nascosto.  
  
-   La finestra di dialogo non sostituisce il winproc.  
  
-   La finestra di dialogo non viene incorporato all'interno di un'altra finestra di dialogo.  
  
 Se la finestra di dialogo si trova all'interno di msenv e non usa **VBDialogBoxParam**, provare a utilizzare sfruttando **VBDialogBoxParam** prima di implementare un gestore personalizzato.  
  
##### <a name="dialogs-created-through-other-packages"></a>Finestre di dialogo create tramite altri pacchetti  
 È possibile implementare la propria soluzione per i dialoghi che si trovano all'esterno di msenv. Per una classe di finestra di dialogo condivise in VSPackage, prendere in considerazione lo spostamento di pulsante della barra del titolo o l'implementazione di un gestore in ogni finestra di dialogo. Il codice seguente è una struttura di un'implementazione che consentono di iniziare:  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Pulsanti della Guida nel codice gestito  
 Override del comportamento predefinito di finestra pulsante barra del titolo della Guida è facile da codice gestito. Di seguito è un'applicazione demo completo che illustri questo comportamento. In pratica, è necessario eseguire l'override del form **WndProc** (metodo) e quindi attivare la Guida F1 quando richiede un **SC_CONTEXTHELP** messaggio viene intercettato.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di carattere e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notifiche e avanzamento per Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)