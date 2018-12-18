---
title: Le notifiche e l'avanzamento di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 00ab0622820777f556eff667e6de5f769196e6b0
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="notifications-and-progress-for-visual-studio"></a>Le notifiche e l'avanzamento di Visual Studio
##  <a name="BKMK_NotificationSystems"></a>Sistemi di notifica  
  
### <a name="overview"></a>Panoramica  
 Esistono diversi modi per informare l'utente di ciò che accade in Visual Studio per le attività di sviluppo software.  
  
 Durante l'implementazione di qualsiasi tipo di notifica:  
  
-   **Mantenere il numero di notifiche alla minima** numero effettivo. Messaggi di notifica devono essere applicate per la maggior parte degli utenti di Visual Studio o agli utenti di un'area di funzionalità e delle funzionalità specifiche. Un uso eccessivo di notifiche sidetrack l'utente o diminuire percepita facilità di utilizzo del sistema.  
  
-   **Assicurarsi di visualizzare i messaggi utilizzabili, deselezionare** che l'utente può utilizzare per richiamare il contesto appropriato per la scelta delle opzioni più complesse e ulteriori azioni.  
  
-   **Presentare messaggi sincroni e asincroni in modo appropriato.** Le notifiche sincrone indicano che un elemento richiede attenzione immediata, ad esempio quando si blocca un servizio web o un codice viene generata un'eccezione. L'utente dovrebbe essere informato di tali situazioni immediatamente in modo che richiede l'input, ad esempio in una finestra di dialogo modale. Notifiche asincrone sono quelle in cui l'utente deve conoscere ma non necessario per agire immediatamente, ad esempio quando viene completata un'operazione di compilazione o distribuzione di siti web viene completata. Tali messaggi devono essere più ambiente e non interrompere il flusso di attività dell'utente.  
  
-   **Utilizzare le finestre di dialogo modale solo quando necessario, per impedire all'utente di ulteriori azioni** prima di riconoscere il messaggio o di prendere una decisione presentata nella finestra di dialogo.  
  
-   **Rimozione delle notifiche di ambiente quando non sono più validi.** Non richiedono all'utente di eliminare una notifica se sono già stati effettuati azione per risolvere il problema che sono stati informati.  
  
-   **Tenere presente che le notifiche possono causare false correlazioni.** Gli utenti potrebbero ritenere che uno o più delle relative azioni ha attivato una notifica quando in realtà non esiste alcuna relazione causale. Essere chiaro nel messaggio di notifica su contesto, il trigger e l'origine della notifica.  
  
### <a name="choosing-the-right-method"></a>Scelta del metodo  
 Utilizzare questa tabella per agevolare la scelta del metodo per notificare all'utente del messaggio.  
  
