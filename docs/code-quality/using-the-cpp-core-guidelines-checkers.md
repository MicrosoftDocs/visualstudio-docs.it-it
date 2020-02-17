---
title: Uso dei correttori Linee guida di base di C++
ms.date: 08/14/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: 95b3af7db7fc0e4c71d78716714031fd07dbdab5
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271779"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Usare i controlli delle Linee guida di base di C++

Le C++ linee guida di base sono un set portatile di linee guida, regole e procedure consigliate C++ per la C++ scrittura di codice in creato da esperti e designer. Visual Studio supporta attualmente un sottoinsieme di queste regole come parte degli strumenti di analisi del C++codice per. I controlli delle linee guida di base vengono installati per impostazione predefinita in Visual Studio 2017 e Visual Studio 2019 e sono [disponibili come pacchetto NuGet per Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Progetto C++ di linee guida principali

Creato da Bjarne Stroustrup e altre, le C++ linee guida principali sono una guida all'uso C++ moderno in modo sicuro ed efficace. Le linee guida enfatizzano l'indipendenza dai tipi statici e la sicurezza delle risorse. Identificano modi per eliminare o ridurre al minimo la maggior parte delle parti soggette a errori del linguaggio e suggerire come rendere il codice più semplice e più efficiente in modo affidabile. Queste linee guida sono gestite dalla base C++ standard. Per altre informazioni, vedere la documentazione, [ C++ le linee guida di base](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e C++ accedere ai file di progetto della documentazione delle linee guida di base su [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le C++ linee guida per il controllo principale nell'analisi del codice
È possibile abilitare l'analisi del codice nel progetto selezionando la casella di controllo **Abilita analisi codice su compilazione** nella sezione **analisi codice** della finestra di dialogo **pagine delle proprietà** del progetto.

![Pagina delle proprietà per le impostazioni generali dell'analisi codice](media/cppcorecheck_codeanalysis_general.png)

Un sottoinsieme C++ di regole di controllo di base è incluso nel set di regole consigliate nativo Microsoft che viene eseguito per impostazione predefinita quando è abilitata l'analisi del codice. Per abilitare le regole aggiuntive del controllo principale, fare clic sull'elenco a discesa e scegliere i set di regole che si desidera includere:

![Elenco a discesa C++ per set di regole di controllo di base aggiuntivi](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Esempi
Di seguito è riportato un esempio di alcuni dei problemi che C++ le regole di controllo principali possono trovare:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Questo esempio illustra alcuni degli avvisi che possono essere trovati C++ dalle regole di controllo principali:

- C26494 è il tipo di regola. 5: Inizializza sempre un oggetto.

- C26485 è associato alle regole. 3: nessun decadimento da matrice a puntatore.

- C26481 è associato alle regole. 1: non usare l'aritmetica dei puntatori. In alternativa, utilizzare `span`.

Se i C++ set di regole di analisi del codice di base del controllo vengono installati e abilitati quando si compila il codice, i primi due avvisi vengono restituiti, ma il terzo viene eliminato. Ecco l'output di compilazione del codice di esempio:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Le C++ linee guida di base sono disponibili per semplificare la scrittura di codice migliore e sicuro. Tuttavia, se si dispone di un'istanza in cui non è necessario applicare una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile usare l'attributo `gsl::suppress` per impedire C++ al controllo principale di rilevare e segnalare eventuali violazioni di una regola nel blocco di codice seguente. È possibile contrassegnare singole istruzioni per l'eliminazione di regole specifiche. È anche possibile eliminare l'intero profilo dei limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero di regola specifico.

## <a name="supported-rule-sets"></a>Set di regole supportati
Quando vengono aggiunte nuove regole al controllo C++ delle linee guida di base, il numero di avvisi generati per il codice preesistente può aumentare. È possibile utilizzare set di regole predefiniti per filtrare i tipi di regole da abilitare.
Gli argomenti di riferimento per la maggior parte delle regole sono disponibili in [riferimento al controllo principale di Visual C++ Studio](code-analysis-for-cpp-corecheck.md).

A partire da Visual Studio 2017 versione 15,3, i set di regole supportati sono:
- Le **regole del puntatore del proprietario** applicano [i C++ controlli di gestione risorse correlati al proprietario\<t > dalle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Le **regole const** applicano [controlli correlati a C++ const delle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- Le **regole del puntatore non elaborato** applicano [i C++ controlli di gestione risorse correlati a puntatori non elaborati delle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Le **regole univoche del puntatore** applicano [ C++ i controlli di gestione delle risorse correlati ai tipi con semantica dei puntatori univoca dalle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Le **regole dei limiti** applicano il [profilo dei limiti C++ delle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- Le **regole di tipo** applicano il [profilo C++ dei tipi delle linee guida di base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 versione 15.5**:

- **Regole di classe** Alcune regole si concentrano sull'utilizzo corretto di funzioni membro speciali e specifiche virtuali. Si tratta di un subset di controlli consigliati per [le classi e le gerarchie di classi](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Regole di concorrenza** Una singola regola, che rileva gli oggetti Guard dichiarati in modo errato. Per altre informazioni, vedere [linee guida correlate alla concorrenza](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Regole di dichiarazione** Un paio di regole delle [linee guida sulle interfacce](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) che riguardano il modo in cui vengono dichiarate le variabili globali.
- **Regole delle funzioni** Due controlli che consentono di adottare l'identificatore `noexcept`. Questa è una parte delle linee guida per la [progettazione e l'implementazione di funzioni chiare](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Regole del puntatore condiviso** Come parte dell'applicazione delle linee guida per la [gestione delle risorse](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) , sono state aggiunte alcune regole specifiche per il modo in cui i puntatori condivisi vengono passati alle funzioni o utilizzati localmente.
- **Regole di stile** Un controllo semplice ma importante, che impedisce l'uso di [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Questo è il primo passaggio per migliorare lo stile di codifica e l'utilizzo di espressioni e C++istruzioni in.

**Visual Studio 2017 versione 15.6**:

- **Regole aritmetiche** Regole per rilevare l' [overflow](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)aritmetico, [le operazioni senza](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) firma e la [manipolazione di bit](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

È possibile scegliere di limitare gli avvisi solo a uno o pochi gruppi. I set di regole **native minime** e **native consigliate** includono C++ regole di controllo principali oltre ad altri controlli preveloci. Per visualizzare i set di regole disponibili, aprire la finestra di dialogo delle proprietà del progetto, selezionare **codice Analysis\General**, aprire l'elenco a discesa nella casella combinata **set di regole** e scegliere **Scegli più set di regole**. Per altre informazioni sull'uso dei set di regole in Visual Studio, vedere [uso di set di regole per raggruppare regole di analisi del codice](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macro

Il C++ controllo delle linee guida di base viene visualizzato con un file di intestazione che definisce le macro che semplificano l'eliminazione di intere categorie di avvisi nel codice:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Queste macro corrispondono ai set di regole e si espandono in un elenco separato da spazi di numeri di avviso. Usando i costrutti pragma appropriati, è possibile configurare il set di regole valido interessante per un progetto o una sezione di codice. Nell'esempio seguente l'analisi del codice avverte solo i modificatori costanti mancanti:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributi

Il compilatore C++ Microsoft dispone di un supporto limitato per l'attributo di eliminazione GSL. Può essere usato per disattivare gli avvisi sulle istruzioni Expression e Block all'interno di una funzione.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Elimina analisi tramite opzioni della riga di comando

Invece di #pragmas, è possibile utilizzare le opzioni della riga di comando nella pagina delle proprietà del file per non visualizzare gli avvisi relativi a un progetto o a un singolo file. Ad esempio, per disabilitare l'avviso 26400 per un file:

1. Fare clic con il pulsante destro del mouse sul file in **Esplora soluzioni**

2. Scegliere le **Proprietà | C/C++| Riga di comando**

3. Nella finestra **Opzioni aggiuntive** aggiungere `/wd26400`.

È possibile utilizzare l'opzione della riga di comando per disabilitare temporaneamente tutte le analisi del codice per un file specificando `/analyze-`. Viene generato un avviso *D9025 che esegue l'override di '/analyze ' con '/analyze-'* , che ricorda di riabilitare l'analisi del codice in un secondo momento.

## <a name="corecheck_per_file"></a>Abilitare il C++ controllo delle linee guida di base su file di progetto specifici

Talvolta può essere utile eseguire analisi del codice mirate e continuare a usare l'IDE di Visual Studio. Lo scenario di esempio seguente può essere usato per i progetti di grandi dimensioni per risparmiare tempo di compilazione e per semplificare la filtrazione dei risultati:

1. Nella shell dei comandi impostare le variabili di ambiente `esp.extension` e `esp.annotationbuildlevel`.
2. Per ereditare queste variabili, aprire Visual Studio dalla shell dei comandi.
3. Caricare il progetto e aprirne le proprietà.
4. Abilitare l'analisi del codice, selezionare i set di regole appropriati, ma non abilitare le estensioni dell'analisi codice.
5. Passare al file che si vuole analizzare con il controllo C++ delle linee guida di base e aprirne le proprietà.
6. Scegliere **Opzioni rigaC++C/\command** e Aggiungi `/analyze:plugin EspXEngine.dll`
7. Disabilitare l'utilizzo dell'intestazione precompilata (**intestazioni CC++/\Precompiled**). Questa operazione è necessaria perché il motore delle estensioni può tentare di leggere le informazioni interne dall'intestazione precompilata (PCH); Se il PCH compilato con le opzioni del progetto predefinite, non sarà compatibile.
8. Ricompilare il progetto. I controlli prerapidi comuni devono essere eseguiti in tutti i file. Poiché il C++ controllo delle linee guida di base non è abilitato per impostazione predefinita, deve essere eseguito solo nel file configurato per usarlo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Come usare il controllo C++ delle linee guida di base all'esterno di Visual Studio

È possibile usare le C++ linee guida principali controlli nelle compilazioni automatiche.

### <a name="msbuild"></a>MSBuild
Il controllo dell'analisi del codice nativo (PREfast) è integrato nell'ambiente MSBuild dai file di destinazioni personalizzate. Per abilitarla, è possibile usare le proprietà del progetto e C++ aggiungere il controllo delle linee guida di base (basato su PREfast):

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Assicurarsi di aggiungere queste proprietà prima dell'importazione del file Microsoft. cpp. targets. È possibile scegliere set di regole specifici o creare un set di regole personalizzate oppure utilizzare il set di regole predefinito che include altri controlli preveloci.

È possibile eseguire il C++ controllo principale solo nei file specificati usando lo stesso approccio descritto in [precedenza](#corecheck_per_file), ma usando i file MSBuild. Le variabili di ambiente possono essere impostate tramite l'elemento `BuildMacro`:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Se non si vuole modificare il file di progetto, è possibile passare le proprietà nella riga di comando:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Progetti non MSBuild

Se si usa un sistema di compilazione che non si basa su MSBuild, è ancora possibile eseguire il controllo, ma è necessario acquisire familiarità con alcuni elementi interni della configurazione del motore di analisi del codice. Questi elementi interni non saranno necessariamente supportati in futuro.

È necessario impostare alcune variabili di ambiente e usare le opzioni della riga di comando appropriate per il compilatore. È preferibile usare l'ambiente "prompt dei comandi degli strumenti nativi", in modo da non dover cercare percorsi specifici per il compilatore, includere directory e così via.

1. **Variabili di ambiente**
   - `set esp.extensions=cppcorecheck.dll` indica al motore di caricare il modulo C++ delle linee guida di base.
   - `set esp.annotationbuildlevel=ignore` Disabilita la logica che elabora le annotazioni SAL. Le annotazioni non influiscono sull' C++ analisi del codice nel controllo delle linee guida di base, ma la loro elaborazione richiede tempo (a volte molto tempo). Questa impostazione è facoltativa, ma altamente consigliata.
   - `set caexcludepath=%include%` si consiglia di disabilitare gli avvisi generati sulle intestazioni standard. È possibile aggiungere altri percorsi, ad esempio il percorso delle intestazioni comuni nel progetto.
2. **Opzioni della riga di comando**
   - `/analyze` Abilita l'analisi del codice (si consiglia anche di usare/analyze: only e/analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` questa opzione carica il motore delle estensioni di analisi del codice in PREfast. Questo motore, a sua volta, carica C++ il controllo delle linee guida di base.

## <a name="use-the-guideline-support-library"></a>Usare la libreria di supporto per le linee guida
La libreria del supporto per le linee guida è stata progettata per consentire di seguire le linee guida di base. Il GSL include definizioni che consentono di sostituire costrutti soggetti a errori con alternative più sicure. È ad esempio possibile sostituire un `T*, length` coppia di parametri con il tipo di `span<T>`. GSL è disponibile in [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). La libreria è open source ed è quindi possibile visualizzare le origini, creare commenti o contribuire. Il progetto è disponibile in [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Usare le C++ linee guida per il controllo principale nei progetti di Visual Studio 2015

Se si usa Visual Studio 2015, i C++ set di regole di analisi del codice di base non sono installati per impostazione predefinita. È necessario eseguire alcuni passaggi aggiuntivi prima di poter abilitare gli C++ strumenti di analisi del codice per il controllo principale in Visual Studio 2015. Microsoft fornisce supporto per i progetti Visual Studio 2015 usando un pacchetto NuGet. Il pacchetto è denominato Microsoft. CppCoreCheck ed è disponibile in [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Per questo pacchetto è necessario avere almeno Visual Studio 2015 con Update 1 installato.

Il pacchetto installa anche un altro pacchetto come dipendenza, una libreria di supporto per le linee guida solo intestazione (GSL). GSL è disponibile anche in GitHub all' [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

A causa del modo in cui vengono caricate le regole di analisi del codice, è necessario installare il pacchetto NuGet C++ Microsoft. CppCoreCheck in ogni progetto che si vuole controllare in Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Per aggiungere il pacchetto Microsoft. CppCoreCheck al progetto in Visual Studio 2015

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione a cui si desidera aggiungere il pacchetto. Scegliere **Gestisci pacchetti NuGet** per aprire **Gestione pacchetti NuGet**.

2. Nella finestra **Gestione pacchetti NuGet** cercare Microsoft. CppCoreCheck.

    ![Finestra di gestione pacchetti NuGet che mostra il pacchetto CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Selezionare il pacchetto Microsoft. CppCoreCheck, quindi scegliere il pulsante **Installa** per aggiungere le regole al progetto.

   Il pacchetto NuGet aggiunge un file MSBuild *. targets* aggiuntivo al progetto che viene richiamato quando si Abilita l'analisi del codice nel progetto. Questo file con estensione *targets* aggiunge le C++ regole di controllo di base come estensione aggiuntiva allo strumento di analisi del codice di Visual Studio. Quando si installa il pacchetto, è possibile utilizzare la finestra di dialogo Pagine delle proprietà per abilitare o disabilitare le regole rilasciate e sperimentali.

## <a name="see-also"></a>Vedere anche

- [Informazioni di C++ riferimento sul controllo principale di Visual Studio](code-analysis-for-cpp-corecheck.md)
