---
title: Menu e comandi di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16f67faf7ffe3a3fd119b7ddf002ab463822a830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu e comandi di Visual Studio
## <a name="command-usage"></a>Sintassi del comando  
  
### <a name="overview"></a>Panoramica  
 A differenza di Microsoft Office, ovvero un gruppo che include molti prodotti distinti, Visual Studio contiene molti prodotti che contribuisca ognuno i set di comandi all'IDE di Visual Studio globale. L'IDE gestisce la complessità di migliaia di comandi filtrando le funzionalità disponibili per l'utente in base al contesto.  
  
 Quando viene modificato un contesto utente - ad esempio il passaggio da una finestra di progettazione a una finestra di modifica del codice - funzionalità non è correlata a viene rimosso il nuovo contesto. Allo stesso tempo, nuova funzionalità viene visualizzata insieme alle informazioni dinamiche correlate, ad esempio le opzioni di proprietà e della casella degli strumenti. L'utente non è opportuno notare lo scambio del set di comandi disponibili. Se l'utente è distratti o confusi da comandi visualizzati o scomparire, la progettazione dell'interfaccia utente deve quindi regolazione. Il contesto dell'utente corrente è sempre indicato in uno o più modi, ad esempio nella barra del titolo IDE, la finestra proprietà o la finestra di dialogo Pagine delle proprietà.  
  
 Barre dei comandi consentono flessibilità nell'interfaccia utente. L'unico comando strutture inerenti a Visual Studio ambiente sono nel menu principale e barra dei comandi principale, che può essere personalizzata e anche nascosta. Altre barre dei comandi vengono visualizzati e interrompersi in base allo stato dell'applicazione. Editor di documento e le finestre degli strumenti può anche contenere barre degli strumenti incorporate all'interno i bordi della finestra.  
  
#### <a name="basic-guidelines"></a>Linee guida di base  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utilizzare comandi condivisi esistenti, gruppi di comandi e menu, ove possibile.  
 Poiché i comandi vengono visualizzati in genere basata su contesto, l'utilizzo di menu condivisi esistenti e i gruppi di comandi assicura che la struttura di comando rimane relativamente stabile tra le modifiche al contesto. Riutilizzo di comandi condivisi e inserire nuovi comandi vicino comandi condivisi correlati inoltre riduce la complessità IDE e crea un'esperienza utente più semplice. Se un nuovo comando deve essere definita, provare a inserirlo in un gruppo di comando condiviso esistente. Se deve essere definito un nuovo gruppo, è necessario inserirlo in un menu esistente condiviso vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Non creare le icone per ogni comando.  
 Fare attenzione prima di creare un'icona del comando. Icone devono essere create solo per i comandi che:  
  
-   vengono visualizzati in una barra degli strumenti predefinita.  
  
-   possono essere aggiunti dagli utenti per una barra degli strumenti tramite il **Personalizza...**  finestra di dialogo.  
  
-   è associata un'icona con la stessa azione in un altro prodotto Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitare l'aggiunta di tasti di scelta rapida  
 La maggior parte degli utenti utilizzano una piccola frazione di tutti i collegamenti disponibili. In caso di dubbi, non si associano le funzionalità di un tasto di scelta rapida. Lavoro con il proprio utente esperienza team prima di aggiungere nuove scelte rapide.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Assegnare i comandi di una posizione di menu predefinita.  
 Tenere presente che i comandi verranno personalizzati da altri utenti e progettare di conseguenza. Non è non esiste un comando nascosto. Vengono visualizzati tutti i comandi di Visual Studio nel **strumenti > Personalizza** finestra di dialogo, la finestra di comando, il completamento automatico di **strumenti > Opzioni > tastiera** finestra di dialogo e l'ambiente DTE (Development Tools). Verificare che i comandi di un nome e una descrizione comando nel file CTC in modo che gli utenti poterli trovare facilmente.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplicato non condivisi i comandi in una barra degli strumenti incorporata.  
 È utile posizionare i comandi in stretta vicinanza nell'area di interesse dell'utente. Un modo per eseguire questa operazione consiste nel creare una barra degli strumenti incorporata nella parte superiore del documento o finestra degli strumenti dell'editor. I comandi posizionati sulla barra degli strumenti devono essere specifici per l'area di contenuto all'interno della finestra. Duplicato non condivisi i comandi in queste barre degli strumenti. Ad esempio, non inserire un'icona di "Salva" all'interno di una barra degli strumenti incorporata.  
  
