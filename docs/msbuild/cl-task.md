---
title: "Attività CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5b5609ac97d9322ddf4af5bc5638212a3ccfd045
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="cl-task"></a>Attività CL
Esegue il wrapping dello strumento del compilatore Visual C++, cl.exe. Il compilatore genera file eseguibili (EXE), librerie a collegamento dinamico (DLL) o moduli di codice (NETMODULE). Per altre informazioni, vedere [Opzioni del compilatore](/cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **CL**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
-   **AdditionalIncludeDirectories**  
  
     Parametro String[] facoltativo.  
  
     Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.  
  
     Per altre informazioni, vedere [/I (Directory di inclusione aggiuntive)](/cpp/build/reference/i-additional-include-directories).  
  
-   **AdditionalOptions**  
  
     Parametro String facoltativo.  
  
     Elenco di opzioni della riga di comando. Ad esempio, "/*option1* /*option2* /*option#*". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività.  
  
     Per altre informazioni, vedere [Opzioni del compilatore](/cpp/build/reference/compiler-options).  
  
-   **AdditionalUsingDirectories** Parametro String[] facoltativo.  
  
     Specifica una directory in cui il compilatore effettuerà la ricerca per risolvere i riferimenti di file passati alla direttiva **#using**.  
  
     Per altre informazioni, vedere [/AI (Specifica le directory di metadati)](/cpp/build/reference/ai-specify-metadata-directories).  
  
-   **AlwaysAppend**  
  
     Parametro String facoltativo.  
  
     Stringa che viene sempre generata sulla riga di comando. Il valore predefinito è "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Crea un file di elenco che contiene il codice assembly.  
  
     Per altre informazioni, vedere l'opzione **/Fa** in [/FA, /Fa (File di listato)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **AssemblerOutput**  
  
     Parametro String facoltativo.  
  
     Crea un file di elenco che contiene il codice assembly.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NoListing** - *\<none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndSourceCode** - **/FAs**  
  
    -   **All** - **/FAcs**  
  
     Per altre informazioni, vedere le opzioni **/FA**, **/FAc**, **/FAs** e **/FAcs** in [/FA, /Fa (File di listato)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **BasicRuntimeChecks**  
  
     Parametro String facoltativo.  
  
     Abilita e disabilita la funzionalità di controllo degli errori di run-time, con il pragma [runtime_checks](/cpp/preprocessor/runtime-checks).  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Default** -                          *\<none>*  
  
    -   **StackFrameRuntimeCheck** - **/RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     Per altre informazioni, vedere [/RTC (Controlli di runtime)](/cpp/build/reference/rtc-run-time-error-checks).  
  
-   **BrowseInformation**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, crea un file di informazioni di visualizzazione.  
  
     Per altre informazioni, vedere l'opzione **/FR** in [/FR, /Fr (Crea file sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BrowseInformationFile**  
  
     Parametro String facoltativo.  
  
     Specifica un nome di file per il file di informazioni di visualizzazione.  
  
     Per altre informazioni, vedere il parametro **BrowseInformation** in questa tabella e [/FR, /Fr (Crea file sbr)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BufferSecurityCheck**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, rileva alcuni sovraccarichi del buffer che sovrascrivono l'indirizzo del mittente, una tecnica comune per sfruttare il codice che non applica restrizioni per le dimensioni del buffer.  
  
     Per altre informazioni, vedere [/GS (Controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check).  
  
-   **BuildingInIDE**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, indica che **MSBuild** viene richiamato dall'IDE. In caso contrario, **MSBuild** viene richiamato sulla riga di comando.  
  
-   **CallingConvention**  
  
     Parametro String facoltativo.  
  
     Specifica la convenzione di chiamata, che determina l'ordine in cui gli argomenti della funzione vengono inseriti nello stack, se la funzione chiamante o la funzione chiamata rimuove gli argomenti dallo stack alla fine della chiamata e la convenzione di decorazione dei nomi che il compilatore usa per identificare le singole funzioni.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Cdecl** - **/Gd**  
  
    -   **FastCall** -                          **/Gr**  
  
    -   **StdCall** -                          **/Gz**  
  
     Per altre informazioni, vedere [/Gd, /Gr, /Gv, /Gz (Convenzioni di chiamata)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
-   **CompileAs**  
  
     Parametro String facoltativo.  
  
     Specifica se compilare il file di input come file di origine C o C++.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Default** - *\<none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Per altre informazioni, vedere [/Tc, /Tp, /TC, /TP (Specifica il tipo di file di origine)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
-   **CompileAsManaged**  
  
     Parametro String facoltativo.  
  
     Consente alle applicazioni e ai componenti di usare le funzionalità di Common Language Runtime (CLR).  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **false** - *\<none>*  
  
    -   **true** - **/clr**  
  
    -   **Pure** - **/clr:pure**  
  
    -   **Safe** - **/clr:safe**  
  
    -   **OldSyntax** - **/clr:oldSyntax**  
  
     Per altre informazioni, vedere [/clr (Compilazione Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
-   **CreateHotPatchableImage**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, indica al compilatore di preparare un'immagine per *l'applicazione di una patch a caldo*. Questo parametro assicura che la prima istruzione di ogni funzione sia di due byte, condizione necessaria per l'applicazione di una patch a caldo.  
  
     Per altre informazioni, vedere [/hotpatch (Crea immagine con funzionalità di patch a caldo)](/cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
-   **DebugInformationFormat**  
  
     Parametro String facoltativo.  
  
     Seleziona il tipo delle informazioni di debug create per il programma e indica se tali informazioni vengono mantenute in file oggetto (OBJ) o in un database di programma (PDB).  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **OldStyle** - **/Z7**  
  
    -   **ProgramDatabase** - **/Zi**  
  
    -   **EditAndContinue** - **/ZI**  
  
     Per altre informazioni, vedere [/Z7, /Zd, /Zi, /ZI (Formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format).  
  
-   **DisableLanguageExtensions**  
  
     Parametro booleano facoltativo.  
  
     Se **true**, indica al compilatore di generare un errore per i costrutti di linguaggio che non sono compatibili con ANSI C o ANSI C++.  
  
     Per altre informazioni, vedere l'opzione **/Za** in [/Za, /Ze (Disabilita estensioni linguaggio)](/cpp/build/reference/za-ze-disable-language-extensions).  
  
-   **DisableSpecificWarnings**  
  
     Parametro String[] facoltativo.  
  
     Disabilita i numeri di avviso specificati in un elenco delimitato da punti e virgola.  
  
     Per altre informazioni, vedere l'opzione `/wd` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **EnableEnhancedInstructionSet**  
  
     Parametro String facoltativo.  
  
     Specifica l'architettura per la generazione di codice che usa le istruzioni Streaming SIMD Extensions (SSE) e Streaming SIMD Extensions 2 (SSE2).  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
     Per altre informazioni, vedere [/arch (x86)](/cpp/build/reference/arch-x86).  
  
-   **EnableFiberSafeOptimizations**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, supporta l'indipendenza da fiber per i dati allocati usando l'archiviazione locale di thread statici, ovvero dati allocati usando `__declspec(thread)`.  
  
     Per altre informazioni, vedere [/GT (Supporta archiviazione locale di thread indipendente da fiber)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
-   **EnablePREfast**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, abilitare l'analisi del codice.  
  
     Per altre informazioni, vedere [/analyze (Analisi codice)](/cpp/build/reference/analyze-code-analysis).  
  
-   **ErrorReporting**  
  
     Parametro String facoltativo.  
  
     Consente di inviare informazioni sugli errori interni del compilatore direttamente a Microsoft. Per impostazione predefinita, l'impostazione nelle build IDE è **Prompt** e l'impostazione nelle build da riga di comando è **Queue**.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **None** - **/errorReport:none**  
  
    -   **Prompt** - **/errorReport:prompt**  
  
    -   **Queue** - **/errorReport:queue**  
  
    -   **Send** - **/errorReport:send**  
  
     Per altre informazioni, vedere [/errorReport (Segnala gli errori interni del compilatore)](/cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
-   **ExceptionHandling**  
  
     Parametro String facoltativo.  
  
     Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **false** - *\<none>*  
  
    -   **Async** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     Per altre informazioni, vedere [/EH (Modello di gestione delle eccezioni)](/cpp/build/reference/eh-exception-handling-model).  
  
-   **ExpandAttributedSource**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, viene creato un file di listato con attributi espansi inseriti nel file di origine.  
  
     Per altre informazioni, vedere [/Fx (Esegue il merge del codice)](/cpp/build/reference/fx-merge-injected-code).  
  
-   **FavorSizeOrSpeed**  
  
     Parametro String facoltativo.  
  
     Specifica se ottimizzare la dimensione o la velocità del codice.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Neither** - *\<none>*  
  
    -   **Size** - **/Os**  
  
    -   **Speed** - **/Ot**  
  
     Per altre informazioni, vedere [/Os, /Ot (Ottimizza per dimensione codice, Ottimizza per velocità codice)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
-   **FloatingPointExceptions**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, abilita il modello di eccezione a virgola mobile affidabile. Vengono generate eccezioni immediatamente dopo l'attivazione.  
  
     Per altre informazioni, vedere l'opzione /**fp:except** in [/fp (Specifica il comportamento della virgola mobile)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **FloatingPointModel**  
  
     Parametro String facoltativo.  
  
     Imposta il modello a virgola mobile.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Precise** - **/fp:precise**  
  
    -   **Strict** - **/fp:strict**  
  
    -   **Fast** - **/fp:fast**  
  
     Per altre informazioni, vedere [/fp (Specifica il comportamento della virgola mobile)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **ForceConformanceInForLoopScope**  
  
     Parametro booleano facoltativo.  
  
     Se `true`, consente di implementare il comportamento C++ standard per cicli [for](/cpp/cpp/for-statement-cpp) con estensioni Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).  
  
     Per altre informazioni, vedere [/Zc:forScope (Imponi conformità nell'ambito di un ciclo For)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).  
  
-   **ForcedIncludeFiles**  
  
     Parametro `String[]` facoltativo.  
  
     Determina l'elaborazione di uno o più file di intestazione specificati da parte del preprocessore.  
  
     Per altre informazioni, vedere [/FI (Specifica il file di inclusione da utilizzare)](/cpp/build/reference/fi-name-forced-include-file).  
  
-   **ForcedUsingFiles**  
  
     Parametro **String[]** facoltativo.  
  
     Determina l'elaborazione di uno o più file **#using** specificati da parte del preprocessore.  
  
     Per altre informazioni, vedere [/FU (Specifica file #using da utilizzare)](/cpp/build/reference/fu-name-forced-hash-using-file).  
  
-   **FunctionLevelLinking**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, indica al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT).  
  
     Per altre informazioni, vedere [/Gy (Attiva collegamento a livello di funzione)](/cpp/build/reference/gy-enable-function-level-linking).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, indica al compilatore di elaborare i commenti per la documentazione nei file del codice sorgente e di creare un file XDC per ogni file del codice sorgente che contiene commenti per la documentazione.  
  
     Per altre informazioni, vedere [/doc (Elabora i commenti per la documentazione) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Vedere anche il parametro **XMLDocumentationFileName** in questa tabella.  
  
-   **IgnoreStandardIncludePath**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, impedisce al compilatore di cercare file di inclusione nelle directory specificate nelle variabili di ambiente PATH e INCLUDE.  
  
     Per altre informazioni, vedere [/X (Ignora percorso di inclusione standard)](/cpp/build/reference/x-ignore-standard-include-paths).  
  
-   **InlineFunctionExpansion**  
  
     Parametro **String** facoltativo.  
  
     Specifica il livello di espansione della funzione inline per la compilazione.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Default** - *\<none>*  
  
    -   **Disabled** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** - **/Ob2**  
  
     Per altre informazioni, vedere [/Ob (Espansione funzioni inline)](/cpp/build/reference/ob-inline-function-expansion).  
  
-   **IntrinsicFunctions**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, sostituisce alcune chiamate di funzione con form intrinseci o speciali della funzione che consentono di eseguire l'applicazione più rapidamente.  
  
     Per altre informazioni, vedere [/Oi (Genera funzioni intrinseche)](/cpp/build/reference/oi-generate-intrinsic-functions).  
  
-   **MinimalRebuild**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, abilita la ricompilazione minima, che determina se è necessario ricompilare i file di origine C++ che includono modifiche alle definizioni delle classi C++ archiviate nei file di intestazione (estensione h).  
  
     Per altre informazioni, vedere [/Gm (Abilita ricompilazione minima)](/cpp/build/reference/gm-enable-minimal-rebuild).  
  
-   **MultiProcessorCompilation**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, usare più processori per la compilazione. Questo parametro crea un processo per ogni processore effettivo nel computer in uso.  
  
     Per altre informazioni, vedere [/MP (Compilazione con più processi)](/cpp/build/reference/mp-build-with-multiple-processes). Vedere anche il parametro **ProcessorNumber** in questa tabella.  
  
-   **ObjectFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica un nome file oggetto (OBJ) o una directory da usare al posto dell'impostazione predefinita.  
  
     Per altre informazioni, vedere [/Fo (Nome file oggetto)](/cpp/build/reference/fo-object-file-name).  
  
-   **ObjectFiles**  
  
     Parametro **String[]** facoltativo.  
  
     Elenco di file oggetto.  
  
-   **OmitDefaultLibName**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, omette il nome della libreria di runtime C predefinita nel file oggetto (OBJ). Per impostazione predefinita, il compilatore inserisce il nome della libreria nel file OBJ per indirizzare il linker alla libreria corretta.  
  
     Per altre informazioni, vedere [/Zl (Omette il nome della libreria predefinita)](/cpp/build/reference/zl-omit-default-library-name).  
  
-   **OmitFramePointers**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, disabilita la creazione di puntatori ai frame nello stack di chiamate.  
  
     Per altre informazioni, vedere [/Oy (Omissione dei puntatori ai frame)](/cpp/build/reference/oy-frame-pointer-omission).  
  
-   **OpenMPSupport**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, indica al compilatore di elaborare direttive e clausole OpenMP.  
  
     Per altre informazioni, vedere [/openmp (Attiva supporto OpenMP 2.0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
-   **Optimization**  
  
     Parametro **String** facoltativo.  
  
     Specifica diverse ottimizzazioni del codice per velocità e dimensioni.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Disabled** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Full** - **/Ox**  
  
     Per altre informazioni, vedere [Opzioni /O (Ottimizza codice)](/cpp/build/reference/o-options-optimize-code).  
  
-   **PrecompiledHeader**  
  
     Parametro **String** facoltativo.  
  
     Creare o usare un file di intestazione precompilata (PCH) durante la compilazione.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **NotUsing** - *\<none>*  
  
    -   **Create** - **/Yc**  
  
    -   **Use** - **/Yu**  
  
     Per altre informazioni, vedere [/Yc (Crea il file di intestazione precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usa il file di intestazione precompilata)](/cpp/build/reference/yu-use-precompiled-header-file). Vedere anche i parametri **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** in questa tabella.  
  
-   **PrecompiledHeaderFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica un nome di file di intestazione precompilata da creare o usare.  
  
     Per altre informazioni, vedere [/Yc (Crea il file di intestazione precompilata)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usa il file di intestazione precompilata)](/cpp/build/reference/yu-use-precompiled-header-file).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica un nome di percorso per un'intestazione precompilata anziché usare il nome di percorso predefinito.  
  
     Per altre informazioni, vedere [/Fp (Specifica file pch)](/cpp/build/reference/fp-name-dot-pch-file).  
  
-   **PreprocessKeepComments**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, conserva i commenti durante la pre-elaborazione.  
  
     Per altre informazioni, vedere [/C (Conserva i commenti durante la pre-elaborazione)](/cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
-   **PreprocessorDefinitions**  
  
     Parametro `String[]` facoltativo.  
  
     Definisce un simbolo di pre-elaborazione per il file di origine.  
  
     Per altre informazioni, vedere [/D (definizioni preprocessore)](/cpp/build/reference/d-preprocessor-definitions).  
  
-   **PreprocessOutput**  
  
     Parametro `ITaskItem[]` facoltativo.  
  
     Definisce una matrice di elementi di output del preprocessore che può essere usata ed emessa dalle attività.  
  
-   **PreprocessOutputPath**  
  
     Parametro `String` facoltativo.  
  
     Specifica il nome del file di output in cui il parametro **PreprocessToFile** scrive l'output pre-elaborato.  
  
     Per altre informazioni, vedere [/Fi (pre-elaborazione nome file di output)](/cpp/build/reference/fi-preprocess-output-file-name).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, pre-elabora i file di origine C e C++ e copia i file pre-elaborati nel dispositivo di output standard.  
  
     Per altre informazioni, vedere [/EP (Pre-elabora in stdout senza direttive #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
-   **PreprocessToFile**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, pre-elabora i file di origine C e C++ e scrive l'output pre-elaborato in un file.  
  
     Per altre informazioni, vedere [/P (Pre-elabora in un file)](/cpp/build/reference/p-preprocess-to-a-file).  
  
-   **ProcessorNumber**  
  
     Parametro `Integer` facoltativo.  
  
     Specifica il numero massimo di processori da usare in una compilazione multiprocessore. Usare questo parametro in combinazione con il parametro **MultiProcessorCompilation**.  
  
-   **ProgramDataBaseFileName**  
  
     Parametro `String` facoltativo.  
  
     Specifica un nome file per il file del database di programma (PDB).  
  
     Per altre informazioni, vedere [/Fd (Nome file database di programma)](/cpp/build/reference/fd-program-database-file-name).  
  
-   **RuntimeLibrary**  
  
     Parametro `String` facoltativo.  
  
     Indica se un modulo con multithreading è una DLL e seleziona versioni finali o di debug della libreria di runtime.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     Per altre informazioni, vedere [/MD, /MT, /LD (utilizzo della libreria di runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library).  
  
-   **RuntimeTypeInfo**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi di runtime).  
  
     Per altre informazioni, vedere [/GR (Attiva informazioni sui tipi in fase di esecuzione)](/cpp/build/reference/gr-enable-run-time-type-information).  
  
-   **ShowIncludes**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, indica al compilatore di generare un elenco di file di inclusione.  
  
     Per altre informazioni, vedere [/showIncludes (Elenca i file di inclusione)](/cpp/build/reference/showincludes-list-include-files).  
  
-   **SmallerTypeCheck**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, segnala un errore di run-time se un valore viene assegnato a un tipo di dati più piccolo e provoca una perdita di dati.  
  
     Per altre informazioni, vedere l'opzione **/RTCc** in [/RTC (Controlli di runtime)](/cpp/build/reference/rtc-run-time-error-checks).  
  
-   **Sources**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Specifica un elenco dei file di origine separati da spazi.  
  
-   **StringPooling**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, consente al compilatore di creare una copia di stringhe identiche nell'immagine del programma.  
  
     Per altre informazioni, vedere [/GF (Elimina stringhe duplicate)](/cpp/build/reference/gf-eliminate-duplicate-strings).  
  
-   **StructMemberAlignment**  
  
     Parametro `String` facoltativo.  
  
     Specifica l'allineamento dei byte per tutti i membri in una struttura.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **Default** - **/Zp1**  
  
    -   **1Byte** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **/Zp4**  
  
    -   **8Bytes** - **/Zp8**  
  
    -   **16Bytes** - **/Zp16**  
  
     Per altre informazioni, vedere [/Zp (Allineamento membri struct)](/cpp/build/reference/zp-struct-member-alignment).  
  
-   **SuppressStartupBanner**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
     Per altre informazioni, vedere [/nologo (Non visualizza il messaggio di avvio) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
-   **TrackerLogDirectory**  
  
     Parametro `String` facoltativo.  
  
     Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.  
  
     Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Parametro **String[]** facoltativo.  
  
     Considera l'elenco specificato di avvisi del compilatore come errori.  
  
     Per altre informazioni, vedere l'opzione **/we**`n` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWarningAsError**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, considera tutti gli avvisi del compilatore come errori.  
  
     Per altre informazioni, vedere l'opzione **/WX**in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, considerare il tipo `wchar_t` come un tipo nativo.  
  
     Per altre informazioni, vedere [/Zc:wchar_t (Tipo nativo wchar_t)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, rimuove la definizione dei simboli specifici di Microsoft definiti dal compilatore.  
  
     Per altre informazioni, vedere l'opzione **/u** in [/U, /u (Annulla la definizione dei simboli)](/cpp/build/reference/u-u-undefine-symbols).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parametro `String[]` facoltativo.  
  
     Specifica un elenco di uno o più simboli del preprocessore per cui rimuovere la definizione.  
  
     Per altre informazioni, vedere l'opzione **/U** in [/U, /u (Annulla la definizione dei simboli)](/cpp/build/reference/u-u-undefine-symbols).  
  
-   **UseFullPaths**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, visualizza il percorso completo dei file di codice sorgente passati al compilatore nella diagnostica.  
  
     Per altre informazioni, vedere [/FC (Percorso completo del file di codice sorgente nella diagnostica)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, causa la creazione del file di output in formato UTF-8.  
  
     Per altre informazioni, vedere l'opzione **/FAu** in [/FA, /Fa (File di listato)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **WarningLevel**  
  
     Parametro `String` facoltativo.  
  
     Specifica il livello massimo dell'avviso che verrà generato dal compilatore.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **Level4** - **/W4**  
  
    -   **EnableAllWarnings** - **/Wall**  
  
     Per altre informazioni, vedere l'opzione */W***n* in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **WholeProgramOptimization**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`,abilita l'ottimizzazione dell'intero programma.  
  
     Per altre informazioni, vedere [/GL (Ottimizzazione intero programma)](/cpp/build/reference/gl-whole-program-optimization).  
  
-   **XMLDocumentationFileName**  
  
     Parametro `String` facoltativo.  
  
     Specifica il nome dei file di documentazione XML generati. Questo parametro può essere un nome di file o directory.  
  
     Per altre informazioni, vedere l'argomento `name` in [/doc (Elabora i commenti per la documentazione) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Vedere anche il parametro **GenerateXMLDocumentationFiles** in questa tabella.  
  
-   **MinimalRebuildFromTracking**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, viene eseguita una compilazione incrementale verificata; se `false`, viene eseguita una ricompilazione.  
  
-   **TLogReadFiles**  
  
     Parametro `ITaskItem[]` facoltativo.  
  
     Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di lettura*.  
  
     Un log di rilevamento dei file di lettura (TLOG) contiene i nomi dei file di input letti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.  
  
-   **TLogWriteFiles**  
  
     Parametro `ITaskItem[]` facoltativo.  
  
     Specifica una matrice di elementi che rappresentano i *log di rilevamento dei file di scrittura*.  
  
     Un log di rilevamento dei file di scrittura (TLOG) contiene i nomi dei file di output scritti da un'attività e viene usato dal sistema di compilazione del progetto per supportare le compilazioni incrementali. Per altre informazioni, vedere i parametri **TrackerLogDirectory** e **TrackFileAccess** in questa tabella.  
  
-   **TrackFileAccess**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, rileva i modelli di accesso ai file.  
  
     Per altre informazioni, vedere i parametri **TLogReadFiles** e **TLogWriteFiles** in questa tabella.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)