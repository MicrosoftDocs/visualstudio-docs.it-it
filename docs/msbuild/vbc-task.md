---
title: Attività Vbc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b80612f7d7fa97c8ba31de1a631049f48d1f82be
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="vbc-task"></a>Attività Vbc
Esegue il wrapping di vbc.exe, un compilatore che genera file eseguibili con estensione exe, librerie a collegamento dinamico con estensione dll o moduli di codice con estensione netmodule. Per altre informazioni su vbc.exe, vedere [Visual Basic Command-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index) (Compilatore della riga di comando di Visual Basic).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Vbc` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica cartelle aggiuntive in cui eseguire la ricerca degli assembly specificati nell'attributo References.|  
|`AddModules`|Parametro `String[]` facoltativo.<br /><br /> Fa sì che il compilatore renda disponibili per il progetto in compilazione tutte le informazioni sui tipi presenti nei file specificati. Questo parametro corrisponde all'opzione [/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) del compilatore vbc.exe.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base della DLL. Questo parametro corrisponde all'opzione [/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) del compilatore vbc.exe.|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Questo parametro corrisponde all'opzione [/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) del compilatore vbc.exe.|  
|`DebugType`|Parametro `String[]` facoltativo.<br /><br /> Causa la generazione di informazioni di debug da parte del compilatore. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Il valore predefinito è `full`, che consente di collegare un debugger al programma in esecuzione. Il valore `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma consente la visualizzazione di codice in linguaggio assembly solo se il programma in esecuzione è collegato al debugger. Per altre informazioni, vedere [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Parametro `String[]` facoltativo.<br /><br /> Definisce le costanti del compilatore condizionali. Le coppie simbolo/valore sono separate da punti e virgola e vengono specificate tramite la sintassi seguente:<br /><br /> *simbolo1* `=` *valore1* `;` *simbolo2* `=` *valore2*<br /><br /> Questo parametro corrisponde all'opzione [/define](/dotnet/visual-basic/reference/command-line-compiler/define) del compilatore vbc.exe.|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività inserisce la chiave pubblica nell'assembly. Se `false`, l'attività firma l'assembly completamente. Il valore predefinito è `false`. Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`. Questo parametro corrisponde all'opzione [/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) del compilatore vbc.exe.|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Non visualizza gli avvisi specificati. È sufficiente specificare la parte numerica dell'identificatore dell'avviso. Se si specificano più avvisi, usare il punto e virgola per separarli. Questo parametro corrisponde all'opzione [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) del compilatore vbc.exe.|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora i commenti relativi alla documentazione nel file XML specificato. Questo parametro esegue l'override dell'attributo `GenerateDocumentation`. Per altre informazioni, vedere [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività genera informazioni di debug e le inserisce in un file con estensione pdb. Per altre informazioni, vedere [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità di segnalazione degli errori interni da parte dell'attività. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Se è specificato il valore `prompt` e si verifica un errore interno del compilatore, viene chiesto se si vogliono inviare i dati dell'errore a Microsoft.<br /><br /> Se è specificato il valore `send` e si verifica un errore interno del compilatore, i dati dell'errore vengono inviati a Microsoft.<br /><br /> Il valore predefinito è `none`, in base al quale gli errori vengono segnalati solo sotto forma di output di testo.<br /><br /> Questo parametro corrisponde all'opzione [/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) del compilatore vbc.exe.|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica, in byte, il punto in cui allineare le sezioni del file di output. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Questo parametro corrisponde all'opzione [/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) del compilatore vbc.exe.|  
|`GenerateDocumentation`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, vengono generate informazioni di documentazione, che vengono inserite in un file XML con il nome del file eseguibile o della libreria che l'attività sta creando. Per altre informazioni, vedere [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Importa gli spazi dei nomi dalle raccolte di elementi specificati. Questo parametro corrisponde all'opzione [/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) del compilatore vbc.exe.|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Questo parametro corrisponde all'opzione [/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) del compilatore vbc.exe.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per altre informazioni, vedere [/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Specifica la versione del linguaggio: "9" o "10".|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Crea un collegamento a una risorsa .NET Framework nel file di output. Il file di risorse non viene inserito nel file di output. Questo parametro corrisponde all'opzione [/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) del compilatore vbc.exe.|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica la classe o il modulo che contiene la procedura `Sub Main`. Questo parametro corrisponde all'opzione [/main](/dotnet/visual-basic/reference/command-line-compiler/main) del compilatore vbc.exe.|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica l'assembly di cui il modulo fa parte.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Specifica che il compilatore non deve usare il file vbc.rsp. Questo parametro corrisponde al parametro [/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) del compilatore vbc.exe.|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, elimina la visualizzazione dei messaggi informativi del compilatore. Questo parametro corrisponde all'opzione [/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) del compilatore vbc.exe.|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Indica al compilatore di non fare riferimento alle librerie standard. Questo parametro corrisponde all'opzione [/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) del compilatore vbc.exe.|  
|`NoVBRuntimeReference`|Parametro `Boolean` facoltativo.<br /><br /> Solo per uso interno. Se true, viene impedito il riferimento automatico a Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività disabilita la visualizzazione di tutti gli avvisi. Per altre informazioni, vedere [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, le ottimizzazioni del compilatore vengono abilitate. Questo parametro corrisponde all'opzione [/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) del compilatore vbc.exe.|  
|`OptionCompare`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità con cui vengono confrontate le stringhe. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Il valore `binary` specifica l'uso di confronti tra stringhe binarie da parte dell'attività. Il valore `text` specifica l'uso di confronti tra stringhe di testo da parte dell'attività. Il valore predefinito di questo parametro è `binary`. Questo parametro corrisponde all'opzione [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) del compilatore vbc.exe.|  
|`OptionExplicit`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la dichiarazione esplicita delle variabili è obbligatoria. Questo parametro corrisponde all'opzione [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) del compilatore vbc.exe.|  
|`OptionInfer`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, è consentita l'inferenza del tipo delle variabili.|  
|`OptionStrict`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività applica la semantica dei tipi strict per limitare le conversioni implicite di tipi. Questo parametro corrisponde all'opzione [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilatore vbc.exe.|  
|`OptionStrictType`|Parametro `String` facoltativo.<br /><br /> Specifica quale semantica dei tipi strict genera un avviso. Al momento è supportato solo "custom". Questo parametro corrisponde all'opzione [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilatore vbc.exe.|  
|`OutputAssembly`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome del file di output. Questo parametro corrisponde all'opzione [/out](/dotnet/visual-basic/reference/command-line-compiler/out) del compilatore vbc.exe.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Il valore di questo parametro può essere `x86`, `x64`, `Itanium` o `anycpu`. Il valore predefinito è `anycpu`. Questo parametro corrisponde all'opzione [/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) del compilatore vbc.exe.|  
|`References`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'attività per importare informazioni di tipi pubblico dagli elementi specificati nel progetto corrente. Questo parametro corrisponde all'opzione [/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) del compilatore vbc.exe.|  
|`RemoveIntegerChecks`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, disabilita i controlli degli errori di overflow degli integer. Il valore predefinito è `false`. Questo parametro corrisponde all'opzione [/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) del compilatore vbc.exe.|  
|`Resources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Incorpora una risorsa di .NET Framework nel file di output. Questo parametro corrisponde all'opzione [/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) del compilatore vbc.exe.|  
|`ResponseFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Questo parametro corrisponde all'opzione [@ (specificare il file di risposta)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) del compilatore vbc.exe.|  
|`RootNamespace`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per tutte le dichiarazioni di tipo. Questo parametro corrisponde all'opzione [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) del compilatore vbc.exe.|  
|`SdkPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso dei file mscorlib.dll e microsoft.visualbasic.dll. Questo parametro corrisponde all'opzione [/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) del compilatore vbc.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica uno o più file di origine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene usato [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Questa opzione corrisponde all'opzione [/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) del compilatore vbc.exe.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che crea una libreria di codice, `exe`, che crea un'applicazione console, `module`, che crea un modulo o `winexe`, che crea un programma Windows. Il valore predefinito è `library`. Questo parametro corrisponde all'opzione [/target](/dotnet/visual-basic/reference/command-line-compiler/target) del compilatore vbc.exe.|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, con cui si indica che non esiste alcun periodo di timeout.|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica la posizione da cui l'attività caricherà il file eseguibile sottostante (vbc.exe). Se questo parametro non è specificato, viene usato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tutti gli avvisi vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di usare l'oggetto del compilatore in corso, se disponibile. Usato solo da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore tramite la codifica UTF-8. Questo parametro corrisponde all'opzione [/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) del compilatore vbc.exe.|  
|`Verbosity`|Parametro `String` facoltativo.<br /><br /> Specifica il livello di dettaglio dell'output del compilatore. Il livello di dettaglio può essere `Quiet`, `Normal` (impostazione predefinita) o `Verbose`.|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Questo parametro è utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file con estensione ICO nell'assembly, che dà al file di output l'aspetto voluto in Esplora file. Questo parametro corrisponde all'opzione [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) del compilatore vbc.exe.|  
|`Win32Resources`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorsa Win32 (estensione RES) nel file di output . Questo parametro corrisponde all'opzione [/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) del compilatore vbc.exe.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/tooltaskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguita la compilazione di un progetto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```xml  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Basic Command-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)  (Compilatore da riga di comando di Visual Basic)  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)