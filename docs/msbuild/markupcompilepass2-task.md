---
title: "Attività MarkupCompilePass2 | Microsoft Docs"
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1cec015b10e56ce1bb0d9b5aff2fc4faae5686e0
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="markupcompilepass2-task"></a>Attività MarkupCompilePass2
L'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> esegue la compilazione del markup del secondo passaggio sui file [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] che fanno riferimento a tipi nello stesso progetto.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Parametro **Boolean** facoltativo.<br /><br /> Specifica se eseguire l'attività in un <xref:System.AppDomain> separato. Se il parametro restituisce **false** l'attività viene eseguita più rapidamente e nello stesso <xref:System.AppDomain> di [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]. Se il parametro restituisce **true** l'attività viene eseguita più lentamente e in un secondo <xref:System.AppDomain> isolato da [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)].|  
|`AssembliesGeneratedDuringBuild`|Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che vengono modificati durante il processo di compilazione. Ad esempio, una soluzione [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] può contenere un progetto che fa riferimento all'output compilato di un altro progetto. In questo caso, l'output compilato del secondo progetto può essere aggiunto a **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: **AssembliesGeneratedDuringBuild** deve contenere riferimenti al set completo di assembly generati da una soluzione di compilazione.|  
|`AssemblyName`|Parametro **String** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto. Ad esempio, se un progetto sta generando un eseguibile [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] il cui nome è **WinExeAssembly.exe**, il parametro **AssemblyName** presenterà il valore **WinExeAssembly**.|  
|`GeneratedBaml`|Parametro di output **ITaskItem[]** facoltativo.<br /><br /> Contiene l'elenco dei file generati in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`KnownReferencePaths`|Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che non vengono mai modificati durante il processo di compilazione. Include assembly che si trovano in [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], in una directory di installazione di [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] e così via.|  
|`Language`|Parametro **String** obbligatorio.<br /><br /> Specifica il linguaggio gestito supportato dal compilatore. Le opzioni valide sono **C#**, **VB**, **JScript** e **C++**.|  
|`LocalizationDirectivesToLocFile`|Parametro **String** facoltativo.<br /><br /> Specifica come generare informazioni di localizzazione per ogni file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine. Le opzioni valide sono **None**, **CommentsOnly** e **All**.|  
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui vengono generati i file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputType`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di assembly generato da un progetto. Le opzioni valide sono **winexe**, **exe**, **library** e **netmodule**.|  
|`References`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei riferimenti dai file agli assembly contenenti i tipi usati nei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Un riferimento è relativo all'assembly generato dall'attività <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, che deve essere eseguita prima dell'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Parametro **String** facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per le classi all'interno del progetto. **RootNamespace** viene usato anche come spazio dei nomi predefinito di un file di codice gestito generato quando il file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] non include l'attributo `x:Class`.|  
|`XAMLDebuggingInformation`|Parametro **Boolean** facoltativo.<br /><br /> Se **true**, le informazioni diagnostiche verranno generate e incluse nel file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilato per agevolare il debug.|  
  
## <a name="remarks"></a>Note  
 Prima di eseguire **MarkupCompilePass2**, è necessario generare un assembly temporaneo che contenga i tipi usati dai file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] il cui passaggio di compilazione del markup è stato rinviato. L'assembly temporaneo viene generato mediante l'esecuzione dell'attività **GenerateTemporaryTargetAssembly**.  
  
 Al momento dell'esecuzione, a <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> viene specificato un riferimento all'assembly temporaneo generato. Questo consente la compilazione in formato binario dei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] la cui compilazione era stata rinviata nel primo passaggio di compilazione del markup.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente visualizza come usare l'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> per eseguire un secondo passaggio di compilazione.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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