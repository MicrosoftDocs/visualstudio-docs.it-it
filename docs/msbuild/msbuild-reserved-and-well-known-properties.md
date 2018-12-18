---
title: Proprietà riservate e note di MSBuild | Microsoft Docs
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
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d8979877a8cd1fbf60c617e9c03316a46a47879
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Proprietà riservate e note MSBuild
In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è disponibile un set di proprietà predefinite che archiviano informazioni sul file di progetto e i file binari di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Queste proprietà vengono valutate come le altre proprietà di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Ad esempio, per usare la proprietà `MSBuildProjectFile`, è necessario digitare `$(MSBuildProjectFile)`.  
  
 MSBuild usa i valori indicati nella tabella seguente per predefinire le proprietà riservate e quelle note. L'override può essere eseguito solo per le proprietà note usando proprietà globali, proprietà di ambiente con nomi identici o proprietà dichiarate nel file di progetto.
  
## <a name="reserved-and-well-known-properties"></a>Proprietà riservate e proprietà note  
 Nella tabella seguente vengono descritte le proprietà predefinite di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Proprietà|Descrizione|Riservata o nota|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Percorso assoluto della cartella in cui si trovano i file binari di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] attualmente in uso, ad esempio C:\Windows\Microsoft.Net\Framework\\*versionNumber*. Questa proprietà risulta utile quando è necessario fare riferimento ai file nella directory di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Riservata|  
