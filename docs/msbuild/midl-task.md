---
title: "Attività MIDL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 51ed6c8c34fd5aa37eebffabcda077ca8554c498
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="midl-task"></a>Attività MIDL
Esegue il wrapping dello strumento di compilazione Microsoft Interface Definition Language (MIDL), midl.exe. Per altre informazioni, vedere "MIDL Command-Line Reference" (Informazioni di riferimento sulla riga di comando MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **MIDL**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
-   **AdditionalIncludeDirectories**  
  
     Parametro **String[]** facoltativo.  
  
     Aggiunge una directory all'elenco di directory nelle quali viene effettuata la ricerca dei file IDL importati, inclusi i file di intestazione e i file di configurazione dell'applicazione.  
  
     Per altre informazioni, vedere l'opzione **/I** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **AdditionalOptions**  
  
     Parametro **String** facoltativo.  
  
     Elenco di opzioni della riga di comando. Ad esempio, **"***/opzione1 /opzione2 /opzione#*". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività MIDL.  
  
     Per altre informazioni, vedere "MIDL Command-Line Reference" (Informazioni di riferimento sulla riga di comando MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ApplicationConfigurationMode**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, consente di usare alcune parole chiave dei file di configurazione dell'applicazione nel file IDL.  
  
     Per altre informazioni, vedere l'opzione **/app_config** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ClientStubFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file stub client per un'interfaccia RPC.  
  
     Per altre informazioni, vedere l'opzione **/cstub** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **ServerStubFile** in questa tabella.  
  
-   **CPreprocessOptions**  
  
     Parametro **String** facoltativo.  
  
     Specifica le opzioni da passare al preprocessore C/C++. Specificare un elenco di opzioni del preprocessore delimitate da spazio.  
  
     Per altre informazioni, vedere l'opzione **/cpp_opt** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **DefaultCharType**  
  
     Parametro **String** facoltativo.  
  
     Specifica il tipo di carattere predefinito che verrà usato dal compilatore C per compilare il codice generato.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**Signed**|**/char signed**|  
    |**Unsigned**|**/char unsigned**|  
    |**Ascii**|**/char ascii7**|  
  
     Per altre informazioni, vedere l'opzione **/char** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **DllDataFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome file per il file *dlldata* generato per una DLL del proxy.  
  
     Per altre informazioni, vedere l'opzione **/dlldata** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **EnableErrorChecks**  
  
     Parametro **String** facoltativo.  
  
     Specifica il tipo di controllo errori che verrà eseguito dagli stub generati in fase di esecuzione.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**None**|**/error none**|  
    |**EnableCustom**|**/error**|  
    |**All**|**/error all**|  
  
     Per altre informazioni, vedere l'opzione **/error** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckAllocations**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, verifica la presenza di errori di memoria insufficiente.  
  
     Per altre informazioni, vedere l'opzione **/error allocation** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckBounds**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, controlla le dimensioni delle matrici variabili conformi e variabili rispetto alla specifica relativa alla durata delle trasmissioni.  
  
     Per altre informazioni, vedere l'opzione **/error bounds_check** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckEnumRange**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, controlla che i valori di enumerazione siano compresi in un intervallo consentito.  
  
     Per altre informazioni, vedere l'opzione **/error enum** nella guida della riga di comando (**/?**) per midl.exe.  
  
-   **ErrorCheckRefPointers**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, controlla che nessun puntatore di riferimento Null venga passato agli stub client.  
  
     Per altre informazioni, vedere l'opzione **/error ref** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ErrorCheckStubData**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, genera uno stub che acquisisce eccezioni di unmarshalling sul lato server e le propaga al client.  
  
     Per altre informazioni, vedere l'opzione **/error stub_data** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateClientFiles**  
  
     Parametro **String** facoltativo.  
  
     Specifica se il compilatore genera un file di origine C sul lato client per un'interfaccia RPC.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**None**|**/client none**|  
    |**Stub**|**/client stub**|  
  
     Per altre informazioni, vedere l'opzione **/client** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateServerFiles**  
  
     Parametro **String** facoltativo.  
  
     Specifica se il compilatore genera un file di origine C sul lato server per un'interfaccia RPC.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**None**|**/server none**|  
    |**Stub**|**/server stub**|  
  
     Per altre informazioni, vedere l'opzione **/server** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateStublessProxies**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, genera stub completamente interpretati con proxy senza stub per le interfacce degli oggetti.  
  
     Per altre informazioni, vedere l'opzione **/Oicf** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **GenerateTypeLibrary**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, non viene generato un file di libreria dei tipi (TLB).  
  
     Per altre informazioni, vedere l'opzione **/notlb** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **HeaderFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file di intestazione generato.  
  
     Per altre informazioni, vedere l'opzione **/h** o **header** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **IgnoreStandardIncludePath**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, l'attività MIDL effettua la ricerca solo nelle directory specificate usando l'opzione **AdditionalIncludeDirectories** e ignora la directory corrente e le directory specificate dalla variabile di ambiente INCLUDE.  
  
     Per altre informazioni, vedere l'opzione **/no_def_idir** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **InterfaceIdentifierFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del *file dell'identificatore di interfaccia* per un'interfaccia COM. Esegue l'override del nome predefinito ottenuto aggiungendo "_i.c" al nome file IDL.  
  
     Per altre informazioni, vedere l'opzione **/iid** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **LocaleID**  
  
     Parametro **int** facoltativo.  
  
     Specifica l'*identificatore delle impostazioni locali* che consente l'uso di caratteri internazionali in file di input, nomi file e percorsi di directory. Specificare un identificatore delle impostazioni locali decimale.  
  
     Per altre informazioni, vedere l'opzione **/lcid** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche "Locale IDs Assigned by Microsoft" (ID impostazioni locali assegnati da Microsoft) in MSDN.  
  
-   **MkTypLibCompatible**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, è necessario che il formato dei file di input sia compatibile con mktyplib.exe versione 2.03.  
  
     Per altre informazioni, vedere l'opzione **/mktyplib203** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche "ODL File Syntax" (Sintassi dei file ODL) sul sito Web MSDN.  
  
-   **OutputDirectory**  
  
     Parametro **String** facoltativo.  
  
     Specifica la directory predefinita in cui l'attività MIDL scrive i file di output.  
  
     Per altre informazioni, vedere l'opzione **/out** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **PreprocessorDefinitions**  
  
     Parametro **String[]** facoltativo.  
  
     Specifica una o più *definizioni*, ovvero un nome e un valore facoltativo da passare al preprocessore C come in base alla direttiva `#define`. Il formato di ogni definizione è *nome[=valore]*.  
  
     Per altre informazioni, vedere l'opzione **/D** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **UndefinePreprocessorDefinitions** in questa tabella.  
  
-   **ProxyFileName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file proxy di interfaccia per un'interfaccia COM.  
  
     Per altre informazioni, vedere l'opzione **/proxy** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **RedirectOutputAndErrors**  
  
     Parametro **String** facoltativo.  
  
     Reindirizza l'output, ad esempio messaggi di errore e avvisi, dall'output standard al file specificato.  
  
     Per altre informazioni, vedere l'opzione **/o** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **ServerStubFile**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file stub server per un'interfaccia RPC.  
  
     Per altre informazioni, vedere l'opzione **/sstub** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **ClientStubFile** in questa tabella.  
  
-   **Source**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Specifica un elenco dei file di origine separati da spazi.  
  
-   **StructMemberAlignment**  
  
     Parametro **String** facoltativo.  
  
     Specifica l'allineamento (*livello di compressione*) delle strutture nel sistema di destinazione.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**NotSet**|*\<nessuno>*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Per altre informazioni, vedere l'opzione **/Zp** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). L'opzione **/Zp** equivale all'opzione **/pack** e all'opzione **/align** precedente.  
  
-   **SuppressCompilerWarnings**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, elimina i messaggi di avviso dall'attività MIDL.  
  
     Per altre informazioni, vedere l'opzione **/no_warn** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **SuppressStartupBanner**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
     Per altre informazioni, vedere l'opzione **/nologo** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TargetEnvironment**  
  
     Parametro **String** facoltativo.  
  
     Specifica l'ambiente in cui viene eseguita l'applicazione.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**NotSet**|*\<nessuno>*|  
    |**Win32**|**/env win32**|  
    |**Itanium**|**/env ia64**|  
    |**X64**|**/env x64**|  
  
     Per altre informazioni, vedere l'opzione **/env** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TrackerLogDirectory**  
  
     Parametro `String` facoltativo.  
  
     Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.  
  
-   **TypeLibFormat**  
  
     Parametro **String** facoltativo.  
  
     Specifica il formato del file di libreria dei tipi.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Per altre informazioni, vedere le opzioni **/newtlb** e **/oldtlb** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **TypeLibraryName**  
  
     Parametro **String** facoltativo.  
  
     Specifica il nome del file di libreria dei tipi.  
  
     Per altre informazioni, vedere l'opzione **/tlb** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parametro **String[]** facoltativo.  
  
     Rimuove le definizioni precedenti di un nome passando il nome al preprocessore C come in base a una direttiva `#undefine`. Specificare uno o più nomi definiti in precedenza.  
  
     Per altre informazioni, vedere l'opzione **/U** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **PreprocessorDefinitions** in questa tabella.  
  
-   **ValidateAllParameters**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, genera altre informazioni di controllo errore usate per eseguire controlli integrità in fase di esecuzione. Se `false`, le informazioni di controllo errore non vengono generate.  
  
     Per altre informazioni, vedere le opzioni **/robust** e **/no_robust** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **WarnAsError**  
  
     Parametro `Boolean` facoltativo.  
  
     Se `true`, tutti gli avvisi vengono considerati come errori.  
  
     Se il parametro dell'attività MIDL **WarningLevel** non viene specificato, gli avvisi a livello predefinito, ovvero il livello 1, vengono considerati come errori.  
  
     Per altre informazioni, vedere le opzioni **/WX** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **WarningLevel** in questa tabella.  
  
-   **WarningLevel**  
  
     Parametro **String** facoltativo.  
  
     Specifica la gravità (*livello di avviso*) degli avvisi da creare. Per il valore 0 non vengono creati avvisi. Diversamente, viene creato un avviso se il livello di avviso è numericamente inferiore o uguale al valore specificato.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione della riga di comando.  
  
    |Valore|Opzione della riga di comando|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Per altre informazioni, vedere l'opzione **/W** in "MIDL Command-Line Reference" (Riferimenti alla riga di comando di MIDL) nel sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **WarnAsError** in questa tabella.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)