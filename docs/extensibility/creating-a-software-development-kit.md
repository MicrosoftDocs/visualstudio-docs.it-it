---
title: Creazione di un Software Development Kit | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55b62ac0ac448023793f511389146ebb1b07da0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-software-development-kit"></a>Creazione di un Software Development Kit
Un software development kit (SDK) è una raccolta di API che è possibile fare riferimento come un singolo elemento in Visual Studio. Il **gestione riferimenti** la finestra di dialogo sono elencati tutti gli SDK che sono rilevanti per il progetto. Quando si aggiunge un SDK a un progetto, le API disponibili in Visual Studio.  
  
 Esistono due tipi di SDK:  
  
-   Platform SDK sono componenti obbligatori per lo sviluppo di App per una piattaforma. Ad esempio, il [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK è necessario per sviluppare [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.  
  
-   SDK di estensione sono componenti facoltativi che estendono un tipo di piattaforma, ma non sono obbligatori per lo sviluppo di App per la piattaforma.  
  
 Le sezioni seguenti descrivono l'infrastruttura generale di SDK e come creare un SDK della piattaforma e SDK di estensione.  
  
-   [SDK di piattaforma](#PlatformSDKs)  
  
-   [SDK di estensione](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> SDK di piattaforma  
 SDK di piattaforma sono necessari per sviluppare App per una piattaforma. Ad esempio, il [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK è necessario per sviluppare App per [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Installazione  
 Verrà installato tutti platform SDK al SDK HKLM\Software\Microsoft\Microsoft\\\v [TPI] [TPV]\\ @InstallationFolder = [radice SDK]. Di conseguenza, il [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK viene installato in HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Layout  
 SDK di piattaforma sarà necessario lo schema seguente:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Nodo|Descrizione|  
|----------|-----------------|  
|Cartella dei riferimenti|Contiene i file binari che contengono le API che possono essere codificate in. Questi possono includere i file di metadati di Windows (WinMD) o assembly.|  
|Cartella DesignTime|Contiene i file sono necessari solo in fase di pre-run e il debug. Questi può includere documenti XML, librerie, intestazioni, i file binari in fase di progettazione della casella degli strumenti, gli elementi di MSBuild e così via<br /><br /> Documenti XML in teoria, sarebbe, essere inseriti nella cartella \DesignTime, ma i documenti XML per i riferimenti continueranno a essere inseriti accanto ai file di riferimento in Visual Studio. Ad esempio, il documento XML per un riferimento di \References\\[config]\\[arch]\sample.dll sarà \References\\[config]\\[arch]\sample.xml e la versione localizzata di tale documento saranno \References\\[config]\\[arch]\\[locale]\sample.xml.|  
|Cartella di configurazione|Può esistere solo tre cartelle: debug, vendita al dettaglio e CommonConfiguration. Se lo stesso set di file del SDK deve essere utilizzato, indipendentemente dalla configurazione destinati al consumer SDK, è possono distribuire i file sotto CommonConfiguration gli autori SDK.|  
|Cartella di architettura|Può esistere qualsiasi cartella dell'architettura supportata. Visual Studio supporta le architetture seguenti: x86, x64, ARM e neutral. Nota: Win32 esegue il mapping a x86 e AnyCPU esegue il mapping a neutro.<br /><br /> MSBuild esegue la ricerca solo in \CommonConfiguration\neutral di Platform SDK.|  
|SDKManifest.xml|Questo file viene descritto come Visual Studio devono utilizzare il SDK. Esaminare il manifesto SDK per [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** il valore che consente di visualizzare il Visualizzatore oggetti nell'elenco di ricerca.<br /><br /> **PlatformIdentity:** l'esistenza di questo attributo indica a Visual Studio e MSBuild che il SDK è un SDK della piattaforma e che i riferimenti aggiunti da quest'ultimo non devono essere copiati in locale.<br /><br /> **TargetFramework:** questo attributo viene utilizzato da Visual Studio per garantire che solo progetti destinati a stessi Framework come specificato nel valore di questo attributo può utilizzare il SDK.<br /><br /> **MinVSVersion:** questo attributo viene utilizzato da Visual Studio per utilizzare solo gli SDK che si applicano a esso.<br /><br /> **Riferimento:** questo attributo deve essere specificato per solo i riferimenti che contengono i controlli. Per informazioni su come specificare se un riferimento contiene controlli, vedere di seguito.|  
  
##  <a name="ExtensionSDKs"></a> SDK di estensione  
 Le sezioni seguenti descrivono ciò che è necessario eseguire per distribuire un SDK di estensione.  
  
### <a name="installation"></a>Installazione  
 SDK di estensione possono essere installati per un utente specifico o per tutti gli utenti senza specificare una chiave del Registro di sistema. Per installare un SDK per tutti gli utenti, utilizzare il seguente percorso:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Per un'installazione specifiche dell'utente, utilizzare il seguente percorso:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Se si desidera utilizzare un percorso diverso, è necessario eseguire una delle seguenti operazioni:  
  
1.  Specificare, in una chiave del Registro di sistema:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     e aggiungere una sottochiave (impostazione predefinita) che ha un valore di `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Aggiungere la proprietà MSBuild `SDKReferenceDirectoryRoot` al file di progetto. Il valore di questa proprietà è un elenco delimitato da punti semi di directory in cui risiede il SDK di estensione si desidera fare riferimento.  
  
### <a name="installation-layout"></a>Layout di installazione  
 SDK di estensione hanno il layout di installazione seguenti:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< Nomesdk\>\\< SDKVersion\>: il nome e la versione dell'estensione SDK è derivato dai nomi di cartella corrispondente nel percorso radice SDK. MSBuild Usa questa identità per trovare il SDK sul disco e Visual Studio visualizza questa identità nel **proprietà** finestra e **gestione riferimenti** finestra di dialogo.  
  
2.  Cartella Riferimenti: i file binari che contengono le API. Può trattarsi di file di metadati di Windows (WinMD) o assembly.  
  
3.  Cartella Redist: i file necessari per la fase di esecuzione e il debug e devono ottenere incluso come parte dell'applicazione dell'utente. Tutti i file binari devono essere inseriti sotto \redist\\< configurazione\>\\< arch\>, e i nomi binari devono avere il formato seguente per garantire l'univocità:  **\<società >.\< prodotto >. \<scopo >. \<estensione >**. Ad esempio: Microsoft.Cpp.Build.dll. Tutti i file con nomi che che siano in conflitto con nomi di file da altri SDK (ad esempio, i file jpg, png, xaml, pri, css e javascript) devono essere inseriti sotto \redist\\< configurazione\>\\< arch\> \\< nomesdk\>\ tranne i file che sono associati a XAML controlla. Questi file devono essere posizionati sotto \redist\\< configurazione\>\\< arch\>\\< componentname\>\\.  
  
4.  La cartella DesignTime: i file che sono necessari solo pre-run e il debug di tempo e non deve essere incluso come parte dell'applicazione dell'utente. Può trattarsi di documenti XML, librerie, intestazioni, i file binari in fase di progettazione della casella degli strumenti, gli elementi di MSBuild e così via. Qualsiasi SDK che è destinato all'utilizzo da parte di un progetto nativo deve avere un *Nomesdk*file con estensione props. Di seguito viene illustrato un esempio di questo tipo di file.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Documenti di riferimento XML vengono inseriti accanto ai file di riferimento. Ad esempio, il documento di riferimento XML per il **\References\\< configurazione\>\\< arch\>\sample.dll** assembly **\References\\ < configurazione\>\\< arch\>\sample.xml**, e la versione localizzata di tale documento **\References\\< configurazione\>\\< arch\>\\< impostazioni locali\>\sample.xml**.  
  
5.  Cartella di configurazione: tre sottocartelle: Debug, vendita al dettaglio e CommonConfiguration. Gli autori SDK è possono posizionare i file sotto CommonConfiguration quando lo stesso set di file del SDK deve essere utilizzato, indipendentemente dalla configurazione di destinazione da parte del consumer SDK.  
  
6.  Cartella architettura: le architetture seguenti sono supportate: x86, x64, ARM, neutral. Esegue il mapping di Win32 per x86 e AnyCPU esegue il mapping a neutro.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Questo file viene descritto come Visual Studio devono utilizzare il SDK. Di seguito è riportato un esempio.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Di seguito sono riportati gli elementi del file.  
  
1.  DisplayName: il valore visualizzato in Gestione riferimenti, Esplora soluzioni, Visualizzatore oggetti e altre posizioni nell'interfaccia utente per Visual Studio.  
  
2.  ProductFamilyName: Complessiva SDK nome prodotto. Ad esempio, il [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK denominato "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", che appartengono alla stessa famiglia della famiglia di prodotti SDK, "Winjs". Questo attributo consente a Visual Studio e MSBuild per rendere possibile la connessione. Se questo attributo non esiste, il nome del SDK viene utilizzato come nome di famiglia del prodotto.  
  
3.  FrameworkIdentity: specifica una dipendenza da uno o più librerie dei componenti Windows che il valore di questo attributo viene inserito nel manifesto dell'applicazione consumer. Questo attributo è applicabile solo per le librerie dei componenti di Windows.  
  
4.  TargetFramework: specifica gli SDK che sono disponibili in Gestione riferimenti e casella degli strumenti. Questo è un elenco delimitato da punto e virgola di moniker framework di destinazione, ad esempio ".NET Framework, version = v 2.0; .NET Framework, version = v 4.5.1". Se vengono specificate più versioni dello stesso framework di destinazione, gestione riferimenti Usa la versione minima specificata per l'applicazione di filtri. Ad esempio, se ".NET Framework, versione = v 2.0; .NET Framework, version = v 4.5.1" viene specificato, verrà utilizzato Gestione riferimenti ".NET Framework, versione = v 2.0". Se viene specificato un profilo del framework di destinazione specifica, solo tale profilo verrà utilizzato da Gestione riferimenti a scopo di filtro. Ad esempio, quando "Silverlight, versione = v 4.0, profile = WindowsPhone" viene specificato, gestione riferimenti filtri sulle solo il profilo di Windows Phone. un progetto destinato a Silverlight 4.0 Framework completo non consente di visualizzare il SDK in Gestione riferimenti.  
  
5.  MinVSVersion: Visual Studio versione minima.  
  
6.  MaxPlatformVerson: La versione della piattaforma di destinazione massimo deve essere utilizzata per specificare le versioni di piattaforma in cui il SDK di estensione non funzionerà. Ad esempio, di Microsoft Visual C++ Runtime Package v 11.0 deve fare riferimento solo progetti Windows 8. Pertanto, MaxPlatformVersion del progetto di Windows 8 è 8.0. Ciò significa che la gestione di riferimenti esclude Microsoft Visual C++ Runtime Package per un progetto Windows 8.1 e MSBuild genera un errore quando un [!INCLUDE[win81](../debugger/includes/win81_md.md)] progetto fa riferimento a essa. Nota: questo elemento è supportato a partire da [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: specifica gli SDK che sono disponibili in Gestione riferimenti specificando i tipi di progetto di Visual Studio applicabili. Nove valori riconosciuti: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, gestito e nativo. Può usare l'autore del SDK e ("+"), o ("&#124;"), non ("!") operatori per specificare esattamente l'ambito dei tipi di progetto che si applicano al SDK.  
  
     WindowsAppContainer identifica i progetti per [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.  
  
8.  SupportPrefer32Bit: I valori supportati sono "True" e "False". Il valore predefinito è "True". Se il valore è impostato su "False", MSBuild restituisce un errore per [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] progetti (o un avviso per i progetti desktop) se il progetto che fa riferimento a SDK Prefer32Bit abilitato. Per ulteriori informazioni su Prefer32Bit, vedere [pagina compilazione, Progettazione progetti (c#)](../ide/reference/build-page-project-designer-csharp.md) o [pagina Compila, Progettazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: elenco di architetture supportate dal SDK delimitato da punti e virgola. MSBuild viene visualizzato un avviso se non è supportata l'architettura del progetto dispendiosa in termini di SDK di destinazione. Se questo attributo non è specificato, questo tipo di avviso viene visualizzato in MSBuild mai.  
  
10. SupportsMultipleVersions: se questo attributo è impostato su **errore** o **avviso**, MSBuild indica che nello stesso progetto non può fare riferimento a più versioni della stessa famiglia SDK. Se questo attributo non esiste o è impostato su **Consenti**, MSBuild non visualizzare questo tipo di errore o avviso.  
  
11. AppX: Specifica il percorso per i pacchetti di app per la raccolta di componenti di Windows sul disco. Questo valore viene passato al componente di registrazione della libreria di componenti di Windows durante il debug locale. La convenzione di denominazione per il nome del file è  **\<società >.\< Prodotto >. \<Architettura >. \<Configurazione >. \<Versione > AppX**. Configurazione e architettura sono facoltativi il nome di attributo e il valore dell'attributo, se non si applicano alla libreria di componenti di Windows. Questo valore è applicabile solo per le librerie dei componenti di Windows.  
  
12. CopyRedistToSubDirectory: specifica la copia in cui i file nella cartella \redist relativo alla radice del pacchetto dell'app (vale a dire il **posizione pacchetto** scelto nella procedura guidata Crea pacchetto dell'applicazione) e runtime layout radice. Il percorso predefinito è la radice del pacchetto dell'app e layout F5.  
  
13. DependsOn: Un elenco di identità SDK che definiscono gli SDK da cui dipende questo SDK. Questo attributo viene visualizzato nel riquadro dei dettagli di gestione riferimenti.  
  
14. MoreInfo: l'URL alla pagina web che fornisce la Guida e altre informazioni. Questo valore viene utilizzato nel collegamento informazioni nel riquadro destro di gestione riferimenti.  
  
15. Tipo di registrazione: specifica la registrazione WinMD nel manifesto dell'applicazione ed è necessario per WinMD nativo, che dispone di una DLL di implementazione corrispondente.  
  
16. Riferimento al file: specificare per solo tali riferimenti contengono controlli o i file Winmd nativo. Per informazioni su come specificare se un riferimento contiene controlli, vedere [specificando il percorso di elementi della casella degli strumenti](#ToolboxItems) sotto.  
  
##  <a name="ToolboxItems"></a> Specifica la posizione degli elementi della casella degli strumenti  
 L'elemento ToolBoxItems dello schema SDKManifest.xml specifica la categoria e la posizione degli elementi della casella degli strumenti della piattaforma sia gli SDK di estensione. Nell'esempio seguente viene illustrato come specificare percorsi diversi. Questa opzione è disponibile per i riferimenti WinMD o DLL.  
  
1.  Inserire controlli nella categoria della casella degli strumenti predefinita.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Inserire i controlli in un determinato nome di categoria.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Inserire i controlli in nomi di categoria.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Inserire i controlli in nomi di categoria diversa in Visual Studio e Blend.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Consente di enumerare i controlli specifici in modo diverso in Visual Studio e Blend.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerare i controlli specifici e posizionarli nel percorso comune di Visual Studio o solo nel gruppo tutti i controlli.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Controlli specifici di enumerare e visualizzare solo un set specifico in ChooseItems senza di essi nella casella degli strumenti.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK tramite C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)