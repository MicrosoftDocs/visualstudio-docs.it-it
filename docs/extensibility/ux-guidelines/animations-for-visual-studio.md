---
title: Le animazioni per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a45fd22cce46cb9e43a649fb969980f42b395db2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="animations-for-visual-studio"></a>Animazioni per Visual Studio
## <a name="animation-fundamentals"></a>Nozioni fondamentali di animazione  
  
### <a name="animation-best-practices-in-visual-studio"></a>Procedure consigliate di animazione in Visual Studio  
Seguire queste regole per garantire gli stili di animazione semplice e coerente in IDE di Visual Studio.  
  
-   **Essere selettivi.** Limitare le animazioni a quelle utilizzate per scopi specifici.  
  
-   **Intervalli di tempo e velocità sono importanti** per garantire che le transizioni sentirsi rapido e fisica:  
  
    -   Completare le transizioni animate all'interno di mezzo secondo (500 millisecondi).  
  
    -   Le animazioni che si verificano spesso devono essere sufficientemente rapido che non interrompono del flusso di lavoro dell'utente. Controllare l'animazione in un ciclo e regolare la durata fino a quando non sembra corretto. 
  
    -   Le animazioni non devono essere così rapido o jarring che è difficile da comprendere, ma non così lento che rende uno utente per la transizione alla fine.  
  
    -   Utilizzare variabile intervallo per evidenziare l'importanza. Ad esempio, quando lo spostamento all'interno di una sequenza di elementi in un diagramma classi, velocità tramite le transizioni tra gli elementi quindi rallentare per concentrarsi su elementi importanti.  
  
-   **Usare l'interpolazione lineare graduale** da uno stato a un altro, offrendo un'idea della situazione e naturale lo spostamento.  
  
-   Se possibile, **utilizzare un'animazione sottile al passaggio del mouse** per indicare gli elementi interattivi sotto il mouse.  
  
-   Se si basano su animazioni nelle funzionalità, quindi **forniscono un mezzo per disattivarli** in locale (per tutte le caratteristiche) come opzione nel **strumenti > Opzioni** finestra di dialogo.  
  
-   **Solo un'animazione deve essere eseguita in un momento** e trasmettere solo una parte delle informazioni. Lo spostamento o il tentativo di comunicare più operazioni di più di un oggetto può generare confusione. 
  
-   **Abbastanza particolare è importante.** Nella maggior parte dei casi, animazione non deve necessariamente un intervento dell'utente richiesta per soddisfare lo scopo. Piccole modifiche nella temporizzazione, sequenza e il comportamento potrebbero avere un impatto significativo sul percezione di e rendere la differenza tra un'animazione efficace e inefficace.  
  
-   Quando si utilizza l'animazione per richiamare l'attenzione su un elemento **assicurarsi che vale la pena di interrompere l'utente**del flusso di concetti.  
  
-   **Quando lo stato di avanzamento o lo stato** le animazioni:  
  
    -   Arrestare che mostra lo spostamento di stato quando non è un avanzamento del processo sottostante. 
  
    -   Distinguere indeterminati processi dai processi determinati.  
  
    -   Verificare che un'animazione disponga personali stati di completamento e di errore.  
  
    -   Riduci l'uso di animazioni di effetto che mostra lo stato e verificare che contengano il valore reale fornendo informazioni aggiuntive di uso effettivo. Esempi di situazioni di emergenza e modifiche allo stato temporaneo  
  
#### <a name="animation-donts"></a>Animazione sconsigliate:
  
-   Non usare piccoli movimenti (spostamento in un footprint ridotto). Preferisce dissolvenza e le modifiche tramite lo spostamento di oggetti.  
  
-   Non utilizzare le animazioni che si verificano su una vasta area dell'area dello schermo. Indipendentemente dalle dimensioni, questo stile di animazione è fuorviante per l'utente.  
  
-   Non utilizzare le animazioni non correlati all'oggetto a cui in che l'utente è attualmente attivo o l'interazione con.  
  