|Metodo|Usa|Non utilizzare|  
|------------|---------|----------------|  
|[Finestre di messaggio di errore modale](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Utilizzarlo quando è necessaria una risposta dell'utente prima di procedere.|Non utilizzare quando non è necessario bloccare l'utente e interrompere il flusso. Evitare di utilizzare le finestre di dialogo modale se è possibile visualizzare il messaggio in un altro modo meno intrusiva.|  
|[Barra di stato IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Utilizzare quando si verifica informazioni testuali ambiente sullo stato di un processo.|Non utilizzare da soli. Utilizzate in combinazione con un altro meccanismo di feedback.|  
|[Barra informazioni incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|In una finestra degli strumenti o una finestra del documento, utilizzare per notificare lo stato di avanzamento, lo stato di errore, risultati e/o informazioni utilizzabili.|Non utilizzare se le informazioni non sono pertinente per il percorso in cui sono posizionata sulla barra informazioni.<br /><br /> Non usare all'esterno di una finestra del documento o lo strumento.|  
|[Modifiche di cursore del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Può essere utilizzato per inviare una notifica che un processo in corso. Viene utilizzato anche per notificare che si verifica un cambiamento di stato nel mouse, ad esempio durante il trascinamento della selezione è in corso o che il cursore si trova in una determinata modalità, ad esempio di modalità di disegno.|Non utilizzare per le modifiche di stato di avanzamento breve o se gelatinoso del cursore è probabile (ad esempio, quando associato a parti di un processo in esecuzione più lungo anziché l'intero processo).|  
|[Indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilizzare quando è necessario segnalare lo stato (determinata o indeterminato). Esistono diversi tipi di indicatori di stato di avanzamento e di utilizzo specifico per ogni. Vedere [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La finestra di notifiche non è estendibile pubblicamente. Tuttavia, si utilizza per comunicare un intervallo di messaggi relativi a Visual Studio, inclusi i problemi critici e notifiche informative di aggiornamenti per Visual Studio o ai pacchetti di licenza.|Non utilizzare per altri tipi di notifiche.|  
|[Elenco errori](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando il problema è correlato direttamente a un problema (errore/avviso/informazioni) con la soluzione attualmente aperta dell'utente, si potrebbe essere necessario intervenire sul codice.<br /><br /> Ciò potrebbe includere, ad esempio:<br /><br /> -I messaggi del compilatore (errore/avviso/informazioni)<br /><br /> -I messaggi di Analizzatore/diagnostica codice sul codice<br /><br /> -I messaggi di compilazione<br /><br /> Potrebbe essere appropriata per i problemi relativi ai file di progetto o soluzione, ma tenere presente prima di un'indicazione di Esplora soluzioni.|Non utilizzare per gli elementi che non ha alcuna relazione con il codice dell'utente soluzione aperta.|  
|Le notifiche di editor: lampadina|Utilizzare quando si dispone di una correzione disponibile per risolvere un problema che esiste nel file aperto.<br /><br /> Lampadina deve essere utilizzato anche per l'hosting azioni rapide che vengono eseguite nel codice dell'utente su richiesta, ad esempio refactoring, ma in tal caso non verrà visualizzato "style notifica".|Non utilizzare per gli elementi che non ha alcuna relazione al file aperto.|  
|Le notifiche di editor: la digitazione|Utilizzare per avvisare l'utente a un problema con un intervallo particolare del codice aperto (ad esempio, una sottolineatura ondulata rossa per gli errori).|Non utilizzare per gli elementi che non sono correlati a un'estensione particolare del codice aperto.|  
|[Barre di stato incorporata](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilizzare per fornire lo stato correlato al contenuto o processo all'interno di contesto di una finestra degli strumenti specifica, una finestra del documento o una finestra di dialogo.|Non utilizzare per le notifiche di categoria, processi o gli elementi che non ha alcuna relazione con il contenuto all'interno della finestra specifica.|  
|[Notifiche barra delle applicazioni di Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Consente di esporre le notifiche per i processi di out-of-process o complementare di applicazioni.|Non utilizzare per le notifiche che riguardano l'IDE.|  
|[Bolle di notifica](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Consente di inviare una notifica di un processo remoto o modificare **esterno** dell'IDE.|Non utilizzare come mezzo per notificare all'utente di processi **all'interno di** l'IDE.|  
  
### <a name="notification-methods"></a>Metodi di notifica  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a>Finestre di messaggio di errore modale  
 Una finestra di dialogo di messaggio di errore modale viene utilizzato per visualizzare un messaggio di errore che richiede la conferma dell'utente o un'azione.  
  
 ![Messaggio di errore modale](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Una finestra di messaggio di errore modale segnalazione all'utente di una stringa di connessione non valido per un database**  
  
####  <a name="BKMK_IDEStatusBar"></a>Barra di stato IDE  
 Mette in correlazione le probabilità che gli utenti si noti il testo della barra di stato e al loro computer polivalente degli specifico esperienza con la piattaforma Windows. Il cliente di Visual Studio base tende a essere esperti in entrambe le aree, anche se gli utenti di Windows anche esperti potrebbero mancare modifiche nella barra di stato. Pertanto, la barra di stato viene utilizzata meglio per scopi informativi o come un segnale di ridondanza per le informazioni presentate in un' posizione. Qualsiasi tipo di informazioni critiche che l'utente deve risolvere immediatamente deve essere fornito in una finestra di dialogo o nella finestra degli strumenti di notifiche.  
  
 La barra di stato di Visual Studio è progettata per consentire diversi tipi di informazioni da visualizzare. È suddivisa in aree per commenti e suggerimenti, finestra di progettazione, barra di stato, l'animazione e client.  
  
 L'area commenti e suggerimenti e l'area di progettazione sono sempre visibili. L'indicatore di stato e animazione aree sono sempre dinamica ed è basato sul contesto utente. L'area di progettazione ha una larghezza statica dipende dalla lunghezza della stringa che viene effettuato il pull da una risorsa di accompagnamento per il messaggio di testo. In questo modo la localizzazione di ridimensionare la larghezza senza richiedere una modifica del codice. Per l'inglese, la larghezza di questa stringa è approssimativamente 220 pixel. L'area di progettazione si comporterà in genere e l'area commenti e suggerimenti verrà assorbire lo spazio rimanente.  
  
 La barra di stato viene inoltre colorata per aggiungere l'interesse visivo e il valore funzionale comunicando vari cambiamenti di stato IDE, ad esempio quando l'ambiente IDE è in modalità di debug.  
  
 ![Le modifiche ai colori della barra di stato dell'IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **Colori della barra di stato IDE**  
  
####  <a name="BKMK_EmbeddedInfobar"></a>Barra informazioni incorporata  
 Una barra informazioni è utilizzabile nella parte superiore di una finestra del documento o una finestra degli strumenti per informare l'utente di uno stato o una condizione. Può anche offrire i comandi in modo che l'utente può avere un modo per effettuare con facilità un'azione. Barra informazioni sono un controllo shell standard. Evitare di creare la propria, che agiscono e vengono visualizzati non coerente con altri utenti nell'IDE. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) per i dettagli di implementazione e materiale sussidiario sull'utilizzo.  
  
 ![Barra informazioni incorporata](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Una barra informazioni incorporati in una finestra del documento, l'utente che l'ambiente IDE è in modalità di debug cronologico e l'editor non risponderà esattamente come avviene in modalità di debug standard di avviso.**  
  
####  <a name="BKMK_MouseCursorChanges"></a>Modifiche di cursore del mouse  
 Quando si modifica il cursore del mouse, utilizzare i colori che sono collegati al servizio VSColor e sono già associate con il cursore. Modifiche di cursore possono essere utilizzate per indicare un'operazione in corso, nonché hit aree in cui l'utente si posiziona su una destinazione che può essere trascinata, rilasciata o utilizzata per selezionare un oggetto.  
  
 Usare il cursore del mouse occupato/attesa solo quando è necessario riservare tutto il tempo della CPU disponibile per un'operazione, impedendo all'utente di esprimere qualsiasi ulteriore input. Nella maggior parte dei casi con applicazioni ben scritte con multithreading, quando gli utenti possono eseguire altre operazioni di volte in cui deve essere rari.  
  
 Tenere presente che le modifiche di cursore sono utili come una pila di ridondanza per le informazioni presentate in un' posizione. Non fare affidamento su una modifica di cursore come unico metodo di comunicare con l'utente, in particolare quando si tenta di trasmettere un elemento è fondamentale che l'utente deve indirizzare.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a>Indicatori di stato  
 Gli indicatori di stato sono importanti per la concessione all'utente un feedback durante i processi di più di pochi secondi per il completamento. È possibile visualizzare gli indicatori di stato sul posto (quasi il punto di avvio dell'azione in corso), in una barra di stato incorporata, nella finestra di dialogo modale o nella barra di stato di Visual Studio. Seguire le indicazioni in [indicatori di stato](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) relative all'uso e l'implementazione.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a>Finestra di Visual Studio notifiche  
 La finestra di notifiche di Visual Studio notifica agli sviluppatori di licenza, l'ambiente (Visual Studio), estensioni e aggiornamenti. Gli utenti possono chiudere le notifiche di singoli o possono scegliere di ignorare determinati tipi di notifiche. L'elenco di notifiche ignorate viene gestito in un **strumenti > Opzioni** pagina.  
  
 La finestra di notifiche non è attualmente estendibile.  
  
 ![Finestra di Visual Studio notifiche](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Finestra di Visual Studio notifiche degli strumenti**  
  
####  <a name="BKMK_ErrorList"></a>Elenco errori  
 Una notifica all'interno dell'elenco di errore indicano errori e avvisi che si è verificato durante la compilazione e o processo di compilazione e consente all'utente di spostarsi nel codice di errore codice specifico.  
  
 ![Elenco errori](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Elenco di errori in Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a>Barre di stato incorporata  
 Poiché la barra di stato IDE è dinamica, con un contesto di area client impostato sulla finestra del documento attivo e informazioni di aggiornamento nel contesto dell'utente e/o risposte del sistema, è difficile mantenere una continua visualizzazione di informazioni o fornire lo stato on a lungo termine processi asincroni. Ad esempio, la barra di stato IDE non è appropriata per le notifiche dei risultati di esecuzione dei test per più esecuzioni e/o le selezioni delle voci immediatamente utilizzabili. È importante mantenere tali informazioni sullo stato nel contesto della finestra di documento o lo strumento in cui l'utente effettua una selezione o avvia un processo.  
  
 ![Barra di stato incorporata](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Barra di stato incorporata in Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a>Notifiche barra delle applicazioni di Windows  
 La finestra accanto il sistema di area di notifica dell'orologio della barra delle applicazioni di Windows. In molte utilità ed i componenti software forniscono le icone in quest'area, in modo che l'utente può ottenere un menu di scelta rapida per le attività a livello di sistema, ad esempio modifica risoluzione dello schermo o ricevano gli aggiornamenti software.  
  
 Notifiche a livello di ambiente devono essere rese disponibili nell'hub notifiche di Visual Studio, non l'area di notifica di Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a>Bolle di notifica  
 Bolle di notifica possono apparire come informativo all'interno di un editor o la finestra di progettazione o come parte dell'area di notifica di Windows. L'utente visualizza le bolle come i problemi che consentono di risolvere in un secondo momento, che è un vantaggio per le notifiche non critiche. Bolle non sono appropriate per le informazioni critiche che l'utente deve risolvere immediatamente. Se si utilizza bolle di notifica in Visual Studio, seguire la [materiale sussidiario per il Desktop di Windows per le bolle notifica](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Fumetto della notifica](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Fumetto della notifica nell'area di notifica di Windows utilizzato per Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a>Indicatori di stato  
  
### <a name="overview"></a>Panoramica  
 Gli indicatori di stato sono una parte importante di un sistema di notifica per la concessione all'utente un feedback. Forniscono informazioni all'utente quando i processi e le operazioni verranno completata. Tipi di indicatori familiarità includono indicatori di stato, i cursori di rotazione e icone animate. Il tipo e il posizionamento di un indicatore di stato dipende dal contesto, tra cui ciò che viene segnalato e quanto tempo il processo o un'operazione è necessari per completare.  
  
#### <a name="factors"></a>Fattori  
 Per determinare il tipo di indicatore appropriato, è necessario determinare i fattori seguenti.  
  
1.  **Durata:** periodo di tempo richiederà l'operazione  
  
2.  **Modalità:** se l'operazione è modale per l'ambiente (blocchi l'interfaccia utente fino al completamento del processo)  
  
3.  **Permanente o temporaneo:** se il risultato finale dello stato di avanzamento deve essere segnalato e/o visualizzabile in un secondo momento  
  
4.  **Determinata/Indeterminate:** se l'ora di fine e lo stato può essere calcolate  
  
5.  **Percorso immagine/Textual:** se lo stato di avanzamento o di un processo viene acquisita inline, nel corpo di un messaggio o un controllo specifico, ad esempio il controllo struttura ad albero  
  
6.  **Prossimità:** se lo stato di avanzamento deve essere in stretta vicinanza all'interfaccia utente che è correlato al. (Ad esempio, può essere nella barra di stato, che potrebbe essere lontano, o è necessario essere accanto al pulsante che ha avviato il processo?)  
  
#### <a name="determinate-progress"></a>Stato determinato  
  
|Tipo di stato di avanzamento|Quando e come utilizzare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (determinata)|Durata prevista > 5 secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo animazione.|  
|Barra informazioni|Messaggistica associato di scelta rapida dell'interfaccia utente. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** utilizzare più barre informazioni quando è necessario indicare più processi. Utilizzare indicatori di stato in pila.|  
|Finestra di output|Notifica temporanea: il processo a livello di applicazione che l'utente desidera **esaminare** dettagli di dopo il completamento.|**Non** utilizzare se l'utente dovrà fare riferimento ai dati in un secondo momento.|  
|File di log|Abbinato a intransient notifica nei casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: il processo di applicazione a livello di tale utente verrà **non è necessario** dettagli di dopo il completamento.<br /><br /> Include un indicatore di stato incorporata.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
#### <a name="indeterminate-progress"></a>Stato indeterminato  
  
|Tipo di stato di avanzamento|Quando e come utilizzare|Note|  
|-------------------|-------------------------|-----------|  
|Indicatore di stato (indeterminato)|Durata prevista > 5 secondi.<br /><br /> Può includere una descrizione dei dettagli del processo.|**Non** incorporare testo animazione.|  
|Formiche (animate punti orizzontale)|Round trip al server.<br /><br /> Trova il punto di near del contesto parte superiore del contenitore padre.|**Non** utilizzare se non è associato dall'intero contenitore.|  
|Spinner (anello di stato)|Processo associate a scelta rapida dell'interfaccia utente o in cui lo spazio è un fattore importante.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
|Barra informazioni|Messaggistica associato di scelta rapida dell'interfaccia utente. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Non** utilizzare più barre informazioni quando è necessario indicare più processi. Utilizzare indicatori di stato in pila.|  
|Finestra di output|Notifica temporanea: il processo di applicazione a livello utente dovranno **esaminare** dettagli di dopo il completamento.|**Non** informazioni che devono persistere attraverso le sessioni.|  
|File di log|Abbinato a intransient notifica nei casi quando è importante **salvare** dettagli dopo il completamento.||  
|Barra di stato|Notifica temporanea: il processo di applicazione a livello di tale utente verrà **non è necessario** dettagli di dopo il completamento.<br /><br /> Include l'indicatore di stato incorporata.<br /><br /> Può includere una descrizione dei dettagli del processo.||  
  
### <a name="progress-indicator-types"></a>Tipi di indicatori di stato di avanzamento  
  
#### <a name="progress-bars"></a>Indicatori di stato  
  
##### <a name="indeterminate"></a>Indeterminato  
 ![Indicatore di stato indeterminato](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Indicatore di stato indeterminato**  
  
 "Indeterminato" indica lo stato generale di un'operazione o non può essere determinato processo. Utilizzare le barre di stato indeterminato per le operazioni che richiedono una quantità di tempo illimitata che l'accesso o un numero sconosciuto di oggetti. Utilizzare una descrizione testuale complemento a ciò che accade. Utilizzare i timeout dei limiti per operazioni basate sul tempo. Barre di stato indeterminato Usa animazioni per mostrare che lo stato di avanzamento viene eseguita, ma non forniscono altre informazioni. Non scegliere basata solo sull'eventuale mancanza di accuratezza solo una barra di stato indeterminato.  
  
##### <a name="determinate"></a>Determinata  
 ![Indicatore di stato determinato](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Indicatore di stato determinato**  
  
 "Determinata" significa che un'operazione o un processo richiede una quantità limitata di tempo, anche se tale quantità di tempo non è possibile prevedere con precisione. Indicare chiaramente il completamento. Non lasciare un indicatore di stato di passare al 100%, a meno che non è stata completata l'operazione. Animazione della barra di stato determinato sposta da sinistra a destra da 0 a 100%.  
  
 Non spostare l'indicatore di stato con le versioni precedenti durante un'operazione. La barra deve passare costantemente quando inizia l'operazione e raggiungere i 100% quando termina. Il punto della barra di stato è consentire all'utente un'idea di come intera durata dell'operazione, indipendentemente dal fatto il numero di passaggi coinvolti.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Creazione di report (indicatori di stato in pila) simultanee  
 Se un'operazione richiederà molto tempo, forse diversi minuti, quindi due indicatori di stato possono essere utilizzate, uno che mostra lo stato di avanzamento complessivo per un'operazione e l'altro per l'avanzamento del passaggio corrente. Ad esempio, se un programma di installazione copia molti file, una barra di stato di avanzamento può essere utilizzata per indicare l'intero processo di tempo durante il secondo può indicare la percentuale del file corrente o directory vengono copiata. Report non più di cinque operazioni simultanee o i processi che utilizzano le barre di stato di avanzamento in pila. Se si dispone di più di cinque operazioni simultanee o processi per report, utilizzare una finestra di dialogo modale con un pulsante di annullamento e un report le informazioni sullo stato nella finestra di Output.  
  
##### <a name="textual-descriptions"></a>Descrizioni testuali  
 Utilizzare una descrizione testuale complemento qual è il problema e il tempo stimato per il completamento. Se non è possibile determinare il tempo richiesto un'operazione, potrebbe essere una scelta migliore per commenti e suggerimenti un'icona animata anziché una barra di stato.  
  
 Visual Studio fornisce una barra di stato standard nella barra di stato che può essere utilizzata da qualsiasi prodotto integrato in Visual Studio. Per una descrizione testuale di ciò che avviene durante l'indicatore di stato Mostra un'animazione, è possibile aggiornare il testo della barra di stato.  
  
#### <a name="other-progress-indicators"></a>Altri indicatori di stato  
  
##### <a name="ants-animated-horizontal-dots"></a>Formiche (animate punti orizzontale)  
 ![Stato di avanzamento formiche](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Formiche," animate punti orizzontali, forniscono un riferimento visivo per un processo del server di round trip indeterminato.  
  
##### <a name="spinner-progress-ring"></a>Spinner (anello di stato)  
 ![Casella di selezione lo stato di avanzamento](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 La casella di selezione (noto anche come un "anello lo stato di avanzamento") è un indicatore di stato indeterminato utilizzato principalmente in relazione a scelta rapida dell'interfaccia utente. Visualizzare una casella di selezione in stretta vicinanza al relativo contenuto correlato, ad esempio intestazioni di categoria testuale, messaggistica o controllo.  
  
##### <a name="cursor-feedback"></a>Commenti e suggerimenti di cursore  
 Per le operazioni che prendono da 2 a 7 secondi, fornire commenti e suggerimenti del cursore. Ciò significa in genere, tramite il cursore di attesa fornito dal sistema operativo. Per ulteriori informazioni, vedere l'articolo MSDN [Cursors.Wait proprietà](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Percorsi di indicatore di stato di avanzamento  
  
##### <a name="status-bar"></a>Barra di stato  
 La barra di stato fornisce all'applicazione di una posizione per visualizzare i messaggi e informazioni utili per l'utente senza interrompere le attività dell'utente. In genere visualizzato nella parte inferiore di una finestra, lo stato di avanzamento sarà un riquadro di suggerimento di strumento che include un messaggio su misura dello stato di avanzamento in combinazione con un indicatore.  
  
 ![Barra di stato con indicatore di stato](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Barra di stato con indicatore di stato**  
  
 ![Barra di stato con messaggistica](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Barra di stato con la descrizione testuale**  
  
##### <a name="infobar"></a>Barra informazioni  
 È simile alla barra di stato, della barra informazioni fornisce notifica contesto e messaggistica, che possono anche essere associati con gli indicatori di stato indeterminato, ad esempio la barra di stato o una casella di selezione. Barra informazioni non deve fornire lo stato di livello granulare o indicazione di stato determinato. Vedere [barre informazioni](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra informazioni con indicatore di stato e messaggistica](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Barra informazioni con indicatore di stato e la descrizione testuale**  
  
 ![Barra informazioni all'interno di una finestra](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Inline  
 Indica lo stato di avanzamento inline può essere rappresentato da uno dei tipi del caricatore di stato di avanzamento. In genere l'indicatore di stato è associato con la messaggistica, ma questo non è un requisito.  
  
 ![Casella di selezione stato inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **Casella combinata con la descrizione testuale di selezione**  
  
 ![Indicatori di stato in pila inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Barre di stato in pila determinato**  
  
 ![Messaggistica sullo stato inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Testo inline di Esplora server: l'aggiornamento...**  
  
##### <a name="tool-windows"></a>Finestre degli strumenti  
 Indicazione di stato globale è rappresentato da una barra di stato indeterminato posizionata direttamente sotto la barra degli strumenti.  
  
 ![Indicatore di stato indeterminato globale](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Barra di stato indeterminato globale di Team Explorer**  
  
##### <a name="dialogs"></a>Finestre di dialogo  
 Le finestre di dialogo può contenere uno dei tipi del caricatore di stato di avanzamento. Gli indicatori di stato possono essere abbinati a messaggistica nonché combinati con più livelli di indicazione di stato di avanzamento per rappresentare granulare e processo secondario.  
  
 ![Finestra di dialogo con più tipi di indicatori di stato di avanzamento](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Finestra di dialogo Visual Studio con più tipi di indicatori di stato di avanzamento e di processi simultanei**  
  
 ![Finestra di dialogo con caricatore dello stato e messaggistica](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Finestra di dialogo Visual Studio con caricatore dello stato e messaggistica inline dei comandi**  
  
##### <a name="document-well"></a>Documenti  
 Il documento anche possibile visualizzare più tipi di caricatore lo stato di avanzamento in combinazione con i controlli.  
  
 ![Messaggistica nel documento e sullo stato](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Indicatore di stato indeterminato di sotto della barra degli strumenti**  
  
##### <a name="output-window"></a>Finestra di output  
 La finestra di Output è appropriata per la gestione dei processo progressione e lo stato di avanzamento tramite messaggistica testuale inline. È consigliabile utilizzare la barra di stato con reporting per qualsiasi stato di avanzamento per la finestra Output.  
  
 ![Messaggistica sullo stato nella finestra di Output](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Finestra di output con lo stato di processo in corso e attendere il completamento di messaggistica**  
  
##  <a name="BKMK_Infobars"></a>Barre informazioni  
  
### <a name="overview"></a>Panoramica  
 Barre informazioni assegnare all'utente un indicatore vicino al relativo punto di attenzione e utilizza il controllo barra informazioni condivise garantisce la coerenza nell'interazione e l'aspetto visivo.  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Visualizzazione in Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Usa appropriato per una barra informazioni  
  
-   Per consentire all'utente un messaggio non bloccante ma importante rilevante per il contesto corrente  
  
-   Per indicare che l'interfaccia utente in un determinato stato o una condizione che esegue alcune implicazioni interazione, ad esempio il debug cronologico  
  
-   Per notificare all'utente che il sistema ha rilevato problemi, ad esempio quando un'estensione causa problemi di prestazioni  
  
-   Per fornire all'utente un modo per effettuare con facilità un'azione, ad esempio quando l'editor rileva che un file è mista tabulazioni e spazi  
  
##### <a name="do"></a>Eseguire:  
  
-   Mantenere il testo del messaggio barra informazioni breve e il punto.  
  
-   Mantenere il testo su collegamenti e i pulsanti conciso.  
  
-   Verificare le opzioni di "azione" è fornire agli utenti sono minime, mostrare solo le azioni necessarie.  
  
##### <a name="dont"></a>Non:  
  
-   Utilizzare una barra informazioni per rendere disponibili i comandi standard che devono essere inseriti in una barra degli strumenti.  
  
-   Utilizzare una barra informazioni al posto di una finestra di dialogo modale.  
  
-   Creare un messaggio all'esterno di una finestra mobile.  
  
-   Utilizzare più barre informazioni in diverse posizioni all'interno della finestra stessa.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Consente di visualizzare più barre informazioni allo stesso tempo?  
 Sì, più barre informazioni consente di visualizzare contemporaneamente. Vengono visualizzati in ordine cronologico ordine con prima che mostra in visualizzazione di barre informazioni aggiuntive e superiore sotto barra informazioni.  
  
 L'utente verrà visualizzato un massimo di tre barre informazioni alla volta, dopo che, se più barre informazioni sono disponibili, l'area della barra informazioni non sarà più scorrevole.  
  
### <a name="creating-an-infobar"></a>Creazione di una barra informazioni  
 Barra informazioni con quattro sezioni, da sinistra a destra:  
  
-   **Icona:** si tratta di dove aggiungere le icone si desidera visualizzare la barra delle informazioni, ad esempio un'icona di avviso.  
  
-   **Testo:** è possibile aggiungere testo per descrivere l'utente/situazione scenario è, insieme ai collegamenti all'interno del testo, se necessario. Ricordarsi di mantenere il testo breve.  
  
-   **Azioni:** in questa sezione deve contenere collegamenti e i pulsanti per le azioni che l'utente può richiedere la barra informazioni.  
  
-   **Pulsante Chiudi:** l'ultima sezione a destra può avere un pulsante Chiudi.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creazione di una barra informazioni standard nel codice gestito  
 La classe InfoBarModel può essere utilizzata per creare un'origine dati per una barra informazioni. Utilizzare uno di questi quattro costruttori:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Di seguito è riportato un esempio che crea un InfoBarModel con del testo con un collegamento ipertestuale, un pulsante di azione e un'icona.  
  
 ![Barra informazioni con collegamento ipertestuale](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Creazione di una barra informazioni standard nel codice nativo  
 Implementare IVsInfoBar l'interfaccia per fornire una barra informazioni dal codice nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Recupero di una barra informazioni degli elementi di interfaccia da una barra informazioni  
 L'implementazione InfoBarModel o IVsInfoBar sono modelli di dati che devono essere trasformati in un elemento UIElement affinché venga visualizzato nell'interfaccia utente. Un elemento UIElement può essere recuperato con il servizio SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Selezione host  
 Barre informazioni possono essere visualizzati in uno o più delle seguenti posizioni:  
  
-   Finestre degli strumenti  
  
-   All'interno di una scheda di documento  
  
> [!IMPORTANT]
>  È possibile posizionare una barra informazioni per fornire un messaggio sul contesto globale. Questo potrebbe essere visualizzata tra le barre degli strumenti e l'area dei documenti. Questa operazione è sconsigliata perché causa problemi passare "e" jerk dell'IDE e deve essere evitato se non assolutamente necessario e appropriato.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Inserire una barra informazioni in un ToolWindowPane  
 Il metodo ToolWindowPane.AddInfoBar(IVsInfoBar) può essere utilizzato per aggiungere una barra informazioni a una finestra degli strumenti. Questa API è possibile aggiungere un IVsInfoBar (di cui InfoBarModel è un'implementazione predefinita), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Inserire una barra informazioni in un documento o non ToolWindowPane  
 Per inserire una barra informazioni in qualsiasi IVsWindowFrame, utilizzare la proprietà VSFPROPID_InfoBarHost per ottenere il IVsInfoBarHost per il frame e quindi aggiungere la barra informazioni degli elementi di interfaccia.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Inserire una barra informazioni nella finestra principale  
 Per inserire una barra informazioni nella finestra principale, utilizzare VSSPROPID_MainWindowInfoBarHost del servizio IVsShell per ottenere IVsInfoBarHost della finestra principale e quindi aggiungere la barra informazioni degli elementi di interfaccia.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Riconoscerà quando l'utente esegue un'operazione la barra informazioni  
 Sì, restituiamo ogni azione di evento per l'autore della barra informazioni. È l'autore della barra informazioni per eseguire l'azione nell'IDE in base alla selezione utente nella barra informazioni. Verranno rimossi automaticamente barre informazioni dall'host il cui pulsante Chiudi è stato fatto clic, ma è necessario l'intervento aggiuntivo se altre barre informazioni devono essere rimosse dopo la chiusura. Dati di telemetria anche dovranno essere registrati in modo indipendente da ogni barra informazioni.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Ricezione di eventi sulla barra informazioni in un ToolWindowPane  
 ToolWindowPane dispone di due eventi di visualizzazione. L'evento InfoBarClosed viene generato quando una barra informazioni nel ToolWindowPane viene chiuso. L'evento InfoBarActionItemClicked viene generato quando viene selezionato un collegamento ipertestuale o un pulsante sulla barra informazioni.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Ricezione di eventi di barra informazioni direttamente da UIElement  
 IVsInfoBarUIElement.Advise utilizzabile per sottoscrivere gli eventi direttamente da UIElement di una barra informazioni. Implementazione IVsInfoBarUIEvents consente all'autore di chiusura di ricezione e gli eventi click.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a>Convalida di errore  
 Quando un utente immette le informazioni che non sono accettabile, ad esempio quando un campo obbligatorio è ignorato o quando si immettono dati in formato non corretto, è preferibile utilizzare la convalida o commenti e suggerimenti accanto al controllo anziché un messaggio di errore che causano il blocco popup.  
  
### <a name="field-validation"></a>Convalida campo  
 Convalida di moduli e campi è costituita da tre componenti: un controllo, un'icona e una descrizione comando. Sebbene molti tipi di controlli è possono utilizzare questo, una casella di testo verrà utilizzata come esempio.  
  
 ![Convalida campo &#40; vuoto &#41; ] (../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Se il campo è obbligatorio, devono essere presenti indicante il testo della filigrana  **\<richiesto >** e lo sfondo del campo deve essere chiaro giallo (VSColor: `Environment.ControlEditRequiredBackground`) e primo piano deve essere grigio (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Campo di convalida con etichetta "Obbligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Il programma può determinare che il controllo è in uno stato di *il contenuto non valido inserito* quando lo stato attivo viene spostato su un altro controllo o quando l'utente fa clic su un pulsante di commit [OK] o quando l'utente salva il documento o il form.  
  
 Quando si determina lo stato del contenuto non valido, viene visualizzata un'icona all'interno del controllo o semplicemente accanto a esso. La descrizione dell'errore dovrebbe essere visualizzato al passaggio del mouse sull'icona o il controllo. Inoltre, un bordo a 1 pixel dovrebbe essere visualizzato intorno al controllo che sta creando lo stato non valido.  
  
 ![Specifiche del layout della convalida campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Specifiche del layout per la convalida del campo**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Varianti accettabile per le icone  
 Esistono innumerevoli nei casi in cui gli utenti devono essere informati sugli errori di convalida. Se si considera il tipo di controllo e la configurazione dell'interfaccia utente, scegliere la posizione di icona a seconda della situazione.  
  
 ![Posizioni accettabili per la posizione dell'icona](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Variazioni accettabili per i percorsi icona di convalida campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Convalida che richiede un round trip a una connessione di rete o server  
 In alcuni casi, è necessario un round trip al server per verificare il contenuto e potrebbe essere importante visualizzare l'utente lo stato di avanzamento, verificato e gli stati di errore. La figura riportata di seguito viene illustrato un esempio di questo case e l'interfaccia utente di consigliato.  
  
 ![Convalida che prevede un round trip a un server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Convalida che prevede un round trip a un server**  
  
 Si noti che lo spazio disponibile sufficiente a destra del controllo è obbligatorio per adattare il testo "Verifica …" e "Riprova".  
  
#### <a name="in-place-warning-text"></a>Testo dell'avviso sul posto  
 Quando c'è spazio disponibile per inserire il messaggio di errore simile al controllo in uno stato di errore, questo è preferibile utilizzare la descrizione comando da solo.  
  
 ![In &#45; avviso sul posto](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Testo dell'avviso sul posto**  
  
#### <a name="watermarks"></a>Filigrane  
 A volte un intero controllo o finestra è in stato di errore. In questo caso, usare una filigrana per indicare l'errore.  
  
 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Convalida campo filigrana**