|`MSBuildExtensionsPath`|Introdotta in .NET Framework 4: nessuna differenza tra i valori predefiniti di `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`. È possibile impostare la variabile di ambiente `MSBUILDLEGACYEXTENSIONSPATH` su un valore non Null per abilitare il comportamento del valore predefinito di `MSBuildExtensionsPath` nelle versioni precedenti.<br /><br /> In .NET Framework 3.5 e versioni precedenti il valore predefinito di `MSBuildExtensionsPath` fa riferimento al percorso della sottocartella MSBuild nella cartella \Programmi\ o \Programmi (x86), in base al numero di bit del processo corrente. Ad esempio, per un processo a 32 bit in un computer a 64 bit, la proprietà fa riferimento alla cartella \Programmi (x86). Per un processo a 64 bit in un computer a 64 bit, questa proprietà fa riferimento alla cartella \Programmi.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.<br /><br /> Questo percorso è ideale per contenere i file di destinazione personalizzati. È ad esempio possibile installare i file di destinazione in \Programmi\MSBuild\MyFiles\Northwind.targets, quindi importarli nei file di progetto usando il codice XML seguente:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Nota|  
|`MSBuildExtensionsPath32`|Percorso della sottocartella [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]nella cartella \Programmi o \Programmi (x86). Questo percorso fa sempre riferimento alla cartella \Programmi a 32 bit in un computer a 32 bit e alla cartella \Programmi (x86) in un computer a 64 bit. Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath64`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Nota|  
`MSBuildExtensionsPath64`|Percorso della sottocartella [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nella cartella \Programmi. Per un computer a 64 bit, questo percorso fa sempre riferimento alla cartella \Programmi. Per un computer a 32 bit, questo percorso è vuoto. Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Nota|  
|`MSBuildLastTaskResult`|`true` se l'attività precedente è stata completata senza errori (anche se erano presenti avvisi) o `false` se l'attività precedente ha generato errori. In genere, quando si verifica un errore in un'attività, l'errore è l'ultimo elemento che si verifica nel progetto. Pertanto, il valore di questa proprietà non è mai `false`, tranne negli scenari seguenti:<br /><br /> - Quando l'attributo `ContinueOnError` dell'[elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) è impostato su `WarnAndContinue` (o `true`) o su `ErrorAndContinue`.<br /><br /> - Quando `Target` ha un [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) come elemento figlio.|Riservata|  
|`MSBuildNodeCount`|Numero massimo di processi simultanei usati durante la compilazione. Si tratta del valore specificato per **/maxcpucount** nella riga di comando. Se è stata specificata l'opzione **/maxcpucount** senza un valore, `MSBuildNodeCount` specifica il numero di processori nel computer. Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md) e [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Riservata|  
|`MSBuildProgramFiles32`|Percorso della cartella del programma a 32 bit, ad esempio `C:\Program Files (x86)`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Riservata|  
|`MSBuildProjectDefaultTargets`|L'elenco completo delle destinazioni specificate nell'attributo `DefaultTargets` dell'elemento `Project`. L'elemento `Project` seguente conterrebbe, ad esempio, una proprietà `MSBuildDefaultTargets` con valore `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Riservata|  
|`MSBuildProjectDirectory`|Percorso assoluto della directory in cui si trova il file di progetto, ad esempio `C:\MyCompany\MyProduct`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Riservata|  
|`MSBuildProjectDirectoryNoRoot`|Il valore della proprietà `MSBuildProjectDirectory`, esclusa l'unità radice.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Riservata|  
|`MSBuildProjectExtension`|L'estensione del nome file del file di progetto, incluso il punto, ad esempio PROJ.|Riservata|  
|`MSBuildProjectFile`|Nome file completo del progetto, inclusa l'estensione del nome file, ad esempio MyApp.proj.|Riservata|  
|`MSBuildProjectFullPath`|Percorso assoluto e nome file completo del progetto, inclusa l'estensione del nome del file, ad esempio C:\MyCompany\MyProduct\MyApp.proj.|Riservata|  
|`MSBuildProjectName`|Nome file del progetto senza l'estensione, ad esempio MyApp.|Riservata|  
|`MSBuildRuntimeType`|Il tipo di runtime che è attualmente in esecuzione. Introdotto in MSBuild 15. Il valore può essere non definito (prima di MSBuild 15), `Full` che indica che MSBuild è in esecuzione sul desktop di .NET Framework, `Core` che indica che MSBuild è in esecuzione su .NET Core, o `Mono` che indica che MSBuild è in esecuzione in Mono.|Riservata|  
|`MSBuildStartupDirectory`|Percorso assoluto della cartella in cui viene chiamato [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tramite questa proprietà, è possibile compilare tutto ciò che si trova sotto un punto specifico in un albero di progetto senza creare file dirs.proj in ogni directory. È invece presente un solo progetto, ad esempio c:\traversal.proj, come illustrato di seguito:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Per compilare a un punto qualsiasi dell'albero, digitare:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Non includere la barra rovesciata finale in questa proprietà.|Riservata|  
|`MSBuildThisFile`|Il nome file e la parte dell'estensione di `MSBuildThisFileFullPath`.|Riservata|  
|`MSBuildThisFileDirectory`|La parte di directory di `MSBuildThisFileFullPath`.<br /><br /> Includere la barra rovesciata finale nel percorso.|Riservata|  
|`MSBuildThisFileDirectoryNoRoot`|La parte di directory di `MSBuildThisFileFullPath`, esclusa l'unità radice.<br /><br /> Includere la barra rovesciata finale nel percorso.|Riservata|  
|`MSBuildThisFileExtension`|La parte di estensione del nome file di `MSBuildThisFileFullPath`.|Riservata|  
|`MSBuildThisFileFullPath`|Percorso assoluto del file di progetto o di destinazioni che contiene la destinazione in esecuzione.<br /><br /> Suggerimento: è possibile specificare un percorso relativo in un file di destinazioni che sia relativo al file di destinazioni e non al file di progetto originale.|Riservata|  
|`MSBuildThisFileName`|La parte di nome file di `MSBuildThisFileFullPath`, senza l'estensione.|Riservata|  
|`MSBuildToolsPath`|Percorso di installazione della versione di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] associata al valore di `MSBuildToolsVersion`.<br /><br /> Non includere la barra rovesciata finale nel percorso.<br /><br /> Questa proprietà non può essere sottoposta a override.|Riservata|  
|`MSBuildToolsVersion`|Versione del set di strumenti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] da usare per compilare il progetto.<br /><br /> Nota: un set di strumenti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è costituito da attività, destinazioni e strumenti usati per compilare un'applicazione. Gli strumenti includono compilatori come csc.exe e vbc.exe. Per altre informazioni, vedere [Set di strumenti (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) e [Configurazioni standard e personalizzate del set di strumenti](../msbuild/standard-and-custom-toolset-configurations.md).|Riservata|  

## <a name="names-that-conflict-with-msbuild-elements"></a>Nomi in conflitto con gli elementi di MSBuild

Oltre a quanto sopra, i nomi corrispondenti a elementi del linguaggio MSBuild non possono essere usati per proprietà, elementi o metadati di elementi definiti dall'utente:

* VisualStudioProject
* destinazione
* PropertyGroup
* Output
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Scegliere
* When
* Otherwise

## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md) [Proprietà di MSBuild](../msbuild/msbuild-properties.md)