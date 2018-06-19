---
title: Attività UidManager | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e6156111c680bb7d9462fc94f879df9784486c2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31575819"
---
# <a name="uidmanager-task"></a>Attività UidManager
L'attività <xref:Microsoft.Build.Tasks.Windows.UidManager> controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclusi nei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`IntermediateDirectory`|Parametro **String** facoltativo.<br /><br /> Specifica la directory usata per eseguire il backup dei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine specificati dal parametro **MarkupFiles**.|  
|`MarkupFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica i file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine da includere per il controllo, l'aggiornamento o la rimozione degli UID.|  
|`Task`|Parametro **String** obbligatorio.<br /><br /> Specifica l'attività di gestione degli UID da eseguire. Le opzioni valide sono **Check**, **Update** o **Remove**.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività <xref:Microsoft.Build.Tasks.Windows.UidManager> per verificare che i file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine specificati contengano gli elementi [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] con UID appropriati.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Procedura: Localizzare un'applicazione](/dotnet/framework/wpf/advanced/how-to-localize-an-application)