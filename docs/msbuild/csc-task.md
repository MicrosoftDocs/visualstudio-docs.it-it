---
title: "Attività Csc | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a74f8c43d35104957b62fb3da93d2acbf6a9a303
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="csc-task"></a>Attività Csc
Esegue il wrap di CSC.exe e produce file eseguibili (con estensione EXE), librerie a collegamento dinamico (con estensione DLL) o moduli di codice (con estensione NETMODULE). Per altre informazioni su CSC.exe, vedere [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Csc` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica directory aggiuntive in cui cercare i riferimenti. Per altre informazioni, vedere [/lib (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Parametro `String` facoltativo.<br /><br /> Specifica uno o più moduli che devono fare parte dell'assembly. Per altre informazioni, vedere [/addmodule (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, compila codice che usa la parola chiave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Per altre informazioni, vedere [/unsafe (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Parametro `String` facoltativo.<br /><br /> Specifica il file di configurazione dell'applicazione contenente le impostazioni di associazione dell'assembly.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se il calcolo di interi che supera i limiti del tipo di dati genera un'eccezione in fase di esecuzione. Per altre informazioni, vedere [/checked (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Per altre informazioni, vedere [/codepage (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di debug. `DebugType` può essere `full` o `pdbonly`. Il valore predefinito è `full`, che consente di associare un debugger a un programma in esecuzione. La specifica di `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma assembler viene visualizzato solo quando il programma in esecuzione è collegato al debugger.<br /><br /> Questo parametro esegue l'override del parametro `EmitDebugInformation`.<br /><br /> Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Parametro `String` facoltativo.<br /><br /> Definisce i simboli del preprocessore. Per altre informazioni, vedere [/define (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che si vuole un'assembly completamente firmata. Se `false`, specifica che si vuole solo posizionare la chiave pubblica nell'assembly.<br /><br /> Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`.<br /><br /> Per altre informazioni, vedere [/delaysign (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Specifica l'elenco di avvisi da disabilitare. Per altre informazioni, vedere [/nowarn (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora commenti sulla documentazione in un file XML. Per altre informazioni, vedere [/doc (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> If `true`, l'attività genera informazioni di debug e le inserisce in un file di database di programma (con estensione PDB). Se `false`, l'attività non genera alcuna informazione di debug. Il valore predefinito è `false`. Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Offre un modo pratico per segnalare a Microsoft un errore interno di C#. Il valore di questo parametro può essere `prompt`, `send` o `none`. Se il parametro è impostato su `prompt`, si riceve un avviso quando si verifica un errore interno del compilatore. L'avviso consente di inviare elettronicamente una segnalazione a Microsoft. Se il parametro è impostato su `send`, viene inviato automaticamente un report sui bug. Se il parametro è impostato su `none`, l'errore viene segnalato solo nell'output di testo del compilatore. Il valore predefinito è `none`. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica le dimensioni delle sezioni nel file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica il percorso assoluto al file nell'output del compilatore. Se `false`, specifica il nome del file. Il valore predefinito è `false`. Per altre informazioni, vedere [/fullpaths (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Per altre informazioni, vedere [/keycontainer (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per altre informazioni, vedere [/keyfile (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione del linguaggio da usare. Per altre informazioni, vedere [/langversion (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Crea un collegamento a una risorsa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nel file di output. Il file di risorse non viene inserito nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/linkresource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [/linkresource (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso del metodo `Main`. Per altre informazioni, vedere [/main (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly di cui fa parte il modulo.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, indica al compilatore di non eseguire la compilazione con il file csc.rsp. Per altre informazioni, vedere [/noconfig (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, elimina la visualizzazione dei messaggi informativi del compilatore. Per altre informazioni, vedere [/nologo (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce l'importazione di mscorlib.dll, che definisce l'intero spazio dei nomi di sistema. Usare questo parametro se si vuole definire o creare uno spazio dei nomi e oggetti di sistema personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, non includere il manifesto Win32 predefinito.|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, abilita le ottimizzazioni. Se `false`, disabilita le ottimizzazioni. Per altre informazioni, vedere [/optimize (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome del file di output. Per altre informazioni, vedere [/out (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`OutputRefAssembly`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file di assembly di riferimento di output. Per altre informazioni, vedere [/refout (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option).|  
|`PdbFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome file delle informazioni di debug. Il nome predefinito è il nome file di output con estensione PDB.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Il valore di questo parametro può essere `x86`, `x64` o `anycpu`. Il valore predefinito è `anycpu`. Per altre informazioni, vedere [/platform (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'attività per importare informazioni di tipi pubblico dagli elementi specificati nel progetto corrente. Per altre informazioni, vedere [/reference (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> È possibile specificare un alias di riferimento [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] in un file [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aggiungendo i metadati `Aliases` all'elemento originale di "riferimento". Ad esempio, per impostare l'alias "LS1" nella riga di comando CSC seguente:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> è necessario usare:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Inserisce una risorsa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/resource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [/resource (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Parametro `String` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Per altre informazioni, vedere [@ (specifica di un file di risposta)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica uno o più file di origine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che crea una libreria di codice, `exe`, che crea un'applicazione console, `module`, che crea un modulo o `winexe`, che crea un programma Windows. Il valore predefinito è `library`. Per altre informazioni, vedere [/target (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tutti gli avvisi vengono considerati come errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di usare l'oggetto del compilatore in corso, se disponibile. Usato solo da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore tramite la codifica UTF-8. Per altre informazioni, vedere [/utf8output (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Parametro `Int32` facoltativo.<br /><br /> Specifica il livello di avviso da visualizzare nel compilatore. Per altre informazioni, vedere [/warn (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro è utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file con estensione ICO nell'assembly, che dà al file di output l'aspetto voluto in Esplora file. Per altre informazioni, vedere [/win32icon (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Parametro `String` facoltativo.<br /><br /> Specifica il manifesto Win32 da includere.|  
|`Win32Resource`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorsa Win32 (estensione RES) nel file di output . Per altre informazioni, vedere [/win32res (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe `Microsoft.Build.Tasks.ManagedCompiler`, che eredita dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/tooltaskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `Csc` per compilare un eseguibile dai file di origine nella raccolta di elementi `Compile`.  
  
```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)
