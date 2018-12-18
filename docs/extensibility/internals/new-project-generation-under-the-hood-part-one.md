---
title: 'Nuova generazione del progetto: Dietro le quinte, parte 1 | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 158340ad82829338bb39709573ce9e025332341a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nuova generazione del progetto: Dietro le quinte, parte 1
Mai pensato di come creare un tipo di progetto? Chiedere a ciò che effettivamente si verifica quando si crea un nuovo progetto? Si analizzerà dietro le quinte e vedere cosa accade veramente in.  
  
 Esistono diverse attività che coordina Visual Studio per l'utente:  
  
-   Visualizza una struttura ad albero di tutti i tipi di progetto disponibili.  
  
-   Visualizza un elenco di modelli di applicazione per ogni tipo di progetto e consente la selezione di uno.  
  
-   Raccoglie informazioni di progetto per l'applicazione, ad esempio nome del progetto e il percorso.  
  
-   Passa le informazioni per la factory del progetto.  
  
-   Genera gli elementi di progetto e le cartelle nella soluzione corrente.  
  
## <a name="the-new-project-dialog-box"></a>La finestra di dialogo Nuovo progetto  
 Tutto ha inizio quando si seleziona un tipo di progetto per un nuovo progetto. Per iniziare, fare clic su **nuovo progetto** sul **File** menu. Il **nuovo progetto** viene visualizzata la finestra di dialogo, esaminando un codice simile al seguente:  
  
 ![Finestra di dialogo Nuovo progetto](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Diamo un'occhiata più vicino. Il **tipi di progetto** albero sono elencati i vari tipi di progetto è possibile creare. Quando si seleziona un tipo di progetto come **Windows Visual c#**, verrà visualizzato un elenco dei modelli di applicazione per iniziare. **Modelli di Visual Studio installati** vengono installati da Visual Studio e sono disponibili per tutti gli utenti del computer. È possibile aggiungere nuovi modelli che si crea o raccogliere per **modelli** e sono disponibili solo all'utente.  
  
 Quando si seleziona un modello di **applicazione Windows**, una descrizione del tipo di applicazione viene visualizzata nella finestra di dialogo, in questo caso, **un progetto per la creazione di un'applicazione con un'interfaccia utente di Windows**.  
  
 In fondo il **nuovo progetto** la finestra di dialogo, si noterà diversi controlli che consentono di raccogliere ulteriori informazioni. I controlli visualizzati dipendono dal tipo di progetto, ma in genere includono un progetto **nome** casella di testo, un **percorso** casella di testo ed elementi correlati **Sfoglia** pulsante e una **Nome soluzione** casella di testo ed elementi correlati **Crea directory per soluzione** casella di controllo.  
  
## <a name="populating-the-new-project-dialog-box"></a>La finestra di dialogo Nuovo progetto di compilazione  
 In cui does il **nuovo progetto** la finestra di dialogo ottenere le informazioni da? Sono disponibili due meccanismi al lavoro in questo caso, uno di essi è deprecato. Il **nuovo progetto** la finestra di dialogo combina e visualizza le informazioni ottenute da entrambi i meccanismi.  
  
 Il metodo precedente (obsoleto) utilizza le voci del Registro di sistema e i file VSDIR. Questo meccanismo viene eseguito all'apertura di Visual Studio. Il metodo più recente Usa file. vstemplate. Questo meccanismo viene eseguito quando viene inizializzato Visual Studio, ad esempio, tramite l'esecuzione  
  
```  
devenv /setup  
```  
  
 oppure  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Tipi di progetto  
 La posizione e i nomi del **tipi di progetto** radice nodi, ad esempio **Visual c#** e **altri linguaggi**, viene determinato dalle voci di registro di sistema. L'organizzazione dei nodi figlio, ad esempio **Database** e **Smart Device**, rispecchia la gerarchia delle cartelle che contengono i file con estensione vstemplate corrispondente. Esaminiamo i nodi radice prima.  
  
#### <a name="project-type-root-nodes"></a>Nodi radice di tipo di progetto  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è inizializzato, attraversa le sottochiavi della chiave del Registro di sistema del sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs per compilare e assegnare i nodi radice di un nome di **tipidiprogetto** struttura ad albero. Queste informazioni sono memorizzato nella cache per un uso successivo. Esaminare il TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC il} \\ /1 chiave. Ogni voce è un GUID di VSPackage. Il nome della sottochiave (/ 1) viene ignorato, ma la sua presenza indica che si tratta di un **tipi di progetto** nodo radice. Un nodo radice potrebbe essere a sua volta sottochiavi diverse che consentono di controllare l'aspetto nel **tipi di progetto** struttura ad albero. Esaminiamo alcuni di essi.  
  
##### <a name="default"></a>(Predefinito)  
 Questo è l'ID risorsa della stringa localizzata che i nomi del nodo radice. La risorsa di stringa si trova nella DLL selezionata dal GUID VSPackage satellite.  
  
 Nell'esempio, è il GUID VSPackage  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC IL}  
  
 e l'ID di risorsa (valore predefinito) del nodo radice (/ 1) è &#2345;  
  
 Se si esamina la sottochiave SatelliteDll cercare il GUID della chiave di pacchetti nelle vicinanze, è possibile trovare il percorso dell'assembly che contiene la stringa di risorsa:  
  
 \<Percorso di installazione di Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Per verificarlo, aprire Esplora File e trascinare csprojui.dll nella directory di Visual Studio. Tabella di stringhe viene illustrato che risorse &#2345; contiene la didascalia **Visual c#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Determina la posizione del nodo radice di **tipi di progetto** struttura ad albero.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Minore è il numero di priorità, maggiore è la posizione nell'albero.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Se questa sottochiave è presente, la posizione del nodo radice è controllata nella finestra di dialogo Impostazioni per sviluppatori. Ad esempio,  
  
 REG_SZ DeveloperActivity VC #  
  
 indica che in Visual c# è un nodo radice se Visual Studio è impostato per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] lo sviluppo. In caso contrario, sarà un nodo figlio del **altri linguaggi**.  
  
##### <a name="folder"></a>Cartella  
 Se questa sottochiave è presente, il nodo radice diventa quindi un nodo figlio della cartella specificata. Viene visualizzato un elenco di possibili cartelle sotto la chiave  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Ad esempio, la voce di progetti di Database ha una chiave di cartella corrispondente alla voce di altri tipi di progetto in PseudoFolders. In questo caso, nel **tipi di progetto** albero **progetti di Database** sarà un nodo figlio del **altri tipi di progetto**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>I nodi figlio di tipo di progetto e i file vstdir  
 La posizione dei nodi figlio di **tipi di progetto** albero segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per i modelli di macchina (**Modelli Visual Studio installati**), il normale percorso è \Programmi\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ e per i modelli utente (**modelli**), trova Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Le gerarchie di cartelle da queste due posizioni vengono unite per creare il **tipi di progetto** struttura ad albero.  
  
 Per Visual Studio con c# le impostazioni di sviluppo, la **tipi di progetto** struttura è simile alla seguente:  
  
 ![Tipi di progetto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 La cartella ProjectTemplates corrispondente è simile al seguente:  
  
 ![Modelli di progetto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Quando il **nuovo progetto** verrà visualizzata la finestra di dialogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attraversa la cartella ProjectTemplates e ricrea la struttura di **tipi di progetto** struttura ad albero con alcune modifiche:  
  
-   Il nodo radice di **tipi di progetto** albero è determinata dal modello di applicazione.  
  
-   Il nome del nodo può essere localizzato e può contenere caratteri speciali.  
  
-   Il tipo di ordinamento può essere modificato.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Individuare il nodo radice per un tipo di progetto  
 Quando Visual Studio consente di scorrere le cartelle ProjectTemplates, apre tutti i file ZIP ed estrae i file con estensione vstemplate. Un file con estensione vstemplate Usa XML per descrivere un modello di applicazione. Per ulteriori informazioni, vedere [nuova generazione progetto: in parte integrante, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Il \<ProjectType > tag determina il tipo di progetto per l'applicazione. Ad esempio, il file di \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contiene un file EmptyProject.vstemplate con questo tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Il \<ProjectType > tag e non la sottocartella della cartella ProjectTemplates, determina il nodo radice di un'applicazione nel **tipi di progetto** struttura ad albero. Nell'esempio, le applicazioni di Windows CE appariranno sotto la **Visual c#** nodo radice, e anche se fosse necessario spostare la cartella WindowsCE nella cartella di Visual Basic, le applicazioni di Windows CE ancora appariranno sotto la  **Visual c#** nodo radice.  
  
##### <a name="localizing-the-node-name"></a>Il nome del nodo di localizzazione  
 Quando Visual Studio consente di scorrere le cartelle ProjectTemplates, esamina tutti i file vstdir che trova. Un file vstdir è un file XML che controlla l'aspetto del tipo di progetto nel **nuovo progetto** la finestra di dialogo. Nel file vstdir, utilizzare il \<LocalizedName > tag al nome di **tipi di progetto** nodo.  
  
 Ad esempio, il file \CSharp\Database\TemplateIndex.vstdir contiene questo tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Consente di determinare l'ID di risorse e DLL satellite della stringa localizzata che i nomi del nodo radice, in questo caso, **Database**. Il nome localizzato può contenere caratteri speciali che non sono disponibili per i nomi di cartella, ad esempio **.NET**.  
  
 Se non \<LocalizedName > tag è presente, il tipo di progetto denominato dalla cartella stessa, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Ricerca l'ordinamento per un tipo di progetto  
 Per determinare l'ordinamento del tipo di progetto, utilizzano il file vstdir il \<SortOrder > tag.  
  
 Ad esempio, il file \CSharp\Windows\Windows.vstdir contiene questo tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Il file \CSharp\Database\TemplateIndex.vstdir contiene un tag con un valore maggiore:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Numero più basso nel \<SortOrder > tag, maggiore è la posizione nell'albero della pertanto la **Windows** nodo viene visualizzato superiore il **Database** nodo il **tipi di progetto**  struttura ad albero.  
  
 Se non \<SortOrder > tag è specificato per un tipo di progetto, viene visualizzato in ordine alfabetico seguente qualsiasi tipo di progetto contenenti \<SortOrder > specifiche.  
  
 Si noti che non sono presenti file vstdir nella cartella documenti (**modelli**) cartelle. Nomi dei tipi di progetto applicazione di utente non sono localizzati e vengono visualizzati in ordine alfabetico.  
  
#### <a name="a-quick-review"></a>Un'analisi veloce  
 È opportuno modificare il **nuovo progetto** finestra di dialogo e creare un nuovo modello di progetto utente.  
  
1.  Aggiungere una sottocartella del nodo progetto personalizzato alla cartella \Programmi\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.  
  
2.  Creare un file MyProject.vstdir nella cartella nodo progetto personalizzato utilizzando un editor di testo.  
  
3.  Aggiungere le righe del file vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Salvare e chiudere il file vstdir.  
  
5.  Creare un file MyProject.vstemplate nella cartella nodo progetto personalizzato utilizzando un editor di testo.  
  
6.  Aggiungere le righe del file. vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Salvare il file the.vstemplate e chiudere l'editor.  
  
8.  Inviare il file con estensione vstemplate per una nuova cartella MyProjectNode\MyProject.zip compressa.  
  
9. Nella finestra di comando di Visual Studio, digitare:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Aprire Visual Studio.  
  
1.  Aprire il **nuovo progetto** finestra di dialogo casella ed espandere il **Visual c#** nodo del progetto.  
  
 ![Nodo progetto personalizzato](../../extensibility/internals/media/myprojectnode.png "nodo progetto personalizzato")  
  
 **Nodo progetto personalizzato** viene visualizzato come nodo figlio di Visual c# sotto il nodo di Windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di un nuovo progetto: dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)