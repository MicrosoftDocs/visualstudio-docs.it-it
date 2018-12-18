---
title: "Attività GenerateApplicationManifest | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 76a2fc5e184b566e0c9783f6f64beecc7ca882a2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="generateapplicationmanifest-task"></a>Attività GenerateApplicationManifest
Genera un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o un manifesto nativo. Un manifesto nativo descrive un componente definendo un'identità univoca per il componente e identificando tutti gli assembly e i file che costituiscono il componente. Un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] estende un manifesto nativo indicando il punto di ingresso dell'applicazione e specificando il livello di sicurezza dell'applicazione.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività `GenerateApplicationManifest`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Name` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, il nome viene dedotto dal parametro `EntryPoint` o `InputManifest`. Se non è possibile creare alcun nome, l'attività genera un errore.|  
|`AssemblyVersion`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Version` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, viene usato il valore predefinito "1.0.0.0".|  
|`ClrVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione minima di Common Language Runtime (CLR) richiesta dall'applicazione. Il valore predefinito è la versione di CLR usata dal sistema di compilazione. Se l'attività genera un manifesto nativo, questo parametro viene ignorato.|  
|`ConfigFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elemento che contiene il file di configurazione dell'applicazione. Se l'attività genera un manifesto nativo, questo parametro viene ignorato.|  
|`Dependencies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un elenco di elementi che definisce il set di assembly dipendenti per il manifesto generato. Ogni elemento può essere ulteriormente descritto dai metadati dell'elemento per indicare informazioni aggiuntive sullo stato della distribuzione e il tipo di dipendenza. Per altre informazioni, vedere la sezione relativa ai metadati degli elementi riportata di seguito.|  
|`Description`|Parametro `String` facoltativo.<br /><br /> Specifica la descrizione per l'applicazione o il componente.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un singolo elemento che indica il punto di ingresso per l'assembly del manifesto generato.<br /><br /> Per un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], questo parametro specifica l'assembly avviato quando si esegue l'applicazione.|  
|`ErrorReportUrl`|Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Specifica l'URL della pagina Web visualizzata nelle finestre di dialogo durante le segnalazioni di errori nelle installazioni ClickOnce.|  
|`FileAssociations`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un elenco di uno o più tipi di file associati al manifesto della distribuzione ClickOnce.<br /><br /> Le associazioni di file sono valide solo quando la destinazione è .NET Framework 3.5 o versione successiva.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> I file da includere nel manifesto. Specificare il percorso completo per ogni file.|  
|`HostInBrowser`|Parametro <xref:System.Boolean> facoltativo.<br /><br /> Se `true`, l'applicazione è ospitata in un browser (come le applicazioni Web Browser WPF).|  
|`IconFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Indica il file dell'icona dell'applicazione. L'icona dell'applicazione è espressa nel manifesto dell'applicazione generato e viene usata per il menu Start e la finestra di dialogo Installazione applicazioni. Se questo input non viene specificato, viene usata un'icona predefinita. Se l'attività genera un manifesto nativo, questo parametro viene ignorato.|  
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML di input da usare come base per il generatore del manifesto. In questo modo è possibile applicare nel manifesto di output dati strutturati, ad esempio definizioni della protezione dell'applicazione o definizioni del manifesto personalizzate. L'elemento radice del documento XML deve essere un nodo assembly nello spazio dei nomi asmv1.|  
|`IsolatedComReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i componenti COM da isolare nel manifesto generato. Questo parametro supporta la possibilità di isolare i componenti COM per la distribuzione di "COM senza registrazione". Funziona generando automaticamente un manifesto con definizioni di registrazione COM standard. Tuttavia, i componenti COM devono essere registrati nel computer di compilazione per garantire il funzionamento corretto.|  
|`ManifestType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di manifesto da generare. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Se questo parametro non è specificato, l'attività usa il valore predefinito `ClickOnce`.|  
|`MaxTargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica la lunghezza massima consentita di un percorso di file nella distribuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Se questo valore è specificato, viene verificata la lunghezza di ogni percorso di file nell'applicazione rispetto a questo limite. Per tutti gli elementi che superano il limite verrà generato un avviso di compilazione. Se questo input non è specificato o è uguale a zero, non viene eseguita alcuna verifica. Se l'attività genera un manifesto nativo, questo parametro viene ignorato.|  
|`OSVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione minima del sistema operativo richiesta dall'applicazione. Ad esempio, il valore "5.1.2600.0" indica che il sistema operativo è Windows XP. Se questo parametro viene omesso, viene usato il valore "4.10.0.0", che indica Windows 98 Second Edition, la versione minima di sistema operativo supportata per .NET Framework. Se l'attività genera un manifesto nativo, questo input viene ignorato.|  
|`OutputManifest`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il nome del file del manifesto di output generato. Se questo parametro non è specificato, il nome del file di output viene dedotto dall'identità del manifesto generato.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma di destinazione dell'applicazione. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Se questo parametro non è specificato, l'attività usa il valore predefinito `AnyCPU`.|  
|`Product`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'identità del manifesto generato. Questo nome viene usato per il collegamento nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`Publisher`|Parametro `String` facoltativo.<br /><br /> Specifica l'editore dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'utente registrato o dall'identità del manifesto generato. Questo nome viene usato per la cartella nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`RequiresMinimumFramework35SP1`|Parametro `Boolean` facoltativo.<br /><br /> Se true, l'applicazione richiede .NET Framework 3.5 SP1 o una versione più recente.|  
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Identifica le impostazioni cultura dell'applicazione e specifica il campo `Language` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non viene specificato, si presuppone che l'applicazione sia indipendente dalle impostazioni cultura.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker del framework di destinazione.|  
|`TargetFrameworkProfile`|Parametro `String` facoltativo.<br /><br /> Specifica il profilo del framework di destinazione.|  
|`TargetFrameworkSubset`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del subset di .NET Framework da usare come destinazione.|  
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione del progetto.|  
|`TrustInfoFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML che specifica la sicurezza dell'applicazione. L'elemento radice del documento XML deve essere un nodo trustInfo nello spazio dei nomi asmv2. Se l'attività genera un manifesto nativo, questo parametro viene ignorato.|  
|`UseApplicationTrust`|Parametro `Boolean` facoltativo.<br /><br /> Se true, le proprietà `Product`, `Publisher` e `SupportUrl` vengono scritte nel manifesto dell'applicazione.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco dei parametri della classe Task, vedere [Classe di base Task](../msbuild/task-base-class.md).  
  
 Per informazioni sull'uso dell'attività `GenerateDeploymentManifest`, vedere [Attività GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md).  
  
 Gli input per i file e le dipendenze possono essere ulteriormente decorati con i metadati dell'elemento per specificare informazioni aggiuntive sullo stato di ogni elemento.  
  