### <a name="content-and-command-visibility"></a>Visibilità di comando e contenuta  
 Comandi sono presenti negli ambiti seguenti: **ambiente**, **gerarchia**, e **documento**. Conoscere ogni ambito per essere certi di posizionamento del comando.  
  
 I comandi di **ambiente** ambito stabilire un contesto primario e sono condivise tra più contesti. Modificano la visibilità o la disposizione dei documenti e finestre degli strumenti. Tra i comandi nell'ambiente di ambito sono **nuovo progetto**, **Connetti al Server**, **Connetti processo**, **Taglia**,  **Copia**, **Incolla**, **trovare**, **opzioni**, **personalizzare**, **nuova finestra**, e **visualizzare la Guida**.  
  
 I comandi di **gerarchia** ambito gestire gerarchie di Visual Studio, tra cui **progetto**, **Team**, e **dati**. Ad esempio, si riferiscono al sottocontesto del progetto - **Debug**, **compilare**, **Test**, **architettura**, o **analizza** . Tra i comandi nella gerarchia di ambito sono **Aggiungi nuovo elemento**, **nuova Query**, **impostazioni progetto**, **Aggiungi nuova origine dati**, **Avvia procedura guidata prestazioni**, e **nuovo diagramma**.  
  
 I comandi di **documento** act ambito sul contenuto di un documento, ad esempio di codice, struttura o una query elemento di lavoro (WIQ). Sono inoltre operare sulla visualizzazione di una finestra degli strumenti o in caso contrario sono specifici di tale finestra degli strumenti. Comandi di ambito dei documenti obbliga anche per gli oggetti di file che sono a loro volta gerarchia specifiche, ad esempio **rimuovere dal progetto**. Tra i comandi nel documento sono ambito **refactoring > rinominare**, **Crea copia di elemento di lavoro**, **Espandi tutto**, **Comprimi tutto**, e **Crea attività definita dall'utente**.  
  
