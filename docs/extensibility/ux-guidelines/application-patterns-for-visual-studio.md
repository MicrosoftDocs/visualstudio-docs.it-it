---
title: Modelli di applicazione per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 139b51fbf0ede7ea439d2308a0d03afe7ba617ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="application-patterns-for-visual-studio"></a>Modelli di applicazione per Visual Studio
##  <a name="BKMK_WindowInteractions"></a>Interazioni di finestra  
  
### <a name="overview"></a>Panoramica  
I due tipi di finestra principale utilizzati in Visual Studio sono editor di documenti e finestre degli strumenti. Rare, ma possibili, sono finestre di dialogo non modale di grandi dimensioni. Anche se questi sono tutti non modali nella shell, sui modelli sono fondamentalmente diversi. Questa sezione descrive la differenza tra le finestre dei documenti, finestre degli strumenti e finestre di dialogo non modale. Sono disponibili modelli di finestra di dialogo modale in [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Il confronto dei modelli di utilizzo di finestra  
**Finestre di documento** sono quasi sempre visualizzate all'interno del documento. In questo modo, l'editor di documento una "fase center" per disporre le finestre di strumento supplementare intorno.  
  
Oggetto **finestra degli strumenti** è spesso visualizzato come finestra separata, più piccolo compressa contro il bordo dell'IDE. Questo può essere visibile, nascosto o nascosto automaticamente. Tuttavia, talvolta finestre degli strumenti vengono presentate all'interno del documento, anche se si deseleziona la **finestra/ancoraggio** proprietà nella finestra. Di conseguenza, più ampia, ma anche decisioni di progettazione comune: durante il tentativo di integrare in Visual Studio, è necessario decidere se la funzionalità deve essere visualizzata una finestra degli strumenti o una finestra del documento.  
  
**Le finestre di dialogo non modale** sconsiglia in Visual Studio. Finestre di dialogo più non modali sono, per definizione, finestre degli strumenti mobili e deve essere implementate in questo modo. Le finestre di dialogo non modali sono consentiti nei casi in cui le dimensioni di una finestra normale strumento ancorata al lato della shell potrebbero essere troppo restrittivo. Sono consentiti anche nei casi in cui l'utente potrebbe essere probabile spostare la finestra di dialogo per un monitor secondario.  
  
Considerare con attenzione il tipo contenitore è necessario. Considerazioni sul modello di utilizzo comune per la progettazione dell'interfaccia utente sono nella tabella seguente.  
  
||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modale|  
|-|---------------------|-----------------|---------------------|  
| **Posizione** | Sempre posizionato anche all'interno del documento e non ancora intorno ai bordi dell'IDE. È possibile "estrarre" in modo da spostarla separatamente dalla shell di principale. | In genere ancorate ai bordi dell'IDE, ma può essere personalizzato per essere a virgola mobile, nascoste automaticamente (unpinned) o ancorato all'interno del documento anche.|Finestra mobile grandi separato dall'IDE. |  
| **Eseguire il commit del modello** | *Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente rilascia il **File &gt; salvare**, **Salva con nome**, o **Salva tutto** comando. Una finestra del documento è il concetto dei dati all'interno di esso venga "scritto" quindi eseguito il commit a uno dei Salva i comandi. Quando si chiude una finestra del documento, tutto il contenuto venga salvato su disco o perso. | *Commit immediato*<br /><br /> Non è non Salva modello. Per finestre di strumento di controllo che consentono di modificare un file, il file deve essere aperto nell'editor attivo o nella finestra di progettazione e l'editor o la finestra di progettazione è proprietario di salvataggio. | *Commit invio immediato o posticipato*<br /><br /> In genere, una finestra di dialogo non modale grandi dimensioni richiede un'azione per eseguire il commit delle modifiche e consente di un'operazione "Cancel", il rollback di tutte le modifiche apportate all'interno della sessione della finestra di dialogo.  In questo modo una finestra di dialogo non modale da una finestra degli strumenti in finestre degli strumenti dispongono sempre di un modello di commit immediato. |  
| **Visibilità** | *Aprire o creare (file) e Chiudi*<br /><br /> Aprire una finestra del documento viene eseguita tramite l'apertura di un documento esistente o utilizzare un modello per creare un nuovo documento. È presente alcuna "Apri \<editor specifico >" comando. | *Nascondere e mostrare*<br /><br /> Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. Contenuto e gli stati all'interno della finestra degli strumenti vengono mantenute se nella visualizzazione o nascosto. Le finestre degli strumenti multi-istanza possono essere chiusa nonché nascoste. Quando una finestra degli strumenti di multi-istanza è chiusa, viene eliminato il contenuto e lo stato all'interno della finestra degli strumenti. | *Avviata da un comando*<br /><br /> Le finestre di dialogo vengono avviate da un comando basato su attività. |  
| **Istanze** | *Multi-istanza*<br /><br /> Diversi editor è possibile aprire il contemporaneamente e modificando diversi file, mentre alcuni editor consentono inoltre lo stesso file essere aperto in più di un editor (utilizzando la **finestra &gt; nuova finestra** comando).<br /><br /> Un singolo editor può modificare uno o più file contemporaneamente (progettazione). | *Singola o multi instance*<br /><br /> Contenuto cambia per riflettere contesto (come illustrato nel Visualizzatore proprietà) o push lo stato attivo/contesto ad altre finestre (elenco di attività, Esplora soluzioni).<br /><br /> Le finestre degli strumenti a istanza singola e a istanza multipla devono essere associate alla finestra del documento attivo, a meno che non vi è un motivo a. | *A istanza singola* |  
| **Esempi** | **Editor di testo**, come l'editor di codice<br /><br /> **Aree di progettazione**, ad esempio una finestra di progettazione del form o un'area di modellazione<br /><br /> **Controllo di layout simili alle finestre di dialogo**, come la finestra Progettazione manifesto | Il **Esplora** fornisce una soluzione e i progetti contenuti all'interno della soluzione<br /><br /> Il **Esplora Server** offre una visualizzazione gerarchica di connessioni server e dei dati che l'utente sceglie di aprire la finestra. Apertura di un oggetto dalla gerarchia di database, ad esempio una query, verrà visualizzata una finestra del documento e consente all'utente di modificare la query.<br /><br /> Il **Visualizzatore proprietà** consente di visualizzare le proprietà dell'oggetto selezionato in una finestra del documento o un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione griglia gerarchici o nei controlli di finestra di dialogo complessi e consentono all'utente di impostare i valori di tali proprietà. | |  
  
##  <a name="BKMK_ToolWindows"></a>Finestre degli strumenti  
  
### <a name="overview"></a>Panoramica  
Finestre degli strumenti supportano le attività dell'utente che si verifica in finestre di documento. Possono essere utilizzati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentali che Visual Studio offre e sono modificabili.  
  
Quando si valuta una nuova finestra degli strumenti nell'IDE, gli autori devono:  
  
-   Utilizzare l'attività appropriata per le finestre degli strumenti esistenti e non crearne di nuovi con funzionalità simili. Nuove finestre degli strumenti devono essere create solo se offrono un "strumento" significativamente diverso o una funzionalità che non può essere integrata in una finestra simile, o disattivando una finestra esistente a un hub tramite pivot.  
  
-   Utilizzare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.  
  
-   Essere coerente con i modelli presenti in altre finestre degli strumenti per lo spostamento di presentazione e della tastiera di controllo.  
  
-   Essere coerente con la presentazione di controllo in altre finestre degli strumenti.  
  
-   Verificare le finestre degli strumenti specifici di documenti visibili automaticamente quando possibile, in modo che vengano visualizzati solo quando viene attivato il documento padre.  
  
-   Verificare che il contenuto di finestra è esplorabile da tastiera (supporto per i tasti di direzione).  
  
#### <a name="tool-window-states"></a>Stati della finestra dello strumento  
Finestre di Visual Studio degli strumenti dispongono di diversi stati, alcuni dei quali sono utente attivato (ad esempio, la funzionalità Nascondi automaticamente). Altri Stati, come visibili automaticamente, consentire le finestre degli strumenti vengono visualizzati nel contesto corretto e nascondere quando non sono necessarie. Vi sono cinque stati di finestra di strumento in totale.  
  
-   **Ancorato bloccato** finestre degli strumenti possono essere collegate a uno qualsiasi dei quattro lati dell'area del documento. Questa icona viene visualizzata nella barra del titolo di finestra degli strumenti. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell di e altre finestre degli strumenti e può anche essere collegata a schede.  
  
-   **Nascondi automaticamente** finestre degli strumenti vengono sbloccate. Non è più visualizzata, lasciando una scheda (con il nome della finestra dello strumento e la relativa icona) sul bordo dell'area del documento, può spostare la finestra. La finestra degli strumenti viene estratta quando l'utente passa sopra la scheda.  
  
-   **Visibili automaticamente** finestre degli strumenti vengono visualizzati automaticamente quando viene avviata un'altra parte dell'interfaccia utente, ad esempio un editor, o lo stato attivo.  
  
-   **Mobile** finestre degli strumenti al passaggio del mouse all'esterno dell'IDE. Ciò è utile per le configurazioni di più monitor.  
  
-   **Documento a schede** finestre degli strumenti possono essere ancorate anche all'interno del documento. Ciò è utile per finestre degli strumenti di grandi dimensioni, ad esempio il Visualizzatore oggetti, che richiedono più ampia di ancoraggio per i bordi del frame, è possibile.  
  
![Strumento di stati della finestra in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 01_ToolWindowStates")<br />Stati della finestra degli strumenti in Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>A istanza singola e multi-istanza  
Finestre degli strumenti sono a istanza singola o multi-istanza. Alcune finestre degli strumenti a istanza singola potrebbero essere associati alla finestra del documento attivo, mentre le finestre degli strumenti multi-istanza potrebbero non. Finestre degli strumenti di multi-istanza rispondono il **finestra &gt; nuova finestra** comando creando una nuova istanza della finestra. L'immagine seguente illustra una finestra degli strumenti, se si abilita il comando nuova finestra quando è attiva un'istanza della finestra:  
  
![Comando 'Nuova finestra' quando un'istanza della finestra per abilitare la finestra dello strumento è attiva](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")<br />Finestra degli strumenti, l'abilitazione di comando 'Nuova finestra' quando è attiva un'istanza della finestra  
  
Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre le finestre degli strumenti multi-istanza possono essere chiusa nonché nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegata a schede, a virgola mobile o impostare come finestra figlio Multiple-Document Interface (MDI) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi nel menu finestra Gestione finestra appropriata:  
  
![Comandi della finestra Gestione nel menu finestra di Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 03_WindowManagementControls")<br />Comandi della finestra Gestione nel menu finestra di Visual Studio
  
#### <a name="document-specific-tool-windows"></a>Finestre degli strumenti specifici del documento  
Alcune finestre degli strumenti sono progettati per modificare in base a un determinato tipo di documento. Queste finestre vengono aggiornati continuamente per riflettere funzionalità applicabili alla finestra del documento attivo nell'IDE.  
  
Esempi di finestre degli strumenti, il cui contenuto viene modificato in modo da riflettere l'editor selezionato sono casella degli strumenti e la struttura del documento. Tali finestre mostrano una filigrana quando lo stato attivo che non offre il contesto per la finestra dispone di un editor.  
  
#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti elenco esplorabile  
Alcune finestre degli strumenti è visualizzato un elenco di elementi navigabili che l'utente può interagire con. In questo tipo di finestra, deve esistere sempre commenti e suggerimenti per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco dovrebbe rispondere il **GoToNextLocation** e **GoToPrevLocation** anche la modifica dell'elemento attualmente selezionato nella finestra dei comandi  
  
Esempi di finestre degli strumenti elenco esplorabile sono Esplora soluzioni e la finestra Risultati ricerca.  
  
### <a name="tool-window-types"></a>Tipi di finestra dello strumento  
  
#### <a name="common-tool-windows-and-their-functions"></a>Le finestre degli strumenti comuni e le relative funzioni

**Finestre degli strumenti gerarchici**
| Finestra degli strumenti | Funzione | 
| --- | --- | 
| Esplora soluzioni | Struttura ad albero gerarchica che visualizza un elenco di documenti contenuti nei progetti, file esterni e gli elementi di soluzione. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto a cui appartiene il tipo di progetto (ad esempio, i tipi basato sul riferimento, basate su directory o in modalità mista). | 
| Visualizzazione classi | Una struttura gerarchica delle classi e i vari elementi nel working set di documenti, indipendentemente dal file stessi. | 
| Esplora server | Struttura ad albero gerarchica che visualizza tutte le connessioni server e dei dati nella soluzione. | 
| Struttura documento | La struttura gerarchica del documento attivo. | 

**Finestre degli strumenti della griglia**
| Finestra degli strumenti | Funzione | 
| --- | --- | 
| Proprietà | Una griglia che visualizza un elenco di proprietà per l'oggetto selezionato, insieme ai controlli di selezione valore per modificare le proprietà. | 
| Elenco attività | Una griglia che consente all'utente di creare/modificare/eliminare attività e i commenti. | 

**Finestre degli strumenti del contenuto**
| Finestra degli strumenti | Funzione | 
| --- | --- | 
| ? | Una finestra che consente agli utenti l'accesso a vari metodi di ottenere informazioni della Guida, da "How Do I?" video a forum di MSDN. | 
| Guida dinamica | Una finestra degli strumenti vengono visualizzati i collegamenti agli argomenti applicabili alla selezione corrente della Guida. | 
| Visualizzatore oggetti | Una pagina con frame due colonne con un elenco di componenti gerarchico di oggetti nel riquadro a sinistra e l'oggetto delle proprietà e metodi nella colonna destra. | 

**Finestre degli strumenti finestra di dialogo**
| Finestra degli strumenti | Funzione | 
| --- | --- | 
| Find | Finestra di dialogo che consente all'utente di ricerca o Trova e Sostituisci nei file diversi all'interno della soluzione. |
| Ricerca avanzata | Finestra di dialogo che consente all'utente di ricerca o Trova e Sostituisci nei file diversi all'interno della soluzione. | 

**Altre finestre degli strumenti**
| Finestra degli strumenti | Funzione | 
| --- | --- | 
| Casella degli strumenti | La finestra degli strumenti utilizzata per archiviare gli elementi che verranno eliminati in aree di progettazione, fornendo un'origine di trascinamento coerenza per tutte le finestre di progettazione. |
| Pagina iniziale | Portale dell'utente a Visual Studio, con accesso al feed di notizie di sviluppatore, Guida di Visual Studio e progetti recenti. Gli utenti possono inoltre creare pagine iniziali personalizzate copiando il file StartPage dal "Common7\IDE\StartPages\" directory file di programma Visual Studio nella cartella StartPages in Visual Studio documenti directory e quindi una modifica del codice XAML a mano o aprirlo in Visual Studio o in un altro editor di codice. | 

**Le finestre degli strumenti del debugger**
| Finestra degli strumenti | Funzione | 
| --- | --- |
| Auto ||  
| Controllo immediato ||  
| Output | Ogni volta che si dispone di eventi testuali o dichiarare lo stato, è possibile utilizzare la finestra di output. |  
| Memoria ||  
| Punti di interruzione ||  
| In esecuzione ||  
| Documenti ||  
| Stack di chiamate ||  
| Variabili locali ||  
| Espressioni di controllo ||  
| Disassembly ||  
| Registri ||  
| Thread ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a>Convenzioni di editor  
  
### <a name="document-interactions"></a>Interazioni di documento  
"Documento anche" è lo spazio più grande all'interno dell'IDE e in cui l'utente in genere è stata esaminata la loro attenzione per completare le attività, assistite da finestre aggiuntive. Editor di documento rappresentano l'unità fondamentale di lavoro che l'utente viene aperto e salvato all'interno di Visual Studio. Mantenendo una forte di selezione a Esplora soluzioni o altre finestre gerarchia attivo. L'utente deve essere in grado di scegliere una di queste finestre di gerarchia e sapere in cui è contenuto il documento e la relativa relazione per la soluzione, il progetto o un altro oggetto radice fornito da un pacchetto di Visual Studio.  
  
Modifica di documenti richiede un'esperienza utente coerente. Per consentire all'utente di concentrarsi sull'attività in questione anziché sulla gestione delle finestre e i comandi di ricerca, selezionare una strategia di visualizzazione di documenti che meglio si adatta le attività dell'utente per la modifica di tale tipo di documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interazioni comuni per l'area dei documenti  
  
-   Gestire un modello di interazione coerente in comune **nuovo File** e **Apri** esperienze.  
  
-   Aggiornare la funzionalità correlate nei menu e finestre correlate quando viene visualizzata la finestra di documento.  
  
-   I comandi di menu sono integrati in modo appropriato nel menu comuni come **modifica**, **formato**, e **vista** menu. Se un gran numero di comandi specializzati è disponibile, quindi è possibile creare un nuovo menu. Questo nuovo menu deve essere visibile solo quando il documento attivo.  
  
-   Una barra degli strumenti incorporata può essere inserito nella parte superiore dell'editor. Questo è preferibile disporre di una barra degli strumenti separata che viene visualizzata all'esterno dell'editor.  
  
-   Mantenere sempre una selezione di Esplora soluzioni o attivo simile finestra gerarchia.  
  
-   Fare doppio clic su un documento in Esplora soluzioni è necessario eseguire la stessa azione **aprire**.  
  
-   Se più di un editor può essere utilizzato in un tipo di documento, l'utente deve essere in grado di eseguire l'override o reimpostare l'azione predefinita in un tipo di documento specificato tramite il **Apri con** la finestra di dialogo facendo clic sul file e selezionando **aperto Con** dal menu di scelta rapida.  
  
-   Non creare anche una procedura guidata in un documento.  
  
### <a name="user-expectations-for-specific-document-types"></a>Aspettative degli utenti per i tipi di documento specifico  
Esistono diversi tipi di base diversi editor di documento e ognuno presenta una serie di interazioni che siano coerenti con altri utenti dello stesso tipo.  
  
-   **Editor di testo:** editor di codice, i file di log  
  
-   **Area di progettazione:** WPF Progettazione Windows Form  
  
-   **Editor di stile di finestra di dialogo:** progettazione manifesto, proprietà del progetto  
  
-   **Progettazione modelli:** Progettazione flussi di lavoro, codemap, diagramma dell'architettura, progressione  
  
Esistono diversi tipi di editor non che usa anche il documento. Mentre non modificano documenti stessi, è necessario eseguire interazioni standard per le finestre dei documenti.  
  
-   **I report:** IntelliTrace report, Hyper-V, report del profiler  
  
-   **Dashboard:** Hub diagnostica  
  
#### <a name="text-based-editors"></a>Editor basati su testo  
  
-   Il documento fa parte del modello di scheda Anteprima, consentendo la visualizzazione in anteprima il documento senza aprirlo.  
  
-   La struttura del documento può essere rappresentata all'interno di una finestra degli strumenti complementari, ad esempio una struttura del documento.  
  
-   IntelliSense (se appropriato) abbiano un comportamento coerente con altri editor di codice.  
  
-   I popup o l'interfaccia utente per l'accesso facilitato seguire gli stili e modelli simili per un'interfaccia utente simile esistente, ad esempio CodeLens.  
  
-   Messaggi relativi a stato del documento verranno visualizzati in un controllo barra informazioni nella parte superiore del documento o nella barra di stato.  
  
-   L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e colori utilizzando un **strumenti > Opzioni** pagina della pagina tipi di carattere e colori condivisa o un determinato nell'editor.  
  
#### <a name="design-surfaces"></a>Aree di progettazione  
  
-   Una finestra di progettazione vuota deve avere una filigrana nell'area di che indica come iniziare.  
  
-   Cambio di visualizzazione meccanismi seguirà modelli esistenti, ad esempio fare doppio clic per aprire un editor di codice o le schede nella finestra del documento che consente l'interazione con entrambi i riquadri.  
  
-   Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non è necessaria una finestra degli strumenti altamente specifico.  
  
-   Gli elementi nell'area di seguono un modello di selezione coerente.  
  
-   Barre degli strumenti incorporate contengono i comandi non comuni, solo i comandi specifici del documento, ad esempio **salvare**.  
  
#### <a name="dialog-style-editors"></a>Editor di stile di finestra di dialogo  
  
-   Il layout dei controlli deve seguire convenzioni di layout di finestra di dialogo normale.  
  
-   Schede all'interno dell'editor non devono corrispondere l'aspetto delle schede dei documenti, deve corrispondere a uno dei due stili consentiti scheda interni.  
  
-   Gli utenti devono essere in grado di interagire con i controlli mediante tastiera di sola lettura. tramite l'editor di attivazione e la tabulazione tra i controlli o utilizzando i tasti di scelta standard.  
  
-   La finestra di progettazione deve utilizzare la finestra Salva modello comune. Non salva generale o un commit pulsanti devono essere posizionati nell'area di lavoro, anche se altri pulsanti potrebbero essere appropriato.  
  
#### <a name="model-designers"></a>Progettisti di modelli  
  
-   Una finestra di progettazione vuota deve avere una filigrana nell'area di che indica come iniziare.  
  
-   Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti.  
  
-   Gli elementi nell'area di seguono un modello di selezione coerente.  
  
-   Barre degli strumenti incorporate contengono i comandi non comuni, solo i comandi specifici del documento, ad esempio **salvare**.  
  
-   Una legenda ammesso nell'area di indicative o una filigrana.  
  
-   L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere colori utilizzando un **strumenti > Opzioni** pagina della pagina tipi di carattere e colori condivisa o un determinato nell'editor.  
  
#### <a name="reports"></a>Report  
  
-   I report vengono in genere solo informazioni e non fanno parte del modello di salvataggio. Tuttavia, possono includere l'interazione ad esempio collegamenti ad altre informazioni rilevanti e sezioni espandere e comprimere.  
  
-   La maggior parte dei comandi nell'area di devono essere collegamenti ipertestuali, pulsanti non.  
  
-   Layout deve includere un'intestazione e seguire le linee guida layout di report standard.  
  
#### <a name="dashboards"></a>Dashboard  
  
-   I dashboard non sono un modello di interazione autonomamente, ma servono come mezzo per offrire una varietà di altri strumenti.  
  
-   Non fanno parte il modello di salvataggio.  
  
-   Gli utenti devono essere in grado di interagire con i controlli solo con tastiera, l'editor di attivazione e la tabulazione tra i controlli o utilizzando i tasti di scelta standard.  
  
##  <a name="BKMK_Dialogs"></a>Finestre di dialogo  
  
### <a name="introduction"></a>Introduzione  
Finestre di dialogo in Visual Studio in genere deve supportare una unità discreta di lavoro dell'utente e quindi essere chiuse.  
  
Se si è stabilito che è necessario che una finestra di dialogo, sono disponibili tre opzioni, in ordine di preferenza:  
  
1.  Integrare le funzionalità in una delle finestre di dialogo condivisi in Visual Studio.  
  
2.  Creare la propria finestra di dialogo tramite un criterio presente in una finestra di dialogo simile esistente.  
  
3.  Creare una nuova finestra di dialogo, interazione seguente e linee guida di layout.  
  
In questa sezione viene descritto come scegliere il modello di finestra di dialogo corretto all'interno di flussi di lavoro di Visual Studio e le convenzioni comuni per la progettazione di una finestra di dialogo.  
  
### <a name="themes"></a>Themes  
Finestre di dialogo in Visual Studio eseguire uno dei due stili di base:  
  
#### <a name="standard-unthemed"></a>Standard (unthemed)  
La maggior parte delle finestre di dialogo sono le finestre di dialogo utilità standard e devono essere unthemed. Non reimpostare come modelli di controlli comuni o tentare di creare pulsanti "moderni" con stili o controlli. Controlli e l'aspetto di chrome seguire [linee guida per l'interazione Desktop di Windows standard per le finestre di dialogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Applicare un tema  
Le finestre di dialogo di specialità culinarie "firma" potrebbe essere temi. Le finestre di dialogo con tema hanno un aspetto distinto, anch'essa contenente alcuni modelli di interazione speciali associati allo stile. Tema la finestra di dialogo solo se soddisfa questi requisiti:  
  
-   La finestra di dialogo è un'esperienza comune che verrà visualizzata e usata spesso o da molti utenti (ad esempio, il **nuovo progetto** finestra di dialogo.  
  
-   La finestra di dialogo contiene gli elementi del marchio di prodotto principali (ad esempio, il **impostazioni Account** finestra di dialogo).  
  
-   La finestra di dialogo viene visualizzato come parte integrante di un flusso più grande che include altre finestre di dialogo con tema (ad esempio, il **Aggiungi servizio connesso** finestra di dialogo).  
  
-   La finestra di dialogo è una parte importante di un'esperienza che svolge un ruolo strategico innalzamento di livello o una versione prodotto di differenziazione.  
  
Quando si crea una finestra di dialogo con tema, utilizzare i colori di ambiente appropriate e seguire il layout corretto e i modelli di interazione. (Vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Progettazione di finestra di dialogo  
Le finestre di dialogo ben progettate considerare gli elementi seguenti:  
  
-   L'attività definita dall'utente è supportato  
  
-   Stile del testo della finestra, lingua e alla terminologia di  
  
-   Scelta del controllo e le convenzioni dell'interfaccia utente  
  
-   Allineamento specifica e il controllo di layout visivo  
  
-   Accesso da tastiera  
  
#### <a name="content-organization"></a>Organizzazione del contenuto  
Prendere in considerazione le differenze tra questi tipi di base delle finestre di dialogo:  
  
-   [Le finestre di dialogo semplice](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentare i controlli in una finestra modale. La presentazione potrebbe includere le variazioni del pattern di controllo complesso, inclusi un selettore del campo o una barra degli strumenti.  
  
-   [A più livelli di finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) vengono utilizzati per eseguire la maggior parte dell'area dello schermo quando un singolo elemento di interfaccia utente è costituito da più gruppi di controlli. Raggruppamenti della finestra di dialogo sono "sovrapposti" tramite controlli struttura a schede, i controlli elenco di navigazione o pulsanti in modo che l'utente può scegliere di raggruppamento per visualizzare in qualsiasi momento.  
  
-   [Procedure guidate](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sono utili per indirizzare l'utente attraverso una sequenza logica di passaggi verso il completamento di un'attività. Una serie di opzioni è disponibile in pannelli sequenziali, talvolta introdurre diversi flussi di lavoro ("rami") dipende da una selezione effettuata nel pannello precedente.  
  
####  <a name="BKMK_SimpleDialogs"></a>Finestre di dialogo semplice  
Una semplice finestra di dialogo è una presentazione dei controlli in una finestra modale. In questa presentazione potrebbe includere le variazioni del pattern di controllo complessi, ad esempio un selettore del campo. Per i dialoghi semplice, seguire il layout generale standard, nonché qualsiasi layout specifici necessari per i raggruppamenti di controllo complessa.
  
![> Crea chiave con nome sicuro è riportato un esempio di finestra di dialogo semplice in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 01_CreateStrongNameKey")<br />Crea chiave con nome sicuro è riportato un esempio di finestra di dialogo semplice in Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a>Finestre di dialogo a più livelli  
Le finestre di dialogo a più livelli include schede, dashboard e strutture incorporate. Vengono utilizzati per ottimizzare immobiliare quando sono presenti più gruppi di controlli disponibili in un singolo elemento di interfaccia utente. I raggruppamenti sono disposti in modo che l'utente può scegliere di raggruppamento per visualizzare in qualsiasi momento.  
  
Nel caso più semplice, il meccanismo per passare da raggruppamenti è un controllo struttura a schede. Sono disponibili varie alternative. Vedere l'assegnazione di priorità sulle e dei livelli per la scelta stile più appropriato.  
  
Il **strumenti &gt; opzioni** finestra di dialogo è riportato un esempio di finestra di dialogo a più livelli utilizzando una struttura ad albero incorporato:  
  
![Strumenti > Opzioni è riportato un esempio di finestra di dialogo a più livelli in Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 02_ToolsOptions")<br />Strumenti > Opzioni è riportato un esempio di finestra di dialogo a più livelli in Visual Studio.
  
####  <a name="BKMK_Wizards"></a>Procedure guidate  
Procedure guidate sono utili per indirizzare l'utente attraverso una sequenza di passaggi logica per il completamento di un'attività. Una serie di scelte disponibili nei pannelli sequenziali, e l'utente deve continuare a ogni passaggio prima di procedere al successivo. Una volta sufficienti valori predefiniti sono disponibili, il **fine** pulsante è abilitato.  
  
 Procedure guidate modale vengono utilizzate per le attività che:  
  
-   Contenere diramazioni, disponibili in percorsi diversi a seconda delle scelte dell'utente  
  
-   Contengono le dipendenze tra i vari passaggi, in cui i passaggi successivi dipendono dall'input dell'utente tramite la procedura precedente  
  
-   Sono sufficientemente complesse che l'interfaccia utente deve essere utilizzato per illustrare le scelte disponibili e i possibili risultati in ogni passaggio  
  
-   Sono transazionali, che richiede un set di passaggi da completare nella sua interezza prima eseguito il commit di tutte le modifiche  
  
### <a name="common-conventions"></a>Convenzioni comuni  
Per ottenere una progettazione ottimale e funzionalità con le finestre di dialogo, seguire queste convenzioni in dimensioni di finestra di dialogo, posizione, standard, configurazione di controllo e l'allineamento, dell'interfaccia utente testo, le barre del titolo, pulsanti di controllo e i tasti di scelta.  
  
Per linee guida di layout specifiche, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Dimensione  
Le finestre di dialogo deve adattarsi all'interno di una risoluzione dello schermo di 1024 x 768 minimo e dimensioni di finestra di dialogo iniziale non devono superare i 900 x 700 pixel. Le finestre di dialogo possono essere ridimensionati, ma non è un requisito.  
  
Esistono due indicazioni seguenti per le finestre di dialogo ridimensionabili:  
  
1.  Che viene definita per la finestra di dialogo Ottimizza per il set di controlli senza ritaglio e vengono modificati per supportare la crescita di localizzazione ragionevole una dimensione minima.  
  
2.  Che le dimensioni in scala utente viene mantenuto da una sessione. Ad esempio, se l'utente ridimensiona una finestra di dialogo 150%, quindi un avvio successivo della finestra di dialogo visualizzerà 150%.  
  
#### <a name="position"></a>Posizione  
Le finestre di dialogo deve essere visualizzato centrati all'interno dell'IDE di primo avvio. L'ultima posizione delle finestre di dialogo non ridimensionabile non deve necessariamente essere reso persistente, in modo verranno visualizzati al centro su successivi avvii. 

Per le finestre di dialogo ridimensionabili, le dimensioni devono essere mantenuta in successivi avvii. Per finestre di dialogo modale ridimensionabili, la posizione non desidera essere mantenute. La visualizzazione centrata all'interno dell'IDE evita il rischio della finestra di dialogo che viene visualizzato in una posizione imprevedibile o inutilizzabile quando configurazione dello schermo dell'utente è stato modificato. 

Per i dialoghi non modale che possono essere riposizionate, la posizione dell'utente deve essere mantenuta nel successivi avvii, come la finestra di dialogo potrebbe venire usato di frequente come parte integrante del flusso di lavoro più grande.  
  
Quando le finestre di dialogo deve generare le altre finestre di dialogo, la finestra di dialogo in primo piano deve propagare a destra e dall'elemento padre in modo che sia chiaro per l'utente che si è passati a una nuova posizione.  
  
#### <a name="modality"></a>Modalità  
Da modale significa che gli utenti sono necessari per completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modale impediscono all'utente l'interazione con altre parti dell'ambiente, il flusso di attività della funzionalità deve limitarne l'impiego di possibili. Quando è necessaria un'operazione modale, un numero di finestre di dialogo condivise in che è possibile integrare le funzionalità Visual Studio. Se è necessario creare una nuova finestra di dialogo, seguire il modello di interazione della finestra di dialogo esistente con funzionalità simili.  
  
Quando gli utenti devono eseguire due attività contemporaneamente, come **trovare** e **sostituire** durante la scrittura del nuovo codice, la finestra di dialogo deve essere non modale in modo che l'utente può passare facilmente tra di essi. Visual Studio utilizza in genere le finestre degli strumenti per questo tipo di supporto di editor attività collegata.  
  
#### <a name="control-configuration"></a>Configurazione di controllo  
Essere coerente con le configurazioni del controllo esistenti che eseguono la stessa operazione in Visual Studio.  
  
#### <a name="title-bars"></a>Barre del titolo  
  
-   Il testo nella barra del titolo deve riflettere il nome del comando che l'ha avviata.  
  
-   Nessuna icona deve essere utilizzata nella barra del titolo della finestra. Nei casi in cui il sistema richiede una, utilizzare il logo di Visual Studio.  
  
-   Le finestre di dialogo non è necessario ridurre o ingrandire pulsanti.  
  
-   I pulsanti della Guida nella barra del titolo sono stati deprecati. Non verranno aggiunte alle nuove finestre di dialogo. Quando sono presenti, avviano un argomento della Guida che è concettualmente attinenti all'attività.  
  
 ![Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 03_TitleBarSpecs")<br />Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio
  
#### <a name="control-buttons"></a>Pulsanti di controllo  
In generale, **OK**, **Annulla**, e **Guida** devono essere disposti orizzontalmente i pulsanti nell'angolo inferiore destro della finestra di dialogo. Se una finestra di dialogo dispone di diversi altri pulsanti nella parte inferiore della finestra di dialogo che presenta visual confusione con i pulsanti di controllo, è consentita la pila verticale alternativa.  
  
![Configurazioni accettabile per i pulsanti di controllo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 04_ControlButtonConfig")<br />Configurazioni accettabile per i pulsanti di controllo nelle finestre di dialogo di Visual Studio
  
La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da utilizzare come valore predefinito, scegliere le opzioni seguenti (elencate in ordine di priorità):  
  
-   Scegliere il comando più sicuro e sicuro come impostazione predefinita. Ciò significa che se si sceglie il comando più probabile evitare perdite di dati ed evitare l'accesso di sistema imprevisti.  
  
-   Se la perdita di dati e di sicurezza non sono fattori, quindi scegliere il comando predefinito in base a motivi di praticità. Incluso il comando come il valore predefinito probabilmente determinerà un miglioramento del flusso di lavoro dell'utente quando la finestra di dialogo supporta le attività frequenti o ripetitive.  
  
Evitare di scegliere un'azione in modo permanente distruttiva per il comando predefinito. Se un comando di questo tipo è presente, scegliere un comando sicuro come impostazione predefinita.  
  
#### <a name="access-keys"></a>Chiavi di accesso  
Non utilizzare i tasti di scelta per **OK**, **Annulla**, o **Guida** pulsanti. Per impostazione predefinita, questi pulsanti vengono mappati a tasti di scelta rapida:  
  
| Nome pulsante | Tasto di scelta rapida |  
| --- | --- |  
| OK | INVIO |  
| Annulla | ESC |  
| ? | F1 |  
  
#### <a name="imagery"></a>Immagini  
Usare le immagini con cautela nelle finestre di dialogo. Non utilizzare icone grandi nelle finestre di dialogo semplicemente per utilizzi tutto lo spazio. Usare le immagini solo se sono una parte importante di trasmettere il messaggio all'utente, ad esempio le icone di avviso o di animazioni di stato.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a>Le priorità e sovrapposizione  
  
#### <a name="prioritizing-your-ui"></a>Assegnazione di priorità dell'interfaccia utente  
Potrebbe essere necessario portare alcuni elementi dell'interfaccia utente per forefront e inserire un comportamento più avanzato e in finestre di dialogo Opzioni (inclusi i comandi complessi). Offrire funzionalità utilizzate comunemente per forefront rendendo spazio e per renderlo visibile per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.  
  
#### <a name="layering-your-ui"></a>Disposizione su livelli dell'interfaccia utente  
Se si è stabilito che una finestra di dialogo è necessario, ma la funzionalità correlate che si desidera presentare all'utente va oltre ciò che può essere visualizzata in una semplice finestra di dialogo, è necessario per l'interfaccia utente di livello. Visual Studio Usa i metodi dei livelli più comuni sono schede e corridoi o dashboard. In alcuni casi, le aree che è possono espandere e comprimere potrebbero essere appropriate. Adattivo dell'interfaccia utente non è consigliabile in Visual Studio.  
  
Esistono vantaggi e svantaggi in metodi diversi di sovrapposizione tramite i controlli delle schede di interfaccia utente. Esaminare l'elenco seguente per garantire che si sceglie una tecnica dei livelli a seconda della situazione.  
  
##### <a name="tabbing"></a>Tabulazione  
  
| Il meccanismo di passaggio | Vantaggi e uso appropriato | Uso inappropriato e svantaggi |  
| --- | --- | --- |  
| Controllo Tab | Raggruppare logicamente finestre di dialogo in set correlati<br /><br />Utile per meno di cinque (o il numero di schede che rientrano in una riga tra la finestra di dialogo) pagine di controlli correlati in una finestra di dialogo<br /><br />Le etichette delle schede deve essere breve: uno o due parole in grado di identificare facilmente il contenuto<br /><br />Uno stile di finestra di dialogo comuni di sistema<br /><br />Esempio: **Esplora File &gt; le proprietà degli elementi** | Può essere difficile apportare etichette descrittive di breve<br /><br />In genere non è facilmente scalabile oltre cinque schede in una finestra di dialogo<br /><br />Appropriato se si dispone di un numero eccessivo di schede per una riga (usare una tecnica alternativa livelli)<br /><br />Non è estendibile |  
| Navigazione nella barra laterale | Dispositivo di commutazione semplice in grado di supportare più categorie di schede<br /><br />Elenco semplice di categorie (alcuna gerarchia)<br /><br />Estendibile<br /><br />Esempio: **personalizzare... &gt;Aggiunta di comando** | Non un buon uso di spazio orizzontale se sono presenti meno di tre gruppi<br /><br />Attività può essere ottimizzata adatta per un elenco a discesa |  
| Controllo Tree | Consente di categorie illimitate<br /><br />Consente di raggruppamento e/o gerarchia di categorie<br /><br />Estendibile<br /><br />Esempio: **strumenti &gt; opzioni** | Gerarchie molto annidate possono causare un numero eccessivo di scorrimento orizzontale<br /><br />Visual Studio include un eccesso di visualizzazioni struttura ad albero |  
| Wizard | Semplifica il completamento dell'operazione guidando l'utente passaggi sequenziali, basato su attività: la procedura guidata rappresenta un'attività di alto livello e i singoli pannelli rappresentano sottoattività necessarie per raggiungere l'intera attività<br /><br />Utile quando l'attività attraversa i limiti dell'interfaccia utente, come quando l'utente in caso contrario deve utilizzare più editor e finestre per completare l'attività<br /><br />Utile quando l'attività richiede l'esecuzione del branching<br /><br />Utile quando l'attività contiene le dipendenze tra i passaggi<br /><br />Utile quando più attività simili con fork di una decisione possono essere visualizzate in una finestra di dialogo per ridurre il numero di diverse finestre di dialogo simile | Non è appropriato per qualsiasi attività che non richiede un flusso di lavoro sequenza<br /><br />Gli utenti possono diventare sovraccarico e confusi da una procedura guidata con un numero eccessivo di passaggi<br /><br />Procedure guidate non dispongono implicitamente area dello schermo |  
  
##### <a name="hallways-or-dashboards"></a>Corridoi o dashboard  
Corridoi e i dashboard sono pannelli che fungono da punti alle altre finestre di dialogo e finestre di avvio o finestre di dialogo. Ben progettata "corridoio" immediatamente espone solo le più comuni opzioni, comandi e le impostazioni, consentendo all'utente di eseguire rapidamente attività comuni. Ad esempio un corridoio reale fornisce porte per accedere a locali di cui dispone, qui l'interfaccia utente meno comuni verrà raccolti in "locali" (spesso altre finestre di dialogo) di funzionalità correlate che è possibile accedere da corridoio principale.  
  
In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in un'unica raccolta piuttosto che le funzionalità meno comuni in posizioni distinte di refactoring è semplicemente un dashboard.  
  
![Concetto hallway per esporre un'interfaccia utente aggiuntiva in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 08_Hallway")<br />Concetto hallway per esporre un'interfaccia utente aggiuntiva in Outlook
  
##### <a name="adaptive-ui"></a>Interfaccia utente adattivo  
Mostrare o nascondere l'interfaccia utente in base all'utilizzo o Self-segnalati esperienza di un utente è un altro modo per presentare l'interfaccia utente necessaria nascondendo altre parti. Questa operazione è sconsigliata in Visual Studio, come gli algoritmi per decidere quando visualizzare o nascondere l'interfaccia utente possono risultare difficili, e le regole saranno sempre errate per alcuni set di case.  
  
##  <a name="BKMK_Projects"></a>Progetti  
  
### <a name="projects-in-the-solution-explorer"></a>Progetti in Esplora soluzioni  
La maggior parte dei progetti sono classificati come basato sul riferimento, basate su directory o misto. Tutti i tre tipi di progetti sono supportati contemporaneamente in Esplora soluzioni. La radice dell'esperienza utente durante l'utilizzo di progetti viene eseguita all'interno di questa finestra. Anche se i nodi di progetto diversi sono di riferimento, directory o i progetti di tipo modalità mista, è un modello di interazione comune che deve essere applicato a un punto di partenza prima divergente in motivi definiti dall'utente specifici del progetto.  
  
Progetti deve sempre essere:  
  
-   Supporta la possibilità di aggiungere le cartelle dei progetti per organizzare il contenuto di progetto  
  
-   Gestire un modello coerente per la persistenza del progetto  
  
Progetti devono gestire anche modelli di interazione coerente per:  
  
-   Rimozione di elementi di progetto  
  
-   Salvataggio di documenti  
  
-   Modifica delle proprietà di progetto  
  
-   Modifica il progetto in una visualizzazione alternativa  
  
-   Operazioni di trascinamento e rilascio  
  
### <a name="drag-and-drop-interaction-model"></a>Modello di interazione di trascinamento e rilascio  
Progetti classificare se stesso come base di riferimento (in grado di rendere persistente solo i riferimenti a elementi di progetto nel servizio di archiviazione), (in grado di mantenere solo gli elementi di progetto fisicamente archiviate all'interno di una gerarchia del progetto), basato su directory o mista (in grado di mantenere i riferimenti o gli elementi fisici). L'IDE supporta tutti e tre i tipi di progetti contemporaneamente all'interno di **Esplora**.  
  
Da una prospettiva di trascinamento e rilascio, è consigliabile applicare le caratteristiche seguenti per ogni tipo di progetto all'interno di **Esplora**:  
  
-   **Progetto basato sul riferimento:** il punto importante è che il progetto è trascinando intorno a un riferimento a un elemento nel servizio di archiviazione. Quando un progetto basato sul riferimento funge da origine per un'operazione di spostamento, è necessario rimuovere solo il riferimento all'elemento dal progetto. L'elemento non deve effettivamente eliminato dal disco rigido. Quando un progetto basato sul riferimento funge da destinazione per un'operazione di spostamento (o copia), è necessario aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.  
  
-   **Progetto basato su directory:** trascinamento intorno l'elemento fisico anziché un riferimento da un punto di vista di trascinamento e rilascio, il progetto. Quando un progetto basato su directory funge da origine per un'operazione di spostamento, deve finire eliminazione dell'elemento fisico dal disco rigido, nonché di rimuoverlo dal progetto. Quando un progetto basato su directory funge da destinazione per un'operazione di spostamento (o copia), deve creare una copia dell'elemento di origine nella posizione di destinazione.  
  
-   **Progetto di destinazione mista:** da un punto di vista di trascinamento e rilascio, il comportamento di questo tipo di progetto è in base alla natura dell'elemento trascinato (un riferimento a un elemento nel servizio di archiviazione) o l'elemento stesso. Il comportamento corretto per i riferimenti e gli elementi fisici descritte in precedenza.  
  
Se fossero un solo tipo di progetto nel **Esplora**, operazioni di trascinamento e rilascio sarà molto semplice. Poiché ogni sistema del progetto ha la possibilità di definire il comportamento di trascinamento e rilascio, seguire determinate linee guida (in base al comportamento di trascinamento e rilascio di Windows Explorer) per garantire un'esperienza utente prevedibile:  
  
-   Un invariato operazione di trascinamento **Esplora** (quando Ctrl né MAIUSC vengono mantenuti verso il basso) deve risultare in un'operazione di spostamento.  
  
-   Operazione di trascinamento di MAIUSC dovrebbe restituire anche un'operazione di spostamento.  
  
-   Operazione di trascinamento di CTRL dovrebbe restituire un'operazione di copia.  
  
-   Sistemi di progetto basato sul riferimento e mista supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti sono la destinazione di un'operazione di trascinamento e rilascio (quando **Ctrl + Maiusc** viene tenuto premuto), dovrebbe restituire un riferimento all'elemento da aggiungere al progetto  
  
Non tutte le operazioni di trascinamento e rilascio sono appropriate per combinazioni di base di riferimento basate su directory progetti e misti. In particolare, è difficile fingono di consentire un'operazione di spostamento tra un progetto basato su directory di origine e di un progetto di destinazione basato sul riferimento perché il progetto di origine basato su directory sarà necessario eliminare l'elemento di origine al termine dello spostamento. Il progetto di destinazione basato sul riferimento quindi sarebbe necessario un riferimento a un elemento eliminato.  
  
È inoltre fuorviante per fingono di consentire un'operazione di copia tra questi tipi di progetti perché il progetto di destinazione basato sul riferimento non deve fare una copia indipendente dell'elemento di origine. Analogamente, Ctrl + Maiusc trascinamento di un progetto di destinazione basato su directory non è consentita perché è in grado di mantenere riferimenti a un progetto basato su directory. Nei casi in cui l'operazione di trascinamento e rilascio non è supportata, l'IDE deve impedire l'eliminazione e indicare all'utente il cursore di non rilascio (mostrato nella seguente tabella puntatore).  
  
Per implementare correttamente il comportamento di trascinamento e rilascio, il progetto di origine dell'operazione di trascinamento deve comunicare sua natura nel progetto di destinazione. (Ad esempio, è basato sul riferimento o directory?) Queste informazioni sono indicate per il formato degli Appunti che viene offerto dall'origine. Come origine di trascinamento (un'operazione di copia negli Appunti) un progetto deve offrire uno `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` , rispettivamente, a seconda se il progetto è basato su directory o riferimento. Entrambi questi formati presentano lo stesso contenuto di dati, è simile a Windows `CF_HDROP` formattare ad eccezione del fatto che gli elenchi di stringhe, anziché essere nomi di file, sono un double -`NULL` terminato l'elenco di `Projref` stringhe (come restituito dal `IVsSolution::GetProjrefOfItem`o `::GetProjrefOfProject` a seconda dei casi).  
  
Come destinazione di un rilascio (o l'operazione Incolla negli Appunti), un progetto deve accettare entrambi `CF_VSREFPROJECTITEMS` e `CF_VSSTGPROJECTITEMS`, anche se la gestione dell'operazione di trascinamento e rilascio esatto varia a seconda della natura del progetto di destinazione e il progetto di origine. Il progetto di origine dichiara sua natura, che offre `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS`. La destinazione del trascinamento in grado di riconoscere il proprio natura e pertanto dispone di informazioni sufficienti per decidere come per se sposta, copia o collegamento deve essere eseguito. L'utente modifica anche premendo Ctrl, MAIUSC, o sia Ctrl e MAIUSC deve essere eseguita l'operazione di trascinamento e rilascio. È importante per la destinazione di rilascio indicare in modo corretto verrà eseguita in anticipo in quale operazione relativo `DragEnter` e `DragOver` metodi. Il **Esplora** riconosce automaticamente se il progetto di origine e il progetto di destinazione sono nello stesso progetto.  
  
In particolare non è possibile trascinare gli elementi di progetto attraverso istanze di Visual Studio (ad esempio, da un'istanza di devenv.exe a un altro). Il **Esplora** direttamente disabilita questo.  
  
L'utente deve essere sempre in grado di determinare l'effetto di un'operazione di trascinamento e rilascio selezionando un elemento, trascinarlo nella posizione di destinazione e osservare che i seguenti puntatori del mouse viene visualizzato prima del rilascio dell'elemento:  
  
| Puntatore del mouse | Comando | Descrizione |  
| :---: | --- | --- |  
| ![Icona di "Nessun trascinamento" del mouse](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | Nessun rilascio | Elemento non può essere rilasciato nella posizione specificata. |  
| ![Icona "copia" del mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Copia | Elemento verrà copiato nel percorso di destinazione. |  
| ![Mouse "Sposta" icona](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Move | Elemento verrà spostato nel percorso di destinazione. |  
| ![Icona "Aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Aggiungi riferimento | Verrà aggiunto un riferimento all'elemento selezionato nel percorso di destinazione. |

#### <a name="reference-based-projects"></a>progetti di tipo riferimento  
 Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine selezionato per i progetti di destinazione in base a cui fa riferimento:  
  
| Modificatore | Category | Elemento di origine: / collegamento di riferimento | Elemento di origine: fisico elemento o un file system (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nessun modificatore | Operazione | Move | Collegamento |  
| Nessun modificatore | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |  
| Nessun modificatore | Origine | Elimina riferimento all'elemento originale | Mantiene l'elemento originale |  
| Nessun modificatore | Risultato | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_LINK`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |  
| Maiusc + trascinamento | Operazione | Move | Nessun rilascio |  
| Maiusc + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Nessun rilascio |  
| Maiusc + trascinamento | Origine | Elimina riferimento all'elemento originale | Nessun rilascio |  
| Maiusc + trascinamento | Risultato | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | Nessun rilascio |  
| CTRL + trascinare | Operazione | Copia | Nessun rilascio |  
| CTRL + trascinare | destinazione | Aggiunge il riferimento alla voce originale | Nessun rilascio |  
| CTRL + trascinare | Origine | Mantiene il riferimento all'elemento originale | Nessun rilascio |  
| CTRL + trascinare | Risultato | `DROPEFFECT_COPY`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | Nessun rilascio |  
| CTRL + MAIUSC + trascinamento | Operazione | Collegamento | Collegamento |  
| CTRL + MAIUSC + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |  
| CTRL + MAIUSC + trascinamento | Origine | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |  
| CTRL + MAIUSC + trascinamento | Risultato | `DROPEFFECT_LINK`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_LINK`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |  
| CTRL + MAIUSC + trascinamento | Nota | Come il comportamento di trascinamento e rilascio per i tasti di scelta rapida in Esplora risorse. ||  
| Taglia e Incolla | Operazione | Move | Collegamento |  
| Taglia e Incolla | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |  
| Taglia e Incolla | Origine | Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale |  
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento rimane nella posizione originale nel servizio di archiviazione |  
| Copiare e incollare | Operazione | Copia | Collegamento |  
| Copiare e incollare | Origine | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |  
| Copiare e incollare | Risultato | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |  
| Copiare e incollare | Operazione | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento rimane nella posizione originale nel servizio di archiviazione |  
  
#### <a name="directory-based-projects"></a>Progetti basati su directory  
Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine selezionato per i progetti basati su directory di destinazione:  
  
| Modificatore | Category | Elemento di origine: / collegamento di riferimento | Elemento di origine: fisico elemento o un file system (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nessun modificatore | Operazione | Move | Move |  
| Nessun modificatore | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |  
| Nessun modificatore | Origine | Elimina riferimento all'elemento originale | Elimina riferimento all'elemento originale | | Nessun modificatore | Risultato | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |  
| Maiusc + trascinamento | Operazione | Move | Move |  
| Maiusc + trascinamento | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |  
| Maiusc + trascinamento | Origine | Elimina riferimento all'elemento originale | Elimina elemento dal percorso originale |
| Maiusc + trascinamento | Risultato | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |  
| CTRL + trascinare | Operazione | Copia | Copia |  
| CTRL + trascinare | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |  
| CTRL + trascinare | Origine | Mantiene il riferimento all'elemento originale | Mantiene il riferimento all'elemento originale |  
| CTRL + trascinare | Risultato | `DROPEFFECT_COPY`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_COPY`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |  
| CTRL + MAIUSC + trascinamento | | Nessun rilascio | Nessun rilascio |  
| Taglia e Incolla | Operazione | Move | Move |  
| Taglia e Incolla | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |  
| Taglia e Incolla | Origine | Elimina riferimento all'elemento originale | Elimina elemento dal percorso originale |  
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento viene eliminato dalla posizione originale nel servizio di archiviazione |  
| Copiare e incollare | Operazione | Copia | Copia |  
| Copiare e incollare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |  
| Copiare e incollare | Origine | Mantiene l'elemento originale | Mantiene l'elemento originale |  
| Copiare e incollare | Risultato | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento rimane nell'archivio di aggiuntivi percorso originale |
  
#### <a name="mixed-target-projects"></a>Progetti di destinazione mista  
Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine selezionato per i progetti di destinazione mista:  
  
| Modificatore | Category | Elemento di origine: / collegamento di riferimento | Elemento di origine: fisico elemento o un file system (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Nessun modificatore | Operazione | Move | Move |
| Nessun modificatore | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Nessun modificatore | Origine | Elimina riferimento all'elemento originale | Elimina riferimento all'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_ MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_ MOVE`viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nel servizio di archiviazione |
| Maiusc + trascinamento | Operazione | Move | Move |
| Maiusc + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Maiusc + trascinamento | Origine | Elimina riferimento all'elemento originale | Elimina elemento dal percorso originale | 
| Maiusc + trascinamento | Risultato | `DROPEFFECT_ MOVE`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_ MOVE`viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nel servizio di archiviazione |
| CTRL + trascinare | Operazione | Copia | Copia |
| CTRL + trascinare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| CTRL + trascinare | Origine | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL + trascinare | Risultato | `DROPEFFECT_ COPY`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_ COPY`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |
| CTRL + MAIUSC + trascinamento | Operazione | Collegamento | Collegamento |
| CTRL + MAIUSC + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge riferimento all'elemento di origine originale |
| CTRL + MAIUSC + trascinamento | Origine | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL + MAIUSC + trascinamento | Risultato | `DROPEFFECT_ LINK`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione | `DROPEFFECT_ LINK`viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nel servizio di archiviazione |
| Taglia e Incolla | Operazione | Move | Move |
| Taglia e Incolla | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| Taglia e Incolla | Origine | Elimina riferimento all'elemento originale | Elimina elemento dal percorso originale |
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento viene eliminato dalla posizione originale nel servizio di archiviazione |
| Copiare e incollare | Operazione | Copia | Copia |
| Copiare e incollare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Copiare e incollare | Origine | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copiare e incollare | Risultato | Elemento rimane nella posizione originale nel servizio di archiviazione | Elemento rimane nella posizione originale nel servizio di archiviazione |
  
Questi dettagli devono essere prese in considerazione quando si implementa il trascinamento nel **Esplora**:  
  
-   Progettare per più scenari di selezione.  
  
-   I nomi di file (percorso completo) devono essere univoci all'interno del progetto di destinazione o l'eliminazione non è consentita.  
  
-   I nomi delle cartelle deve essere univoci (tra maiuscole e minuscole) a livello di vengono rilasciati.  
  
-   Vi sono differenze di comportamento tra i file che sono chiusi o aperti al momento dell'operazione di trascinamento (non indicate negli scenari precedenti).  
  
-   File di primo livello si comportano in modo leggermente diverso rispetto ai file nelle cartelle.  
  
Un altro problema di viene illustrato come gestire le operazioni di spostamento per gli elementi che dispongono di editor o finestre di progettazione aperte. Il comportamento previsto è come indicato di seguito (si applica a tutti i tipi di progetto):  
  
1.  Se l'aprire editor/finestra di progettazione non dispone di eventuali modifiche non salvate, quindi la finestra dell'editor di progettazione deve automaticamente chiuso.  
  
2.  Nel caso di aprire editor/finestra di progettazione le modifiche non salvate, l'origine dell'operazione di trascinamento deve attendere per l'eliminazione e quindi chiedere all'utente di salvare le modifiche non salvate per i documenti aperti prima di chiudere la finestra con un messaggio simile al seguente :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
In questo modo l'utente la possibilità di salvare i lavori in corso prima che la destinazione effettui la copia. Un nuovo metodo `IVsHierarchyDropDataSource2::OnBeforeDropNotify` è stato aggiunto per consentire questo tipo di gestione.  
  
La destinazione verrà quindi copiare lo stato dell'elemento perché è nello spazio di memorizzazione (senza includere le modifiche non salvate nell'editor, se l'utente ha scelto **n**). Dopo la destinazione è stata completata la copia (in `IVsHierarchyDropDataSource::Drop`), l'origine è data la possibilità di completare la parte di eliminazione dell'operazione di spostamento (in `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Deve essere lasciato aperto alcun editor con le modifiche non salvate. Per tali documenti con le modifiche non salvate, ciò significa che la fase di copia dell'operazione di spostamento verrà eseguita ma verrà interrotta la parte di eliminazione. In uno scenario di selezione più quando l'utente sceglie **n**, tali documenti con le modifiche non salvate non devono essere chiuso o rimossi, ma quelli senza modifiche non salvate deve essere chiuso e rimosso.