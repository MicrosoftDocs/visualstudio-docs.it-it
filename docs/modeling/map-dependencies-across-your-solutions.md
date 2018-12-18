---
title: Mappare le dipendenze nelle soluzioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f5fd14ba1a2cdad08996b1494c0510f85b929006
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="map-dependencies-across-your-solutions"></a>Eseguire il mapping delle dipendenze nelle soluzioni

Per comprendere le dipendenze in tutto il codice, visualizzarle creando mappe codice. In questo modo è possibile vedere il funzionamento complessivo del codice senza leggere file e righe di codice.

![Visualizzare le dipendenze nelle soluzioni](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

**Ecco alcuni video**:

- [Comprensione delle dipendenze del codice tramite la visualizzazione](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)

- [Visualizza l'impatto di una modifica](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)

- [Informazioni sul codice complesso con mappe del codice](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understanding-complex-code-with-Code-Map-ENU)

## <a name="GetStarted"></a> Introduzione all'uso delle mappe codice

**Per usare le mappe codice saranno necessari**:
  
-   Visual Studio Enterprise per creare mappe codice tramite l'editor di codice, Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti.  
  
-   Visual Studio Professional per aprire le mappe codice, apportare modifiche limitate ed esplorare il codice.  
  
> [!WARNING]
>  Prima di condividere le mappe create in Visual Studio Enterprise con altri utenti che usano Visual Studio Professional, assicurarsi che tutti gli elementi nella mappa siano visibili (ad esempio elementi nascosti, gruppi espansi e collegamenti tra gruppi).  
  
 **È possibile eseguire il mapping delle dipendenze per il codice nei seguenti linguaggi**:  
  
-   Visual c# o Visual Basic in una soluzione o di assembly (con estensione dll o .exe)  
  
-   Codice C o C++ nativo o gestito in progetti Visual C++, file di intestazione (.h o `#include`) o file binari  
  
-   Progetti X++ e assembly creati da moduli .NET per Microsoft Dynamics AX  
  
 **Nota:** per progetti diversi da c# o Visual Basic, sono disponibili meno opzioni per l'avvio di una mappa del codice o l'aggiunta di elementi a una mappa codice esistente. Ad esempio, non è possibile fare clic con il pulsante destro del mouse su un oggetto nell'editor di testo di un progetto C++ e aggiungerlo a una mappa codice. Tuttavia, è possibile trascinare e rilasciare singoli elementi di codice o file da Esplora soluzioni, Visualizzazione classi e Visualizzatore oggetti.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Per visualizzare tutte le dipendenze nella soluzione  
  
1.  Aprire il menu **Architettura** .  
  
2.  Se è stata appena aperta la soluzione e non è stata ancora compilata o se il codice è stato modificato dall'ultima compilazione, scegliere **Genera mappa codici per la soluzione**.  
  
3.  Se il codice non è stato modificato dall'ultima compilazione, scegliere **Genera mappa codici per la soluzione senza compilazione** per accelerare la creazione della mappa.  
  
4.  [Visualizzare tutte le dipendenze](#SeeOverviewSource) per capire come usare le mappe codice per visualizzare le dipendenze complessive nella soluzione.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Per visualizzare dipendenze specifiche nella soluzione  
  
1.  Con la soluzione caricata, aprire **Esplora soluzioni**.  
  
2.  Selezionare i progetti, i riferimenti agli assembly, le cartelle, i file, i tipi o i membri di cui eseguire il mapping.  
  
3.  Nel **Esplora** sulla barra degli strumenti, scegliere **Mostra in mappa codice**![creare nuovo grafico dalla selezionato nodi pulsante](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). In alternativa, scegliere **Mostra in mappa codice**dal menu di scelta rapida. È anche possibile trascinare elementi da Visualizzazione classi o Visualizzatore oggetti in una mappa codice nuova o esistente.  
  
4.  [Visualizzare dipendenze specifiche](#SeeSpecificSource) per informazioni su come usare le mappe codice per visualizzare dipendenze specifiche nella soluzione.  
  
###  <a name="CreateEmptyMap"></a> Per aggiungere una nuova mappa codice vuota alla soluzione  
  
1.  In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione di primo livello. Scegliere **Aggiungi** , quindi **Nuovo elemento**.  
  
2.  In **Installato**scegliere **Generale**.  
  
3.  Nel riquadro destro scegliere **Documento grafico diretto** e quindi scegliere **Aggiungi**.  
  
     Ora si ha una mappa vuota, che viene visualizzata nella cartella **Elementi di soluzione** della soluzione.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Per creare una nuova mappa codice vuota senza aggiungerla alla soluzione  
  
1.  Aprire il menu **Architettura** e scegliere **Nuova mappa del codice sorgente**.  
  
     \- oppure -  
  
2.  Aprire il menu **File** e scegliere **Nuovo** , quindi **File**.  
  
3.  In **Installato**scegliere **Generale**.  
  
4.  Nel riquadro destro scegliere **Documento grafico diretto** e quindi scegliere **Apri**.  
  
     Ora si ha una mappa vuota, che non viene visualizzata nelle cartelle della soluzione.  
  
##  <a name="SeeOverviewSource"></a> Visualizzare tutte le dipendenze  
  
###  <a name="OverviewSource"></a> Visualizzare le dipendenze nella soluzione  
  
1.  Aprire il menu **Architettura** e scegliere **Genera mappa codici per la soluzione senza compilazione**.  
  
     ![Comando di generazione codice mappa](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
     Viene visualizzata una mappa che mostra gli assembly di primo livello e i relativi collegamenti aggregati. A una maggiore ampiezza del collegamento aggregato corrisponde un maggior numero di dipendenze che rappresenta.  
  
2.  Usare il pulsante **Legenda** sulla barra degli strumenti del codice per visualizzare o nascondere l'elenco di icone del tipo di progetto (ad esempio Test, Web e Progetto per telefono), gli elementi di codice (ad esempio Classi, Metodi e Proprietà) e i tipi di relazione (ad esempio Eredita da, Implementa e Chiamate).  
  
     ![Torna all'inizio &#45; grafico delle dipendenze di livello di assembly](../modeling/media/dependencygraph_toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
     Questa soluzione di esempio contiene cartelle della soluzione (**Test** e **Componenti**), progetti di test, progetti Web e assembly. Per impostazione predefinita, tutte le relazioni del contenitore vengono visualizzate come *gruppi*che è possibile espandere e comprimere. Il gruppo **Esterni** contiene qualsiasi elemento esterno alla soluzione, incluse le dipendenze della piattaforma. Gli assembly esterni mostrano solo gli elementi usati. Per impostazione predefinita, i tipi di base del sistema sono nascosti sulla mappa per evitare confusione.  
  
3.  Per eseguire il drill-down nella mappa, espandere i gruppi che rappresentano progetti e assembly. Per espandere tutti gli elementi premere **CTRL+A** per selezionare tutti i nodi e quindi scegliere **Gruppo**, **Espandi** dal menu di scelta rapida.  
  
     ![Espansione di tutti i gruppi in una mappa del codice](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4.  Tuttavia, questa operazione potrebbe non essere utile per una soluzione di grandi dimensioni. Infatti, per soluzioni complesse, i limiti di memoria potrebbero impedire di espandere tutti i gruppi. In alternativa, per visualizzare gli elementi all'interno di un singolo nodo, espanderlo. Spostare il puntatore del mouse sopra il nodo, quindi scegliere il pulsante con la freccia di espansione (freccia giù) quando viene visualizzato.  
  
     ![Espansione di un nodo in una mappa codici](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  
  
     In alternativa, usare la tastiera selezionando l'elemento e premendo il tasto più (**+**). Per esplorare i livelli più profondi di codice, effettuare la stessa operazione per gli spazi dei nomi, i tipi e i membri.  
  
    > [!TIP]
    >  Per ulteriori dettagli di utilizzo del codice mappe mediante il mouse, tastiera e il tocco, vedere [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).  
  
5.  Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, è possibile nascondere tutti i contenitori di Cartella soluzione e Assembly.  
  
     ![Semplificare la mappa filtrando i contenitori](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
     È anche possibile semplificare la mappa nascondendo o rimuovendo i singoli gruppi ed elementi dalla mappa, senza modificare il codice della soluzione sottostante.  
  
6.  Per visualizzare le relazioni tra elementi, selezionarle nella mappa. I colori dei collegamenti indicano i tipi di relazione, come mostrato nel riquadro **Legenda** .  
  
     ![Visualizzare le dipendenze nelle soluzioni](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
     In questo esempio, i collegamenti viola sono chiamate, i collegamenti punteggiati sono riferimenti e i collegamenti azzurro rappresentano l'accesso al campo. I collegamenti verdi possono essere ereditati o possono essere *collegamenti aggregati* che indicano più di un tipo di relazione (o *categoria*).  
  
    > [!TIP]
    >  Se viene visualizzato un collegamento verde, non necessariamente esiste solo una relazione di ereditarietà. Potrebbero essere presenti anche chiamate al metodo, nascoste dalla relazione di ereditarietà. Per visualizzare determinati tipi di collegamenti, utilizzare le caselle di controllo di **filtri** per i tipi che non si desidera nascondere.  
  
7.  Per altre informazioni su un elemento o un collegamento, spostare il puntatore su di esso finché non viene visualizzata una descrizione comando. In questo modo vengono mostrati i dettagli di un elemento di codice o delle categorie rappresentate da un collegamento.  
  
     ![Visualizzare le categorie di una relazione](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8.  Per esaminare gli elementi e le dipendenze rappresentate da un collegamento di aggregazione, prima selezionare il collegamento, quindi aprire il relativo menu di scelta rapida. Scegliere **Mostra collegamenti partecipanti** (o **Mostra collegamenti partecipanti sulla nuova mappa codice**). I gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento.  
  
9. Per concentrarsi su parti specifiche della mappa, è possibile continuare a rimuovere gli elementi che non si è interessati. Ad esempio, per analizzare la visualizzazione delle classi e dei membri, è sufficiente filtrare tutti i nodi dello spazio dei nomi nel riquadro **Filtri** .  
  
     ![Drill-down a livello di classe e membro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Un altro modo per concentrarsi sulla mappa di soluzione complessa consiste nel generare una nuova mappa contenente gli elementi selezionati da una mappa esistente. Tenere premuto **CTRL** durante la selezione di elementi su cui si vuole concentrarsi, aprire il menu di scelta rapida e scegliere **Nuovo grafico dalla selezione**.  
  
     ![Mostra gli elementi selezionati in una nuova mappa codice](../modeling/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. Il contesto contenitore viene trasferito alla nuova mappa. Nascondere le cartelle della soluzione e tutti gli altri contenitori che non si vuole visualizzare tramite il **filtri** riquadro.  
  
     ![Filtrare i contenitori per semplificare la visualizzazione](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Espandere i gruppi e selezionare gli elementi della mappa per visualizzare le relazioni.  
  
     ![Selezionare gli elementi da visualizzare le relazioni](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
 Vedere anche:  
  
-   [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Trovare potenziali problemi nel codice [eseguendo un analizzatore](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Visualizzare le dipendenze tra assembly o file binari  
  
1.  [Creare una mappa codice vuota](#GetStarted)o aprire una mappa codice esistente (file con estensione dgml).  
  
2.  Trascinare gli assembly o i file binari di cui eseguire il mapping dall'esterno di Visual Studio nella mappa. Ad esempio, trascinare assembly o file binari da Esplora risorse o Esplora file.  
  
> [!NOTE]
>  È possibile trascinare assembly o file binari da Esplora risorse o Esplora file solo se Esplora risorse o Esplora file e Visual Studio vengono eseguiti allo stesso livello di autorizzazione del controllo di accesso utente. Se, ad esempio, il controllo di accesso utente è attivato e si esegue Visual Studio come amministratore, Esplora risorse o Esplora file blocca l'operazione di trascinamento. Per risolvere questo problema, assicurarsi di eseguire le applicazioni allo stesso livello di autorizzazione oppure disattivare il controllo di accesso dell'utente.  
  
##  <a name="SeeSpecificSource"></a> Visualizzare dipendenze specifiche  
 Si supponga, ad esempio, di dover eseguire una revisione del codice in alcuni file con modifiche in sospeso. Per visualizzare le dipendenze in queste modifiche, è possibile creare una mappa codice da tali file.  
  
 ![Mostra dipendenze specifiche su una mappa del codice](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Visualizzare dipendenze specifiche nella soluzione  
  
1.  Aprire **Esplora soluzioni**. Selezionare i progetti, i riferimenti agli assembly, le cartelle, i file, i tipi e i membri di proprio interesse. Per trovare elementi con dipendenze da tipi o membri, aprire il menu di scelta rapida del tipo o del membro da **Esplora soluzioni**. Scegliere il tipo di dipendenza e quindi selezionare i risultati.  
  
2.  Eseguire il mapping degli elementi e dei relativi membri. Nel **Esplora** fare clic sulla barra degli strumenti **Mostra in mappa codice**![creare nuovo grafico dalla selezionato nodi pulsante](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Selezionare gli elementi che si desidera eseguire il mapping](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  La mappa visualizza gli elementi selezionati all'interno degli assembly in cui sono contenuti.  
  
     ![Gli elementi visualizzati come gruppi sulla mappa selezionati](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     È anche possibile trascinare elementi da Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti in una mappa codice nuova o esistente. Per creare una mappa vuota, vedere [Creare una mappa codice vuota](#GetStarted). Per includere la gerarchia padre per gli elementi, tenere premuto **CTRL** quando si trascinano gli elementi oppure usare il pulsante **Includi padri** nella barra degli strumenti della mappa codice per specificare l'azione predefinita.  
  
    > [!NOTE]
    >  Quando si aggiungono elementi da un progetto condiviso in più applicazioni, ad esempio Windows Phone o Windows Store, tali elementi vengono visualizzati nella mappa insieme al progetto di applicazione attivo. Se si cambia il contesto passando a un altro progetto di applicazione e si aggiungono altri elementi dal progetto condiviso, tali elementi vengono visualizzati con il nuovo progetto di applicazione attivo. Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.  
  
4.  Per esplorare gli elementi, espanderli. Spostare il puntatore del mouse sopra un elemento, quindi scegliere il pulsante con la freccia di espansione (freccia Giù) quando viene visualizzato.  
  
     ![Espansione di un nodo in una mappa codici](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  
  
     Per espandere tutti gli elementi, selezionarli usando **CTRL+A**, quindi aprire il menu di scelta rapida per la mappa e scegliere **Gruppo**, **Espandi**. Tuttavia, questa opzione non è disponibile se l'espansione di tutti i gruppi crea una mappa inutilizzabile o problemi di memoria.  
  
5.  Continuare a espandere gli elementi desiderati, fino al livello di classe e membro, se necessario.  
  
     ![Espandere i gruppi a livello di classe e membro](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Per visualizzare i membri nel codice, ma non vengono visualizzati sulla mappa, scegliere il **recupera di nuovo figli** icona ![recupera di nuovo figli icona](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") nella parte superiore angolo sinistro di un gruppo.  
  
6.  Per visualizzare più elementi correlati a quelli sulla mappa, selezionarne uno e scegliere **Mostra correlati** nella barra degli strumenti della mappa codice, quindi selezionare il tipo di elementi correlati da aggiungere alla mappa. In alternativa, selezionare uno o più elementi, aprire il menu di scelta rapida e quindi scegliere il **Mostra...**  opzione per il tipo di elementi correlati da aggiungere alla mappa. Ad esempio:  
  
     Per un **assembly**scegliere:  
  
    |||  
    |-|-|  
    |**Mostra assembly a cui fa riferimento**|Aggiungere gli assembly a cui fa riferimento questo assembly. Gli assembly esterni vengono visualizzati nel gruppo **Esterni** .|  
    |**Mostra assembly che fanno riferimento a**|Aggiungere gli assembly della soluzione che fanno riferimento a questo assembly.|  
  
     Per uno **spazio dei nomi**scegliere **Mostra assembly contenitore**, se non è visibile.  
  
     Per una **classe** o un' **interfaccia**scegliere:  
  
    |||  
    |-|-|  
    |**Mostra tipi base**|Per una classe, aggiungere la classe base e le interfacce implementate.<br /><br /> Per un'interfaccia, aggiungere le interfacce di base.|  
    |**Mostra tipi derivati**|Per una classe, aggiungere le classi derivate.<br /><br /> Per un'interfaccia, aggiungere le interfacce derivate e le classi o gli struct implementati.|  
    |**Mostra tipi a cui fa riferimento**|Aggiungere tutte le classi e i membri usati.|  
    |**Mostra tipi che fanno riferimento a**|Aggiungere tutte le classi e membri che usano la classe.|  
    |**Mostra spazio dei nomi contenitore**|Aggiungere lo spazio dei nomi del padre.|  
    |**Mostra spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|  
    |**Mostra tutti i tipi di base**|Aggiungere la gerarchia di interfacce o di classi base in modo ricorsivo.|  
    |**Mostra tutti i tipi derivati**|Per una classe, aggiungere tutte le classi derivate in modo ricorsivo.<br /><br /> Per un'interfaccia, aggiungere tutte le interfacce derivate e implementare classi o struct in modo ricorsivo.|  
  
     Per un **metodo**scegliere:  
  
    |||  
    |-|-|  
    |**Mostra metodi chiamati**|Aggiungere metodi chiamati dal metodo specifico.|  
    |**Mostra campi a cui fa riferimento**|Aggiungere i campi cui questo metodo fa riferimento.|  
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|  
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|  
    |**Mostra metodi sottoposti a override**|Per un metodo che esegue l'override di altri metodi o implementa un metodo di interfaccia, aggiungere tutti i metodi astratti o virtuali nelle classi base sottoposte a override e, se disponibile, il metodo di interfaccia implementato.|  
  
     Per un **campo** o una **proprietà**scegliere:  
  
    |||  
    |-|-|  
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|  
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|  
  
     ![Mostra metodi chiamati da questo membro](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  La mappa visualizza le relazioni. In questo esempio, i metodi chiamati dal metodo `Find` e la relativa posizione nella soluzione o esternamente.  
  
     ![Mostra dipendenze specifiche su una mappa del codice](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, disattivare la visualizzazione di Cartelle soluzione, Assembly e Spazi dei nomi.  
  
     ![Utilizzare il riquadro filtro per semplificare la visualizzazione](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> Visualizzare le dipendenze tra i file di origine e i file di intestazione C e C++  
 Per creare mappe più complete per i progetti C++, impostare l'opzione del compilatore di informazioni di visualizzazione (**/FR**) su tali progetti. In caso contrario, viene visualizzato un messaggio con la richiesta di impostare l'opzione. Se si seleziona **OK**, l'opzione viene impostata solo per la mappa corrente. È possibile scegliere di nascondere il messaggio per tutte le mappe successive. Se si nasconde il messaggio, è possibile visualizzarlo nuovamente. Impostare la seguente chiave del Registro di sistema su `0` o eliminare la chiave:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  
  
 Quando si apre una soluzione che contiene progetti Visual C++, l'aggiornamento del database di IntelliSense potrebbe richiedere del tempo. Durante questo periodo potrebbe non essere possibile creare mappe codice per file di intestazione (con estensione h o `#include`) o finché il database IntelliSense non ha completato l'aggiornamento. È possibile monitorare lo stato di avanzamento dell'aggiornamento nella barra di stato di Visual Studio. Per risolvere problemi o messaggi che vengono visualizzati perché determinate impostazioni di IntelliSense sono disattivate, vedere [Risoluzione dei problemi relativi alle mappe per il codice C e C++](#Troubleshooting).  
  
-   Per visualizzare le dipendenze tra tutti i file di origine e i file di intestazione nella soluzione, scegliere **Genera grafico dei file di inclusione** dal menu **Architettura**.  
  
     ![Grafico delle dipendenze per codice nativo](../modeling/media/dependencygraphgeneral_nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Per visualizzare le dipendenze tra i file attualmente aperti e i file di origine e i file di intestazione correlati, aprire il file di origine o il file di intestazione. Aprire il menu di scelta rapida del file in un punto qualsiasi del file. Scegliere **Genera grafico dei file di inclusione**.  
  
     ![Primo &#45; grafico delle dipendenze di livello per il file con estensione h](../modeling/media/dependencygraph_native_firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> Risoluzione dei problemi relativi alle mappe per il codice C e C++  
 Gli elementi seguenti non sono supportati nel codice C e C++:  
  
-   I tipi di base non vengono visualizzati nelle mappe che includono la gerarchia padre.  
  
-   La maggior parte delle voci di menu **Mostra** non è disponibile per il codice C e C++.  
  
 Questi problemi potrebbero verificarsi quando si creano mappe del codice per il codice C e C++:  
  
|**Problema**|**Possibile causa**|**Risoluzione**|  
|---------------|------------------------|--------------------|  
|Non è stato possibile generare la mappa codice.|Nessun progetto nella soluzione è stato compilato correttamente.|Correggere gli errori di compilazione che si sono verificati, quindi rigenerare la mappa.|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Architettura **Architettura** .|Il file di database del programma (con estensione pdb) potrebbe essere danneggiato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Ricompilare la soluzione e riprovare.|  
|Alcune impostazioni per il database di esplorazione IntelliSense sono disabilitate.|Alcune impostazioni di IntelliSense potrebbero essere disabilitate nella finestra di dialogo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**di** .|Attivare le impostazioni per abilitarle.<br /><br /> Vedere [opzioni, Editor di testo, C/C++, avanzate](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Il messaggio **Metodi sconosciuti** viene visualizzato su un nodo di metodo.<br /><br /> Questo problema si verifica perché non è possibile risolvere il nome del metodo.|Il file binario potrebbe non disporre di una tabella di rilocazione di base.|Attivare l'opzione **/FIXED:NO** nel linker.|  
||Il file di database del programma (con estensione pdb) potrebbe non essere compilato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Attivare l'opzione **/DEBUG** nel linker.|  
||Non è possibile aprire o trovare il file pdb nei percorsi previsti.|Verificare che il file pdb esista nei percorsi previsti.|  
||Le informazioni di debug sono state rimosse dal file pdb.|Se nel linker è stata usata l'opzione **/PDBSTRIPPED** , includere il file pdb completo.|  
||Il chiamante non è una funzione e non è un thunk nel file binario o un puntatore nella sezione di dati.|Quando il chiamante è un thunk, provare a usare `_declspec(dllimport)` per evitare il thunk.|  
  
##  <a name="RenderMoreQuickly"></a> Accelerare il rendering delle mappe codice  
 Quando si genera una mappa per la prima volta, Visual Studio indicizza tutte le dipendenze trovate. Questo processo potrebbe richiedere molto tempo, soprattutto per le soluzioni di grandi dimensioni, ma ciò migliorerà le prestazioni successive. Se il codice viene modificato, Visual Studio reindicizza solo il codice aggiornato. Per ridurre al minimo il tempo necessario per completare il rendering della mappa, tenere presente quanto segue:  
  
-   [Eseguire il mapping solo delle dipendenze che interessano.](#SeeSpecificSource)  
  
-   Prima di generare la mappa per un'intera soluzione, ridurre l'ambito della soluzione.  
  
-   Disattivare la compilazione automatica per la soluzione con il pulsante **Ignora compilazione** nella barra degli strumenti della mappa codice.  
  
-   Disattivare la compilazione automatica degli elementi padre con il pulsante **Includi padri** nella barra degli strumenti della mappa codice.  
  
-   Modificare il file della mappa codice per rimuovere i nodi e i collegamenti non necessari. La modifica della mappa non influisce in alcun modo sul codice sottostante. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
 ![Pulsanti Skip Build e Includi padri](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
 Sebbene Visual Studio sia in grado di funzionare con 1 GB di memoria, è consigliabile che il computer disponga di almeno 2 GB di memoria per evitare lunghi ritardi quando viene creato l'indice del codice e viene generata la mappa.  
  
 La creazione di mappe o l'aggiunta di elementi a una mappa da Esplora soluzioni potrebbe richiedere più tempo quando la proprietà **Copia nella directory di output** di un elemento di progetto è impostata su **Copia sempre**. Ciò potrebbe causare problemi nelle compilazioni incrementali e in Visual Studio per ricompilare il progetto ogni volta. Per aumentare le prestazioni, impostare questa proprietà su **Copia se più recente** o su `PreserveNewest`. Vedere [Incremental Builds](../msbuild/incremental-builds.md).  
  
 La mappa completata mostrerà le dipendenze solo per il codice compilato correttamente. Se si verificano errori di compilazione per determinati componenti, tali errori vengono visualizzati nella mappa. Assicurarsi quindi che un componente venga effettivamente compilato e contenga le dipendenze prima di prendere decisioni a livello di architettura in base alla mappa.  
  
##  <a name="SavingExporting"></a> Condividere le mappe codice  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Condividere la mappa con altri utenti di Visual Studio  
 Usare il menu **File** per salvare la mappa.  
  
 oppure  
  
 Per salvare la mappa come parte del progetto specifico, nella barra degli strumenti della mappa scegliere **Condividi**, **Sposta** \<*Nome mappa codice*>**.dgml in**, quindi scegliere il progetto in cui si vuole salvare la mappa.  
  
 ![Spostare una mappa in un altro progetto](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 In Visual Studio la mappa viene salvata come file con estensione dgml da condividere con altri utenti di Visual Studio Enterprise e Visual Studio Professional.  
  
> [!NOTE]
>  Prima di condividere una mappa con gli utenti che usano Visual Studio Professional, assicurarsi di espandere tutti i gruppi, visualizzare i nodi nascosti e i collegamenti tra gruppi e recuperare tutti i nodi eliminati che si vuole vengano visualizzati da altri nella mappa. In caso contrario, altri utenti non saranno in grado di visualizzare questi elementi.  
>   
>  Quando si salva una mappa che è contenuta in un progetto di modellazione o che è stata copiata da un progetto di modellazione in un altro percorso potrebbe verificarsi l'errore seguente:  
>   
>  "Impossibile salvare *nomeFile* all'esterno della directory del progetto. Gli elementi collegati non sono supportati."  
>   
>  In Visual Studio viene visualizzato l'errore, ma viene comunque creata la versione salvata. Per evitare l'errore, creare la mappa all'esterno del progetto di modellazione. Sarà quindi possibile salvarlo quindi nel percorso desiderato. Il semplice tentativo di copiare il file in un altro percorso della soluzione e salvarlo non produrrà alcun effetto.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Esportare la mappa come immagine in modo che sia possibile copiarla in altre applicazioni, ad esempio in Microsoft Word o PowerPoint.  
  
1.  Nella barra degli strumenti della mappa codice scegliere **Condividi**, **Invia come immagine in un messaggio di posta elettronica** o **Copia immagine**.  
  
2.  Incollare l'immagine in un'altra applicazione.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Esportare la mappa come file XPS in modo che sia possibile visualizzarla in visualizzatori XAML o XML come Internet Explorer  
  
1.  Nella barra degli strumenti della mappa codice scegliere **Condividi**, **Invia come Portable XPS in un messaggio di posta elettronica** o **Salva come Portable XPS**.  
  
2.  Scegliere la posizione in cui salvare il file.  
  
3.  Assegnare un nome alla mappa codice. Assicurarsi che il **Salva come** casella viene impostata su **file XPS (\*XPS)**. Scegliere **Salva**.  
  
## <a name="what-else-can-i-do"></a>In quale altro modo è possibile procedere?  
  
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
