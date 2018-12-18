---
title: "Supporto per la proprietà di configurazione e di progetto | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e31f4feda55469d2740b32b0eac5d9cfba286d0c
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="support-for-project-and-configuration-properties"></a>Supporto per la proprietà di configurazione e di progetto
Il **proprietà** finestra il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) può visualizzare le proprietà di progetto e la configurazione. È possibile fornire una pagina delle proprietà per un tipo di progetto in modo che l'utente può impostare le proprietà dell'applicazione.  
  
 Se si seleziona un nodo del progetto in **Esplora** e quindi fare clic su **proprietà** nel **progetto** menu, è possibile aprire una finestra di dialogo che include progetti e la configurazione proprietà. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]e tipi derivati da questi linguaggi, questa finestra di dialogo viene visualizzato come una pagina a schede nel progetto di [generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per ulteriori informazioni, vedere [non incluso nella Build: procedura dettagliata: esposizione di progetto e proprietà di configurazione (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Il Framework di pacchetto gestito per i progetti (MPFProj) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e codice in [MPF per i progetti di Visual Studio 2013 -](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistenza del progetto e proprietà di configurazione  
 Proprietà progetto e di configurazione sono persistenti in un file di progetto con qualsiasi estensione di file associato al tipo di progetto, ad esempio, con estensione csproj, vbproj e .myproj. In genere, i progetti di utilizzano un file di modello per generare il file di progetto. Tuttavia, esistono effettivamente diversi modi per associare tipi di progetto e modelli. Per ulteriori informazioni, vedere [descrizione del modello di Directory (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Proprietà progetto e di configurazione vengono create aggiungendo elementi al file del modello. Queste proprietà sono quindi disponibili per qualsiasi progetto creato utilizzando il tipo di progetto che utilizza il modello. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]progetti e il MPFProj utilizzano entrambi la [non incluso nella Build: Cenni preliminari su MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) schema per i file di modello. Tali file hanno una sezione PropertyGroup per ogni configurazione. In genere, le proprietà dei progetti sono persistenti nella prima sezione PropertyGroup, che dispone di un argomento Configuration impostato su una stringa null.  
  
 Il codice seguente mostra l'inizio di un file di progetto MSBuild base.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 In questo file di progetto, `<Name>` e `<SchemaVersion>` sono proprietà del progetto e `<Optimize>` è una proprietà di configurazione.  
  
 È responsabilità del progetto per rendere persistenti le proprietà di progetto e la configurazione del file di progetto.  
  
> [!NOTE]
>  Un progetto può ottimizzare la persistenza persistenti solo valori di proprietà diversi rispetto ai valori predefiniti.  
  
## <a name="support-for-project-and-configuration-properties"></a>Supporto per la proprietà di configurazione e di progetto  
 Il `Microsoft.VisualStudio.Package.SettingsPage` implementa pagine delle proprietà di progetto e la configurazione. L'implementazione predefinita di `SettingsPage` offre proprietà pubbliche per un utente in una griglia delle proprietà generiche. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriata.  
  
 Il `SettingsPage` classe e `Microsoft.VisualStudio.Package.ProjectNode` classe offrono questi metodi per rendere persistenti le proprietà di progetto e la configurazione:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` rendere persistenti le proprietà del progetto.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rendere persistenti le proprietà di configurazione.  
  
    > [!NOTE]
    >  Le implementazioni del `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` classi Usa la `Microsoft.Build.BuildEngine` metodi (MSBuild) per ottenere e impostare le proprietà di progetto e la configurazione dal file di progetto.  
  
 La classe di derivazione `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` per rendere persistenti le proprietà di configurazione di progetto o del file di progetto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e il percorso del Registro di sistema  
 Le classi derivate da `SettingsPage` sono progettati per essere condivisi tra pacchetti VSPackage. Per rendere possibile per un pacchetto VSPackage creare una classe derivata da `SettingsPage`, aggiungere un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` per una classe derivata da `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Il pacchetto VSPackage a cui è associato l'attributo non è rilevante. Quando un pacchetto VSPackage è registrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], viene registrato l'id di classe (CLSID) di qualsiasi oggetto che può essere creato in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possibile crearlo.  
  
 Il percorso del Registro di sistema di un oggetto che può essere creato è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola CLSID e il guid del tipo di oggetto. Se `MyProjectPropertyPage` classe dispone di un guid di {3c693da2-5bca-49b3-bd95-ffe0a39dd723} e il UserRegistryRoot è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, quindi il percorso del Registro di sistema dovrebbe essere HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Layout e un progetto e gli attributi delle proprietà di configurazione  
 Il <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, e <xref:System.ComponentModel.DescriptionAttribute> gli attributi determinano il layout, l'assegnazione di etichette e la descrizione di proprietà di progetto e di configurazione in una pagina delle proprietà generiche. Questi attributi determinare la categoria, nome visualizzato e la descrizione dell'opzione, rispettivamente.  
  
> [!NOTE]
>  Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzare le risorse stringa per la localizzazione e sono definiti in [MPF per i progetti di Visual Studio 2013 -](http://mpfproj12.codeplex.com/).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Il `MyConfigProp` proprietà di configurazione viene visualizzata nella pagina delle proprietà di configurazione come **personali di proprietà di configurazione** nella categoria **categoria My**. Se l'opzione è selezionata, la descrizione, **My Description**, viene visualizzato nel riquadro Descrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta e rimozione di proprietà (pagine)](../../extensibility/adding-and-removing-property-pages.md)   
 [Progetti](../../extensibility/internals/projects.md)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
