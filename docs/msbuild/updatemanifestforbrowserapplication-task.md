---
title: "Attività UpdateManifestForBrowserApplication | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fcc1c9fe8b28b2055c73cad626cc02ef8a56aa98
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="updatemanifestforbrowserapplication-task"></a>Attività UpdateManifestForBrowserApplication
L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita per aggiungere l'elemento **\<hostInBrowser />** al manifesto dell'applicazione (*nomeprogetto*.exe.manifest) quando viene compilato un progetto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationManifest`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file manifesto dell'applicazione a cui si desidera aggiungere l'elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Parametro **Boolean** obbligatorio.<br /><br /> Specifica se modificare il manifesto dell'applicazione per includere l'elemento **\<hostInBrowser />**. Se **true**, un nuovo elemento `<`**hostInBrowser />** viene incluso nell'elemento **\<entryPoint />**. Si noti che l'inclusione degli elementi è cumulativa: se un elemento **\<hostInBrowser />** esiste già, non verrà rimosso o sovrascritto. Al contrario, viene creato un altro elemento **\<hostInBrowser />**. Se **false**, il manifesto dell'applicazione non viene modificato.|  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] vengono eseguiti tramite la distribuzione di [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] e pertanto devono essere pubblicati con manifesti di supporto dell'applicazione e della distribuzione. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa l'attività [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) per generare un manifesto dell'applicazione.  
  
 Per configurare un'applicazione da ospitare in un browser, è necessario aggiungere un altro elemento **\<hostInBrowser />** al manifesto dell'applicazione, come illustrato nell'esempio seguente:  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita quando viene compilato un progetto [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] per aggiungere l'elemento `<hostInBrowser />`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come verificare che l'elemento `<hostInBrowser />` sia incluso in un file manifesto dell'applicazione.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Panoramica delle applicazioni browser XAML di WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)