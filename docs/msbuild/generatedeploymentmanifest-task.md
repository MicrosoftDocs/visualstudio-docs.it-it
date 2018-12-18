---
title: "Attività GenerateDeploymentManifest | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dbb673b263cc7cf4931a07b968a763faf057fad4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="generatedeploymentmanifest-task"></a>Attività GenerateDeploymentManifest
Genera un manifesto di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. In un manifesto di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene descritta la distribuzione di un'applicazione definendone un'identità univoca, identificando caratteristiche di distribuzione come la modalità di installazione o la modalità online, specificando impostazioni e percorsi di aggiornamento dell'applicazione e indicando il manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] corrispondente.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività `GenerateDeploymentManifest`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Name` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, il nome viene dedotto dal parametro `EntryPoint` o `InputManifest`. Se non è possibile dedurre il nome, viene generato un errore.|  
|`AssemblyVersion`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Version` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, l'attività usa il valore "1.0.0.0".|  
|`CreateDesktopShortcut`|Parametro `Boolean` facoltativo.<br /><br /> Se true, durante l'installazione dell'applicazione ClickOnce viene creata un'icona sul desktop.|  
|`DeploymentUrl`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso di aggiornamento per l'applicazione. Se questo parametro non è specificato, non viene definito alcun percorso di aggiornamento per l'applicazione. Se tuttavia il parametro `UpdateEnabled` è impostato su `true`, è necessario specificare il percorso di aggiornamento. Il valore specificato deve essere un percorso URL o UNC completo.|  
|`Description`|Parametro `String` facoltativo.<br /><br /> Specifica una descrizione facoltativa per l'applicazione.|  
|`DisallowUrlActivation`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se l'applicazione deve essere eseguita automaticamente quando viene aperta tramite un URL. Se il parametro è impostato su `true`, è possibile avviare l'applicazione solo dal menu Start. Il valore predefinito di questo parametro è `false`. Questo input è applicabile solo quando il valore del parametro `Install` è impostato su `true`.|  
|`EntryPoint`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Indica il punto di ingresso per l'assembly del manifesto generato. Per un manifesto di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] questo input specifica il manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].<br /><br /> In [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], per generare un manifesto dell'applicazione l'attività [GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md) richiede un `EntryPoint`. Gli assembly o i manifesti nativi non richiedono un `EntryPoint`. Questo requisito è stato applicato con l'errore di compilazione: "MSB3185: EntryPoint non specificato per il manifesto".<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non genera questo errore quando non viene specificato il parametro `EntryPoint` dell'attività. In alternativa, viene inserito il tag \<customHostSpecified> come figlio del tag \<entryPoint>, ad esempio:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> È possibile aggiungere dipendenze DLL al manifesto dell'applicazione seguendo questa procedura:<br /><br /> 1.  Risolvere i riferimenti all'assembly con una chiamata a <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Passare l'output dell'attività precedente e l'assembly stesso a <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Passare le dipendenze usando il parametro `Dependencies` a <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|  
|`ErrorReportUrl`|Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Specifica l'URL della pagina Web visualizzata nelle finestre di dialogo durante le installazioni ClickOnce.|  
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML di input da usare come base per il generatore del manifesto. In questo modo è possibile applicare nel manifesto di output dati strutturati, ad esempio definizioni del manifesto personalizzate. L'elemento radice del documento XML deve essere un nodo assembly nello spazio dei nomi asmv1.|  
|`Install`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se si tratta di un'applicazione installata o di un'applicazione disponibile solo online. Se il parametro è impostato su `true`, l'applicazione verrà installata nel menu Start dell'utente e potrà essere rimossa mediante la finestra di dialogo Installazione applicazioni. Se il parametro è invece impostato su `false`, l'applicazione è destinata all'uso online da una pagina Web. Il valore predefinito di questo parametro è `true`.|  
|`MapFileExtensions`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se viene usato il mapping dell'estensione di file deploy. Se il parametro è impostato su `true`, tutti i file di programma vengono pubblicati con l'estensione di file deploy. Questa opzione è utile per la sicurezza del server Web, per limitare il numero di estensioni di file che è necessario sbloccare per attivare la distribuzione delle applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il valore predefinito di questo parametro è `false`.|  
|`MaxTargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica la lunghezza massima consentita di un percorso di file nella distribuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Se questo parametro è specificato, la lunghezza di ogni percorso di file dell'applicazione viene verificata a fronte di tale limite. Per tutti gli elementi che superano il limite verrà visualizzato un avviso di compilazione. Se questo input non è specificato o è uguale a zero, non viene eseguita alcuna verifica.|  
|`MinimumRequiredVersion`|Parametro `String` facoltativo.<br /><br /> Specifica se è possibile ignorare l'aggiornamento. Se viene usata una versione precedente rispetto a quella minima richiesta, non sarà possibile ignorare l'aggiornamento. Questo parametro è applicabile solo quando il parametro `Install` è impostato su `true`.|  
|`OutputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file del manifesto di output generato. Se questo parametro non è specificato, il nome del file di output viene dedotto dall'identità del manifesto generato.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma di destinazione dell'applicazione. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Il valore predefinito è `AnyCPU`.|  
|`Product`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'identità del manifesto generato. Questo nome viene usato per il collegamento nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`Publisher`|Parametro `String` facoltativo.<br /><br /> Specifica l'editore dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'utente registrato o dall'identità del manifesto generato. Questo nome viene usato per la cartella nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`SuiteNamel`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della cartella del menu Start in cui si trova l'applicazione dopo la distribuzione ClickOnce.|  
|`SupportUrl`|Parametro `String` facoltativo.<br /><br /> Specifica il collegamento visualizzato per l'applicazione nella finestra di dialogo Installazione applicazioni. Il valore specificato deve essere un percorso URL o UNC completo.|  
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Identifica le impostazioni cultura dell'applicazione e specifica il campo `Language` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non viene specificato, si presuppone che l'applicazione sia indipendente dalle impostazioni cultura.|  
|`TrustUrlParameters`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se i parametri della stringa di query dell'URL devono essere disponibili per l'applicazione. Il valore predefinito del parametro è `false` e indica che i parametri non saranno disponibili per l'applicazione.|  
|`UpdateEnabled`|Parametro `Boolean` facoltativo.<br /><br /> Indica se l'applicazione è abilitata per gli aggiornamenti. Il valore predefinito di questo parametro è `false`. Questo parametro è applicabile solo quando il parametro `Install` è impostato su `true`.|  
|`UpdateInterval`|Parametro `Int32` facoltativo.<br /><br /> Specifica l'intervallo di aggiornamento per l'applicazione. Il valore predefinito di questo parametro è zero. Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`.|  
|`UpdateMode`|Parametro `String` facoltativo.<br /><br /> Specifica se è necessario verificare gli aggiornamenti in primo piano prima dell'avvio dell'applicazione o in background durante l'esecuzione dell'applicazione. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Il valore predefinito di questo parametro è `Background`. Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`.|  
|`UpdateUnit`|Parametro `String` facoltativo.<br /><br /> Specifica le unità per il parametro `UpdateInterval`. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco dei parametri della classe Task, vedere [Classe di base Task](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Attività GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)   
 [Attività SignFile](../msbuild/signfile-task.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)