---
title: Attività GetWinFXPath | Microsoft Docs
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e02d0f93dd406df170de2d4e83023fedced7d932
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="getwinfxpath-task"></a>Attività GetWinFXPath
L'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] corrente.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WinFXPath`|Parametro di output **String** facoltativo.<br /><br /> Specifica il percorso reale del runtime [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso del runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] nativo.|  
|`WinFXWowPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso degli assembly [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] nel modulo **Windows on Windows** a 32 bit nei sistemi a 64 bit.|  
  
## <a name="remarks"></a>Note  
 Se l'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> viene eseguita su un processore a 64 bit, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXWowPath**. In caso contrario, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXNativePath**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'attività **GetWinFXPath** per individuare il percorso nativo del runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)