-   Non utilizzare le animazioni che richiedono l'intervento dell'utente per reimpostare lo stato, come forzare l'utente di rispondere a una notifica per attivarlo arrestare lampeggiante lampeggiante. Interazione con essi in alcun modo dovrebbe essere sufficiente per ignorare tali.  
  
Per ulteriori informazioni sulle applicazioni per le procedure consigliate, vedere [modelli animazione](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Metriche di animazione  
  
-   Il sistema deve riflettere visibilmente per azioni dell'utente in meno di 10 millisecondi.  
  
-   Transizioni animate non dovrebbero richiedere più di 500 millisecondi per il completamento.  
  
-   Un modo per compensare le transizioni che richiedono tempi lunghi è per separarlo in due parti. Ad esempio, la prima parte di un'animazione può essere il contenitore di contenuto vuoto (fino a 500 millisecondi), aggiungendo la dissolvenza contenuta nel contenitore (fino a 500 millisecondi).  
  
-   Per i tempi di caricamento che possono essere calcolati, è preferibile un indicatore di stato determinante (indicatore di stato %-fine).  
  
-   Per i tempi di caricamento che non possono essere calcolati, un indicatore di occupato come un cursore o animazione rotante incorporato (caricamento o un indicatore di lavoro) è appropriato.  
  
### <a name="animation-as-communicator"></a>Animazione di communicator  
Nell'interfaccia utente di Visual Studio, animazione funziona solo come strumento di comunicazione.  Utilizzato per comunicare un'ampia gamma di informazioni, ad esempio modifiche strutturali nell'interfaccia utente (ad esempio, quando un menu si apre o chiude). Animazione consente di visualizzare il comportamento di dipendenti dal tempo di sistemi complessi, ad esempio la visualizzazione di stato di installazione. Le animazioni consente anche di attirare l'attenzione con avvisi e notifiche.  
  
 Le animazioni dell'interfaccia utente vengono in genere utilizzati nei quattro modi: visualizzare, attirare l'attenzione, simulare, e stato di avanzamento o tempi di risposta indicatori.  
  
#### <a name="visualize"></a>Visualizzare  
Animazione può evidenziare la natura tridimensionale di oggetti e rendono più semplice per gli utenti di visualizzare la struttura spaziale. A tale scopo, l'animazione potrebbe necessario per ruotare l'oggetto in un cerchio completo, lenta riattivarla avanti e indietro, o portare l'oggetto più vicino e leggermente aumentarne le dimensioni per evidenziare lo stato attivo o rollover.  
  
Anche se gli oggetti tridimensionali possono essere spostati con il controllo utente, la finestra di progettazione deve determinare in anticipo (a livello di codice o manualmente) come al meglio animare un movimento che vengono fornite informazioni sugli ottimale dell'oggetto. Questo programmato animazione può quindi essere attivato dall'utente posizionando il cursore sull'oggetto, mentre i movimenti controllata dall'utente richiedono all'utente di imparare a modificare l'oggetto. Limitare lo spostamento di un singolo asse o di orientamento alla volta. la scala, rotazione, o convertire, ma non più contemporaneamente.  
  
La categoria di visualizzazione include gli aspetti dei dati, relazioni, stato, struttura, sequenza e ora.  
  
##### <a name="data"></a>Dati  
Vengono illustrate informazioni complesse e variabile:  
  
-   Spostarsi all'interno di visualizzazioni di informazioni quali i grafici  
  
-   L'esecuzione di istruzioni tramite una sequenza, presentazione e il paging  
  
-   Chiamare i dettagli, verso e informazioni specifiche di evidenziazione  
  
-   La sovrapposizione di dettagli e ulteriori informazioni su un elemento con lo stato attivo
  
-   Modificare da una rappresentazione struttura o dell'organizzazione a un altro  
  
-   Che rappresentano le modifiche nel tempo utilizzando i dispositivi di scorrimento, ruote scatto riquadro attività e controlli di trasporto (riproduzione, arresto e pausa) 
  
##### <a name="relationships"></a>Relazioni  
  
-   Viene illustrato come gli elementi sono correlati tra loro o gli elementi che sono correlate a un determinato elemento
  
-   Mostrare le relazioni di e le gerarchie padre-figlio o pari livello
  
-   Un elemento genera un altro
  
-   Riduce al minimo di un elemento a un altro elemento
  
-   Un elemento collegato a un altro
  
##### <a name="state"></a>Stato  
  
-   Aggiornamenti del contenuto
  
-   Selezione e lo stato attivo per utente  
  
-   Stato  
  
-   Errori  
  
##### <a name="structure"></a>Struttura  
  
-   Calcolo pivot per la struttura in un nodo  
  
-   Il riorientamento  
  
-   Ridurre a icona e Ingrandisci, o espandere e comprimere  
  
##### <a name="sequence"></a>Sequence  
  
-   Sequenza di presentazione  
  
-   Capovolgimento di immagini  
  
##### <a name="time"></a>Ora  
  
-   Mostra cambia nel tempo, lasso di tempo e screencast  
  
-   Portarsi Cestino, Annulla e Ripeti  
  
-   Ripristinare lo stato cronologico  
  
#### <a name="attract-attention"></a>Attirare l'attenzione  
Se l'obiettivo è di per attirare l'attenzione dell'utente a un singolo elemento da diversi o per avvisare l'utente per informazioni aggiornate, un'animazione potrebbe essere appropriata. Ad esempio, la pagina iniziale dell'applicazione potrebbe utilizzare un pulsante Guida introduttiva che scorre in posizione dopo il caricamento della pagina.  
  
Come regola, l'ultimo elemento di spostamento nella schermata attrae l'attenzione dell'utente.  In una serie di elementi animati, l'attenzione dell'utente seguirà l'ultimo oggetto mobile.  
  
##### <a name="alert"></a>Avviso  
  
-   Avvisare l'utente, ottenere attenzione, visualizzare lo stato di avanzamento  
  
-   Mostra che un elemento viene eseguito correttamente o non correttamente o Mostra lo stato di avanzamento o modifiche di stato di avanzamento  
  
-   Richiedere agli utenti durante un'attività, come ricerca di ulteriori informazioni online o di formazione sull'attività corrente  
  
##### <a name="notifications"></a>Notifiche  
  
-   Avvisare l'utente su una condizione di errore  
  
-   L'utente per vedere se desiderano allontanarsi di interrupt  
  
-   Tirare informare l'utente che un processo è stato completato o modificato, ad esempio durante il download è stato completato.  
  
#### <a name="simulate"></a>Simulare  
In questa categoria sono physicality e dimensionalità.  
  
-   Illustrare in cui gli oggetti provengano da o in cui passano alla  
  
-   Espandere e comprimere o aprire e chiudere  
  
-   Panoramica, lo scorrimento e pagina attiva  
  
-   Sovrapposizione e ordinamento z  
  
-   Sequenza e accordion  
  
-   Capovolgimento e rotazione dell'interfaccia utente  
  
#### <a name="response-and-progress-indicators"></a>Indicatori di risposta e lo stato di avanzamento  
Gli indicatori di stato sono un paio di importanti vantaggi:  
  
-   Entrambi gli indicatori di stato indeterminato e determinata rassicurare l'utente che il sistema non è stato danneggiato e il problema è in corso.  
  
-   Gli indicatori determinato per consentire all'utente che una certa distanza lungo l'azione viene eseguita l'operazione, nonché un senso di recupero più vicino alla fine.  
  
##  <a name="BKMK_AnimationPatterns"></a>Modelli di animazione  
  
### <a name="overview"></a>Panoramica  
Le animazioni in Visual Studio sono progettate per fornire una funzione specifica senza effetti negativi sulla produttività degli utenti. In genere, le animazioni in Visual Studio devono essere:  
  
-   Piccole e non intrusiva  
  
-   Naturali e realistici  
  
-   Complessi e avvolta  
  
-   Veloci ed efficienti  
  
-   Flessibile, non accelera l'esecuzione  
  
Questa illustrazione mostra gli stili di animazione consigliati per Visual Studio. Alcuna animazione o meno evidenti animazioni come dissolvenza in entrata / uscita, più di frequente non vengono utilizzate. Non è limitato di applicazione di animazioni di spostamento come espandere e comprimere, X e Y posizione, modifica e la rotazione. 
  
![Gli stili di animazione consigliati per Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Stili di animazione consigliati per Visual Studio
  
#### <a name="appear-and-disappear"></a>Vengono visualizzati e nascosti  
Con questo modello, un elemento passa dalla visibile a out-di-visualizzazione e viceversa senza un'animazione di transizione.  
  
![Vengono visualizzati e nascosti animazione](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />Vengono visualizzati e nascosti animazione  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Elementi dell'interfaccia utente aggiornati necessario immediatamente compaiano o scompaiano in modo che l'utente non è né distrarre né nascosto. Inoltre, animazioni lento potrebbe essere considerate un trascinamento di prestazioni, che non si verifica con lo stile vengono visualizzati e scompaiono.  
  
##### <a name="incorrect-usage"></a>Utilizzo non corretto  
Casi in cui dell'interfaccia utente viene visualizzato immediatamente che l'utente non ha è chiaro cosa è successo e facilitare l'aggiunta di un'animazione con comprensione del contesto.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
L'intervallo di tempo in genere è zero secondi.  
  
##### <a name="examples"></a>Esempi    
-   Finestre degli strumenti Nascondi automaticamente  
  
-   Editor di attivazione della tastiera dell'interfaccia utente, come IntelliSense e la Guida ai parametri  
  
-   Aree di espansione e compressione del codice  
  
#### <a name="fade-in-and-fade-out"></a>Dissolvenza in entrata e dissolvenza  
Con questo modello, un elemento dell'interfaccia utente esegue la transizione da (% 0 opacità) non è visibile a visibile (100% di opacità) o viceversa.  
  
![Animazione di dissolvenza in entrata e dissolvenza](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />Animazione di dissolvenza in entrata e dissolvenza  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Animazione dell'interfaccia utente più comune è consigliato. È un leggero effetto che aggiunge interesse senza interrompere il flusso. In alcuni casi, l'utente potrebbe anche considerano il fatto che sia presente un'animazione, percepire semplice e di sistema dell'interfaccia utente di propagazione.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
  
-   Opacità di avvio: % 0 per la dissolvenza, 100% per la dissolvenza  
  
-   Fine opacità: 100% per la dissolvenza, % 0 per la dissolvenza  
  
-   Durata: 200 millisecondi autonomo, 100 millisecondi, se utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### <a name="examples"></a>Esempi  
  
-   Finestre degli strumenti Nascondi automaticamente  
  
-   Menu di aperto e chiusura  
  
-   Transizioni di scheda di sfondo e primo piano  
  
#### <a name="color-blend-from-a-to-b"></a>Colore di blend da A B  
Con questo modello, un elemento dell'interfaccia utente consente di modificare da colore A B.  
  
![Animazione di miscele di colore](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />Animazione di sfumatura di colore  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Come una transizione animata quando un elemento dell'interfaccia utente cambia colore da uno stato o contesto a un altro.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
  
-   Colore iniziale: specifici dell'interfaccia utente  
  
-   Colore finale: specifici dell'interfaccia utente  
  
-   Durata: 200 millisecondi autonomo, 100 millisecondi, se utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### <a name="examples"></a>Esempi  
  
-   Documentare le transizioni di stato di finestra (attivo, ultimo attive e inattive)  
  
-   Strumento di transizioni di stato di finestra (con stato attivo e con stato non attivo)  
  
#### <a name="expand-and-contract"></a>Espandere e comprimere  
Con questo modello, un elemento dell'interfaccia utente si espande in X, Y o entrambe le direzioni.  
  
![Espandere e comprimere animazione](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />Espandere e comprimere animazione  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Come una transizione animata quando un elemento dell'interfaccia utente cambia dimensioni da un contesto a un altro.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
  
-   Scala x: % o una specifica dimensione (in pixel)  
  
-   Scala Y: % o una specifica dimensione (in pixel)  
  
-   Posizione di ancoraggio: in genere angolo superiore sinistro (per le lingue da sinistra a destra) o superiore a destra (per le lingue da destra a sinistra)  
  
-   Durata: 200 millisecondi autonomo, 100 millisecondi, se utilizzato come parte di una sequenza di animazione di combinazione  
  
##### <a name="examples"></a>Esempi  
  
-   Pannello Esplora architettura espandere e comprimere  
  
-   Elemento di pagina iniziale di espandere e comprimere  
  
#### <a name="x-y-position-change"></a>Modifica di posizione X-Y  
Con questo modello, un elemento dell'interfaccia utente cambia la posizione X o Y o entrambi.  
  
![Animazione di modifica della posizione X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />Animazione di modifica posizione X-Y  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Come una transizione animata quando un elemento dell'interfaccia utente cambia posizione da un contesto a un altro.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
  
-   Posizione di inizio X e Y: specifici dell'interfaccia utente  
  
-   Posizione finale X e Y: specifici dell'interfaccia utente  
  
-   Tracciato di movimento: nessuno  
  
-   Durata: 200 millisecondi autonomo, 100 millisecondi, se utilizzato come parte di una sequenza di animazione di combinazione  
  
-   Stile di interpolazione: InOut seno  
  
##### <a name="example"></a>Esempio  
Riordinamento di scheda  
  
#### <a name="rotate"></a>Ruota  
Con questo modello, Ruota l'elemento dell'interfaccia utente.  
  
![Animazione di rotazione di elemento dell'interfaccia utente](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />Animazione di rotazione di elemento dell'interfaccia utente  
  
##### <a name="correct-usage"></a>Utilizzo corretto  
Solo per l'indicatore di stato rotante indeterminato.  
  
##### <a name="animation-properties"></a>Proprietà di animazione  
  
-   Gradi di rotazione: 360  
  
-   Centro di rotazione: centrale dell'oggetto  
  
-   Durata: continua  
  
##### <a name="example"></a>Esempio  
Indicatore di stato indeterminato (rotazione)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Le azioni dell'interfaccia utente della shell comuni e le animazioni consigliate  
  
#### <a name="tab-open"></a>Scheda aperta  
![Scheda animazione di apertura](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />Scheda animazione di apertura  
    
-   Stile: vengono visualizzati  
  
-   Durata: zero secondi  

#### <a name="tab-close"></a>Chiudi scheda  
![Scheda animazione di chiusura](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />Scheda animazione di chiusura  
  
-   Stile: Modificare la posizione X  
  
-   Durata: 200 millisecondi  
  
#### <a name="tab-reorder"></a>Riordinamento di scheda  
![Scheda animazione di riordinamento in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />Animazione di riordinamento della scheda

-   Stile: Modificare la posizione X  
  
-   Durata: 200 millisecondi  
    
#### <a name="close-floating-document"></a>Chiusura documento mobile  
![Chiudi mobile animazione documento](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />Animazione di chiusura per documento mobile  
   
-   Stile: vengono visualizzati  
  
-   Durata: 200 millisecondi   
 
#### <a name="window-state-transition"></a>Transizione di stato di finestra  
![Animazione di transizione di stato finestra](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />Animazione di transizione di stato di finestra  
    
-   Style: per garantire la coerenza con le altre finestre, lasciare che il sistema operativo corrente definiscono l'animazione di chiusura del documento.  
  
-   Durata: 200 millisecondi  
  
#### <a name="menu-open"></a>Aprirlo menu  
![Animazione del menu aprirlo](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />Animazione di apertura di menu  
    
-   Stile: dissolvenza  
  
-   Durata: 200 millisecondi  
  
#### <a name="menu-close"></a>Chiudere menu  
![Animazione di chiusura dal menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />Animazione di chiusura di menu  
    
-   Stile: dissolvenza  
  
-   Durata: 200 millisecondi  
  
#### <a name="auto-hide-tool-window-reveal"></a>Mostra finestra di strumento Nascondi automaticamente  
![Animazione di comparsa finestra dello strumento Nascondi automaticamente](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />Animazione di comparsa finestra dello strumento Nascondi automaticamente  

-   Stile: vengono visualizzati  
  
-   Durata: zero secondi