## <a name="item-metadata"></a>Metadati degli elementi  
  
|Nome dei metadati|Descrizione|  
|-------------------|-----------------|  
|`DependencyType`|Indica se la dipendenza è pubblicata e installata con l'applicazione o un prerequisito. Questi metadati sono validi per tutte le dipendenze, ma non vengono usati per i file. I valori disponibili per questi metadati sono:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install è il valore predefinito.|  
|`AssemblyType`|Indica se la dipendenza è un assembly gestito o nativo. Questi metadati sono validi per tutte le dipendenze, ma non vengono usati per i file. I valori disponibili per questi metadati sono:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` è il valore predefinito, che indica che il generatore del manifesto determina automaticamente il tipo di assembly.|  
|`Group`|Indica il gruppo per il download dei file aggiuntivi su richiesta. Il nome del gruppo è definito dall'applicazione e può essere qualsiasi stringa. Una stringa vuota indica che il file non fa parte di un gruppo di download, che è l'impostazione predefinita. File non inseriti in un gruppo fanno parte del download iniziale dell'applicazione. I file di un gruppo vengono scaricati solo se richiesti in modo esplicito dall'applicazione con <xref:System.Deployment.Application>.<br /><br /> Questi metadati sono validi per tutti i file in cui `IsDataFile` è `false` e tutte le dipendenze in cui `DependencyType` è `Install`.|  
|`TargetPath`|Specifica il modo in cui il percorso deve essere definito nel manifesto generato. Questo attributo è valido per tutti i file. Se questo attributo non viene specificato, viene usata la specifica dell'elemento, Questo attributo è valido per tutti i file e le dipendenze con un valore `DependencyType` pari a `Install`.|  
|`IsDataFile`|Valore di metadati `Boolean` che indica se il file è o non è un file di dati. Un file di dati è speciale poiché viene migrato tra gli aggiornamenti dell'applicazione. Questi metadati sono validi solo per i file. `False` è il valore predefinito.|  
  
## <a name="example"></a>Esempio  
 In questo esempio si usa l'attività `GenerateApplicationManifest` per generare un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e l'attività `GenerateDeploymentManifest` per generare un manifesto di distribuzione per un'applicazione con un singolo assembly. Viene quindi usata l'attività `SignFile` per firmare i manifesti.  
  
 L'esempio illustra lo scenario di generazione del manifesto più semplice possibile, in cui i manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono generati per un singolo programma. Un nome e un'identità predefiniti vengono dedotti dall'assembly per il manifesto.  
  
> [!NOTE]
>  Nell'esempio seguente tutti i file binari dell'applicazione sono precompilati in modo che sia possibile concentrarsi sugli aspetti della generazione del manifesto. L'esempio produce una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per altre informazioni sulla proprietà `Thumbprint` usata nell'attività `SignFile` in questo esempio, vedere l'[attività SignFile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono usate le attività `GenerateApplicationManifest` e `GenerateDeploymentManifest` per generare i manifesti dell'applicazione e della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per un'applicazione con un singolo assembly, specificando nome e identità dei manifesti.  
  
 Questo esempio è simile all'esempio precedente, ma il nome e l'identità dei manifesti vengono specificati in modo esplicito. Inoltre, questo esempio è configurato come applicazione online, anziché come applicazione installata.  
  
> [!NOTE]
>  Nell'esempio seguente tutti i file binari dell'applicazione sono precompilati in modo che sia possibile concentrarsi sugli aspetti della generazione del manifesto. L'esempio produce una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per altre informazioni sulla proprietà `Thumbprint` usata nell'attività `SignFile` in questo esempio, vedere l'[attività SignFile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono usate le attività `GenerateApplicationManifest` e `GenerateDeploymentManifest` per generare i manifesti dell'applicazione e della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per un'applicazione con più file e assembly.  
  
> [!NOTE]
>  Nell'esempio seguente tutti i file binari dell'applicazione sono precompilati in modo che sia possibile concentrarsi sugli aspetti della generazione del manifesto. L'esempio produce una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per altre informazioni sulla proprietà `Thumbprint` usata nell'attività `SignFile` in questo esempio, vedere l'[attività SignFile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene usata l'attività `GenerateApplicationManifest` per generare un manifesto nativo per l'applicazione Test.exe, facendo riferimento al componente nativo Alpha.dll e al componente COM isolato Bravo.dll.  
  
 L'esempio produce il manifesto Test.exe, che rende l'applicazione XCOPY distribuibile sfruttando COM senza registrazione.  
  
> [!NOTE]
>  Nell'esempio seguente tutti i file binari dell'applicazione sono precompilati in modo che sia possibile concentrarsi sugli aspetti della generazione del manifesto. L'esempio produce una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)   
 [Attività SignFile](../msbuild/signfile-task.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)