### <a name="command-placement-decisions"></a>Decisioni di selezione host di comando  
 Una volta che si è deciso di creare un comando, è necessario determinare la posizione appropriata e se si desidera creare un tasto di scelta rapida. Seguire questo percorso di decisione per stabilire dove posizionare il comando:  
  
 ![Grafico di decisione posizione comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")  
  
 **Percorso di decisione per la selezione di comando in Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Posizionamento di comando di menu  
  
#### <a name="main-menu-bar"></a>Barra dei menu principale  
 Barra dei menu principale deve essere il percorso standard per i comandi di tutti i pacchetti menu contestuali che contribuiscono all'interfaccia utente. Barra dei menu principale si differenzia da altre strutture di comando nell'ambiente viene utilizzato per controllare quali comandi sono visibili. Tutte le altre barre dei comandi disabilitare semplicemente i comandi che sono fuori dal contesto, se vengono inseriti in un menu o una barra degli strumenti.  
  
 L'ambiente definisce un set di comandi compilato nella barra dei menu principale che sono comuni a più domini di attività e l'intero IDE. Questi comandi sono sempre visibili indipendentemente dal fatto che di cui VSPackage vengono caricati nell'ambiente. Sebbene VSPackage possono estendere questo set di comandi, il comando set da ogni prodotto e la posizione dei relativi comandi è la responsabilità di ogni team.  
  
 La struttura del menu principale di Visual Studio possa essere suddivisi in categorie di menu seguenti:  
  
##### <a name="core-menus"></a>Menu principale  
  
-   File  
  
-   Modifica  
  
-   Visualizza  
  
-   Strumenti  
  
-   Finestra  
  
-   ?  
  
##### <a name="project-specific-menus"></a>Menu specifici del progetto  
  
-   Progetto  
  
-   Compila  
  
-   Debug  
  
##### <a name="context-specific-menus"></a>Menu specifici del contesto  
  
-   Team  
  
-   Dati  
  
-   Test  
  
-   Architettura  
  
-   Analyze  
  
##### <a name="document-specific-menus"></a>Menu specifici del documento  
  
-   Formato  
  
-   Table  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Quando si progettano i menu principali, è necessario attenersi a queste regole:  
  
-   Non superare 25 elementi di livello superiore in un contesto specifico  
  
-   I menu non devono mai superare 600 pixel di altezza.  
  
-   Valutare un menu principale in più contesti, ad esempio in SKU finale e il profilo generale.  
  
-   Menu a comparsa sono accettabili.  
  
-   Menu a comparsa devono contenere almeno tre elementi e non più di sette.  
  
-   Menu a comparsa devono passare solo un livello di profondità: alcune voci di menu di Visual Studio dispongano sottomenu CSS, ma non è consigliabile in questo modello.  
  
-   Utilizzare i separatori non più di sei. Raggruppamenti devono rispettare la figura seguente:  
  
     ![Linee guida per il raggruppamento di menu principale](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")  
  
-   Mentre non è necessario disporre di ogni raggruppamento nella figura, l'aggiunta di ulteriori raggruppamenti è limitato.  
  
-   Ogni raggruppamento deve essere da due a sette voci di menu.  
  
#### <a name="main-menu-ordering"></a>Menu principale di ordinamento  
 Prima di aggiungere un nuovo elemento di livello superiore, è consigliabile inserire il comando in un menu di primo livello esistente. Quando si aggiunge un nuovo menu di primo livello, assicurarsi di inserirlo nella posizione corretta. Decidere se il menu è specifico di progetto, di contesto o documento. Mantenere il nome del menu di primo livello conciso e utilizzare solo una parola.  
  
 I menu principali devono delimitatore il resto dei comandi. File, modifica e visualizzazione deve essere sempre a sinistra e a strumenti, finestra e della Guida in linea deve essere sempre a destra.  
  
#### <a name="context-menus"></a>Menu di scelta rapida  
 Inserimento di una quantità eccessiva funzionalità disponibili nel menu di scelta rapida risultati in un'interfaccia difficile da apprendere. Tutte le funzionalità principali devono essere disponibili tramite la barra dei menu principale. Posizionamento dei comandi deve essere riconciliato con i comandi esistenti per evitare i comandi duplicati. Per i menu di scelta rapida, la shell definisce i gruppi di menu standard che devono essere inclusi, a seconda che il menu di scelta rapida sia per la soluzione, un nodo di progetto o un elemento di progetto.  
  
 Quando si progettano i menu di scelta rapida, rispettare le stesse regole per il menu principale e inoltre:  
  
-   Non superare 25 voci di menu di primo livello.  
  
-   Menu a comparsa sono accettabili ma deve superare un livello di profondità: non utilizzare mai CSS riquadri a comparsa.  
  
-   Utilizzare i separatori non più di sei.  
  
### <a name="command-placement-in-toolbars"></a>Posizionamento di comandi nelle barre degli strumenti  
  
#### <a name="general-toolbars"></a>Barre degli strumenti generale  
 Durante la progettazione e la disposizione delle barre degli strumenti, seguire questi standard:  
  
-   Non usare più di un verbo per ogni pulsante. Un pulsante = un'azione.  
  
-   Usare testo con l'icona solo se è necessario essere rafforzata con l'etichetta.  
  
-   Usare una casella combinata esclusivamente per le proprietà che verranno trasferite più volte in una sessione. In caso contrario, espongono la proprietà in un' posizione.  
  
-   La larghezza di una casella combinata deve essere uguale la larghezza dell'elemento all'interno di finestra + 30% più lungo. Ad esempio, se l'elemento più lungo è 200 pixel, della casella combinata deve essere 260 pixel di larghezza.  
  
-   Limitare l'utilizzo di separatori. L'utilizzo di un separatore accanto a un elenco a discesa è un anti-pattern, poiché la forma di elenco a discesa stesso agisce come un separatore visivo.  
  
-   Gruppi di icona devono contenere da tre a sei icone.  
  
-   Se alcuni comandi utili più qualificatori, usare un pulsante di menu combinato che archivia l'ultima impostazione:  
  
     ![In Visual Studio pulsanti di menu combinato](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")  
  
     **Esempio di un pulsante di menu combinato. I sei comandi a sinistra invece rientrino in un unico pulsante.**  
  
#### <a name="product-specific-toolbars"></a>Barre degli strumenti specifici del prodotto  
 Ogni prodotto può fornire una barra degli strumenti predefinita contenente utilizzati di frequente e importanti comandi e barra degli strumenti predefinita di ogni prodotto vengono visualizzati la prima volta Visual Studio viene avviato dopo il prodotto sia installato.  
  
 I prodotti devono anche sfruttare menu forniti dall'IDE e gruppi di comandi condiviso. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso concepito per organizzare i comandi correlati in modo significativo per l'utente. È importante sfruttare questa struttura comando condiviso per ridurre la complessità.  
  
#### <a name="global-toolbars"></a>Barre degli strumenti globale  
 Barre degli strumenti globale sono necessari in base a destra di una riga predefinita. Quando si crea una nuova barra degli strumenti globale, seguire le linee guida per quel tipo di barra degli strumenti.  
  
 **Linee guida generali sulla barra degli strumenti:**  
  
-   Ogni barra degli strumenti è 24 pixel common Controls (gripper, overflow).  
  
-   Ogni pulsante della barra degli strumenti è 22 pixel incluse la spaziatura. Effettua l'icona di un pulsante di menu combinato aggiunge un altro 11 pixel di larghezza.  
  
-   È consentita la duplicazione dei comandi tra barre degli strumenti.  
  
 **Barre degli strumenti specifici del documento** vengono visualizzati quando un determinato tipo di file è attivo e scompare quando un tipo di file diversi diventa attivo.  
  
-   Barre degli strumenti specifici del documento non può avere più di 12 pulsanti.  
  
-   La larghezza totale della barra degli strumenti non può superare i 300 pixel.  
  
-   Ogni tipo di file può avere uno degli strumenti incorporata o una barra degli strumenti globale specifici del documento, ma non entrambi.  
  
 **Barre degli strumenti specifici del contesto** vengono visualizzati quando un determinato contesto viene impostato e tendono a rimanere attive per lunghi periodi di tempo.  
  
-   Il limite di pulsante per tutte le barre degli strumenti specifici del contesto è 18.  
  
-   Se la maggior parte degli utenti non in modo coerente utilizzano i comandi della barra degli strumenti quando il contesto è attivo, quindi non associare questa barra degli strumenti con un contesto.  
  
-   Verificare che la barra degli strumenti scomparirà quando si esce dal contesto. Nessuna di queste barre degli strumenti dovrebbe essere visualizzato all'avvio.  
  
 **Barre degli strumenti senza alcun contesto** non vengono mai visualizzati automaticamente. Viene visualizzata solo quando l'utente li attiva. Mantenere la larghezza massima di 200 pixel in seguito.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Organizzazione generali e i gruppi definiti shell  
 Utilizzare i comandi condivisi esistenti, gruppi di comandi e menu. Se un nuovo comando deve essere definita, provare a inserirlo in un gruppo di comando condiviso esistente. Se deve essere definito un nuovo gruppo, provare a inserirlo in un menu esistente condiviso vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello. Questo riduce la complessità di comando assicurando commandplacement coerente nell'IDE.  
  
 Condiviso **formato** menu, in genere mostrato nel contesto delle finestre di documento di stile di finestra di progettazione, come illustrato nell'immagine seguente:  
  
 ![Menu di Visual Studio formato con callout](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")  
  
 **Gruppi di menu in Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Riduzione e il riutilizzo dei comandi  
 I comandi vengono in genere visualizzati in base sul contesto, per ridurre il numero di comandi che viene visualizzata in qualsiasi momento. Tuttavia, è inoltre necessario riutilizzare menu condivisi esistenti e i gruppi di comandi per garantire che la struttura di comando relativamente stabile tra le modifiche nel contesto.  
  
 Riutilizzo di comandi condivisi e inserire nuovi comandi vicino comandi condivisi correlati riduce la complessità IDE e crea un'esperienza utente più semplice.  
  
## <a name="naming-commands"></a>Denominazione dei comandi  
  
### <a name="naming-conventions"></a>Convenzioni di denominazione  
 Comando coerenza di denominazione è fondamentale in modo che gli utenti possono trovare ed eseguire comandi, tramite la riga di comando o un'associazione a un tasto di scelta rapida. I nomi dei comandi inoltre comprendere l'utente scopo viene utilizzato un comando quando viene visualizzato in una barra degli strumenti o in un menu di contesto o di propagazione.  
  
#### <a name="when-naming-commands"></a>Denominazione dei comandi quando:  
  
-   Creare testo in modo da facilitarne la localizzazione. Per ulteriori informazioni sulla localizzazione del testo, vedere [internazionalizzazione per Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   In modo conciso. I comandi devono utilizzare non più di tre parole.  
  
-   Utilizzare maiuscole lettere maiuscole/minuscole: la prima lettera di ogni parola deve essere in maiuscolo. Per ulteriori informazioni sulla formattazione del testo in Visual Studio, vedere [lo stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Prendere in considerazione in cui verrà inserito il comando. Si tratta di un menu di primo livello o un riquadro a comparsa? Ad esempio, quando i comandi di allineamento di raggruppamento nel riquadro a comparsa, il comando di primo livello devono essere "Align" e i comandi del riquadro a comparsa deve essere "Left" "Right", "Center", "giustifica" e così via. Sarebbe ridondante per denominare i comandi del riquadro a comparsa "Allinea a sinistra" o "Right Align."  
  
     ![Menu di Visual Studio formato](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>Usare le icone con comandi  
 Essere riserva nell'uso dell'associazione con i comandi di icona. Anche se l'associazione di un'immagine univoca con un comando hastens il possibilità dell'utente per identificare il comando, sempre in modo efficiente e rappresentazione visiva si verificano con l'utilizzo eccessivo di immagine. Le regole seguenti utili per decidere se creare un'icona del comando.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Utilizzare un'icona con un comando solo se:  
  
-   Il comando stesso contiene un'icona associata in un'altra importante prodotto Microsoft, ad esempio una delle applicazioni Microsoft Office.  
  
-   Il comando verrà inserito in una barra degli strumenti predefinita.  
  
-   Il comando è un comando speciali che gli utenti possono aggiungere a una barra degli strumenti utilizzando il **"Personalizza..."** finestra di dialogo.  
  
## <a name="access-and-shortcut-keys"></a>Tasti di scelta rapida e di accesso  
  
### <a name="overview"></a>Panoramica  
 Esistono due tipi di chiave da tastiera:  
  
-   **Le chiavi di accesso** (noto anche come tasti di scelta rapida) consentono l'accesso della tastiera tramite i comandi di menu per l'esecuzione di comandi e a ogni etichetta nella finestra di dialogo dell'interfaccia utente. Tasti di scelta sono principalmente per scopi di accessibilità, siano assegnati a tutti i menu e controlli la maggior parte delle finestre di dialogo, non sono pensati per essere memorizzate, interessano solo la finestra corrente e sono localizzati.  
  
-   **Tasti di scelta rapida** principalmente usare il controllo (Ctrl) e sequenze di tasti funzione (Fn). Sono più progettati per gli utenti avanzati e aiuto nella produttività. Essi vengono assegnati solo per i comandi utilizzati più frequentemente e consentire un rapido accesso mentre viene ignorata dal menu principale. Tasti di scelta rapida sono destinati a essere memorizzate e per tale motivo deve essere assegnato coerente con lo schema di profilo. Schemi di tasti di scelta rapida possono variare da un profilo per un profilo. Un utente può personalizzare i tasti di scelta rapida tramite **strumenti > Opzioni > tastiera**.  
  
### <a name="assigning-access-keys"></a>Assegnazione di tasti  
 Chiavi di accesso è costituito da chiavi Alt più caratteri alfanumerici. Assegnare una chiave di accesso per ogni voce di menu senza eccezione. Seguire le convenzioni comuni per l'assegnazione di tasti di scelta e Windows. ad esempio, la chiave di accesso per **File > Nuovo** deve essere sempre **ALT + F, N**.  
  
 Non utilizzare espressa in pixel-solo lettere, ad esempio "i" (in caratteri maiuscoli o minuscoli) o una "l" minuscola ed evitare l'utilizzo di caratteri con tratti discendenti (g, j, p, q e y) in cui sono difficili da individuare.  
  
 Evitare di utilizzare le chiavi duplicate, quando possibile. Nei casi in cui è inevitabile la duplicazione, il sistema di menu vengono gestiti i conflitti, ciclicamente tutti i comandi che usano la chiave. Ad esempio, per un ipotetico "Number" comando del menu File che coincide con la chiave di accesso "N", **ALT + F, N** creerebbe un nuovo file, e **Alt, F, N, N** eseguire il comando "Number".  
  
### <a name="assigning-shortcut-keys"></a>L'assegnazione di tasti di scelta rapida  
 Evitare l'assegnazione di nuovi tasti di scelta rapida, poiché non sono necessari per ogni comando e imposta il sistema e della memoria di utente, se l'utilizzo eccessivo. Dati dall'analisi analisi utilizzo software (CEIP) indicano che gli utenti di Visual Studio utilizzano solo un piccolo subset di scelta rapida integrati.  
  
 Quando si definiscono i tasti di scelta rapida, seguire queste regole:  
  
-   **Usare il controllo (Ctrl) e sequenze di tasti funzione (Fn).**  
  
-   **Tasti di scelta rapida utilizzati di frequente vengono conservati.** Gestire i collegamenti più diffusi.  
  
-   **Facilitare l'editor tasti di scelta rapida digitare.** Associare al tipo di scelta rapida per i comandi che gli sviluppatori devono pertanto la maggior parte durante la scrittura di codice. Ad esempio, **Edit.InvokeSmartTag** deve disporre di un tasto di scelta rapida come Ctrl + e non Alt + Maiusc + F10.  
  
-   **Cercare in modo coerente con tema di scelta rapida.**  
  
-   **Attenersi alle linee guida di Windows per determinare quali modificatore chiavi da utilizzare.** Utilizzare le combinazioni di tasti Ctrl per i comandi che hanno effetti su larga scala, ad esempio i comandi che si applicano all'intero documento. Utilizzare le combinazioni di tasti MAIUSC per i comandi che estendono o integrano le azioni del tasto di scelta rapida standard. Non utilizzare combinazioni di Ctrl + Alt.  
  
-   **Rimuovere i collegamenti estranei.** Se si dispone di una funzionalità legacy, provare a rimuovere i collegamenti che vengono utilizzati con estrema infrequency (meno di 10 volte dai dati di analisi utilizzo software) o infrequency moderato (meno di 100 volte dai dati di analisi utilizzo software) se la chiave di accesso consente di accedere rapidamente allo stesso comando. Ad esempio: C ALT + H, verrà aperto il sommario della Guida /.  
  
 Non è un modo semplice per verificare la disponibilità di scelta rapida. Se si desidera aggiungere un collegamento, seguire questi passaggi:  
  
1.  Controllare l'elenco dei [scelte rapide da Visual Studio 2013](http://visualstudioshortcuts.com/2013/) per determinare se sono presenti comandi simili a quelle in uso con gruppo.  
  
2.  Passare a **strumenti > Opzioni > ambiente > tastiera** e il collegamento di test. Controllare che ogni schema di mappatura della tastiera elencati in "Applica il seguente schema di mappatura della tastiera aggiuntivi". Controllare i profili in generale, c#, VB e C++, come quelli condividere collegamenti univoci. Il collegamento è disponibile se non è mappata in una qualsiasi di queste posizioni.