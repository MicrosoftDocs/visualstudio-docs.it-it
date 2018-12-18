---
title: Utilizzando i controlli della linee guida di base C++ | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
dev_langs:
- CPP
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 97ada4fa2abd8975bd728b48fc24b9e3e9e2af41
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="using-the-c-core-guidelines-checkers"></a>Utilizzando i controlli della linee guida di base di C++
Le linee guida componenti di base di C++ sono un set portabile di linee guida, regole e procedure consigliate sulla codifica in C++ creati dai progettisti e gli esperti di C++. Visual Studio supporta attualmente un sottoinsieme di queste regole come parte dei relativi strumenti di analisi codice per C++. Correttori ortografici delle linee guida per i componenti di base vengono installati per impostazione predefinita in Visual Studio 2017 e sono [disponibile come pacchetto NuGet per Visual Studio 2015](#vs2015_corecheck).
  
## <a name="the-c-core-guidelines-project"></a>Il progetto di base C++ linee guida  
 Creato da Bjarne Stroustrup e altri, le linee guida componenti di base di C++ sono una Guida all'utilizzo di C++ moderno in modo sicuro ed efficiente. Le linee guida evidenziare l'indipendenza dai tipi statici e sicurezza di risorse. Le classi identificare modi per eliminare o ridurre al minimo le parti più soggetto a errori del linguaggio e suggerisce come rendere il codice più semplice e più efficiente in modo affidabile. Queste linee guida vengono mantenute per la base di C++ Standard. Per ulteriori informazioni, vedere la documentazione, [linee guida di base C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e accedere ai file di progetto di documentazione di linee guida di base di C++ in [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le linee guida C++ Core controllare nell'analisi del codice  
 È possibile abilitare l'analisi del codice del progetto selezionando il **Attiva analisi codice in fase di compilazione** nella casella di controllo di **analisi del codice** sezione del **pagine delle proprietà** finestra di dialogo per il progetto.  
  
 ![Pagina delle proprietà per le impostazioni generali di analisi codice](../code-quality/media/cppcorecheck_codeanalysis_general.png "CPPCoreCheck_CodeAnalysis_General")  
  
 Le regole di controllo di base C++ sono estensioni per il set di regole predefinite che eseguono quando è abilitata l'analisi del codice. Poiché le regole di controllo di base C++ sono in fase di sviluppo, alcune regole sono ben definite e alcuni, ma potrebbe non essere pronto per l'uso in tutto il codice, potrebbe essere informativi. Le regole sono suddivise in due gruppi: è stato rilasciato e sperimentale. È possibile scegliere se eseguire le regole rilasciate o sperimentale nelle proprietà del progetto.  
  
 ![Pagina delle proprietà per le impostazioni di estensioni di analisi codice](../code-quality/media/cppcorecheck_codeanalysis_extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
 Per abilitare o disabilitare i set di regole C++ Core verificare, aprire il **pagine delle proprietà** finestra di dialogo per il progetto. In **le proprietà di configurazione**, espandere **analisi del codice**, **estensioni**. Nell'elenco a discesa accanto al controllo **abilitare C++ Core controllare (rilasciato)** o **abilitare C++ Core controllare (sperimentale)**, scegliere **Sì** o **n**. Scegliere **OK** o **applica** per salvare le modifiche.  
  
## <a name="examples"></a>Esempi  
 Di seguito è riportato un esempio di alcuni dei problemi in grado di trovare le regole di controllo di base C++:  
  
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
  
 Questo esempio illustra alcuni degli avvisi in grado di trovare le regole di controllo di base C++:  
  
-   C26494 è regola Type.5: sempre inizializzare un oggetto.  
  
-   C26485 è regola Bounds.3: nessun decadimento a puntatore, matrice.  
  
-   C26481 è regola Bounds.1: non utilizzare l'aritmetica dei puntatori. In alternativa, usare `span`.  
  
 Se il ruleSet di analisi codice C++ Core controllare installato e abilitato quando si compila questo codice, i primi due avvisi vengono visualizzati, ma il terzo viene eliminato. Di seguito è riportato l'output di compilazione del codice di esempio:  
  
```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------  
1>  CoreCheckExample.cpp  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)  
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
```  
  
Le linee guida componenti di base di C++ sono presenti consentono di scrivere codice migliore e più sicuro. Tuttavia, se si dispone di un'istanza in cui non deve essere applicato una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile utilizzare il `gsl::suppress` attributo per evitare C++ Core controllare il rilevamento e segnalazione qualsiasi violazione di una regola nel blocco di codice seguente. È possibile contrassegnare singole istruzioni per eliminare le regole specifiche. È anche possibile eliminare l'intero profilo limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero specifico di regola.  

## <a name="supported-rule-sets"></a>Set di regole è supportato
Come vengono aggiunte nuove regole per il controllo di linee guida di base C++, è possibile aumentare il numero di avvisi generati per il codice esistente. È possibile utilizzare i set di regole predefiniti per filtrare i tipi di regole da abilitare. Argomenti di riferimento per la maggior parte delle regole sono in [C++ Core controllare riferimenti di Visual Studio](code-analysis-for-cpp-corecheck.md).

A partire da Visual Studio 2017 versione 15.3, i set di regole supportati sono: 
  - **Le regole di puntatore proprietario** applicare [gestione delle risorse di controlli correlati al proprietario<T> dalle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regole const** applicare [controlli correlati const dalle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).  

  - **Le regole di puntatore non elaborato** applicare [gestione delle risorse Controlla puntatori correlati a non elaborato dalle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Le regole di puntatore univoco** applicare [verifica di gestione delle risorse relative ai tipi con la semantica di puntatore univoco dalle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Delimita regole** imporre la [delimita profilo delle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Regole di tipo** imporre la [digitare profilo delle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

  **Visual Studio 2017 versione 15.5**:
  - **Classe di regole** alcune regole incentrate su corretto utilizzo di metodi speciali e virtuali specifiche. Questo è un subset di controlli consigliati per [classi e le gerarchie di classi](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class). 
  - **Regole di concorrenza** una singola regola che rileva gli oggetti dichiarati in modo errato guard. Per ulteriori informazioni, vedere [linee guida relative alla concorrenza](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency). 
  - **Regole della dichiarazione** un paio di regole di [interfacce linee guida](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) quali lo stato attivo sulle variabili globali vengono dichiarati.  
  - **Funzione regole** due controlli che consentono di adozione del `noexcept` identificatore. Questa è una parte delle linee guida per [deselezionare funzione progettazione e implementazione](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions). 
  - **Regole di puntatore condiviso** come parte di [la gestione delle risorse](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) imposizione delle linee guida, abbiamo aggiunto alcune regole specifiche per i puntatori condivisi vengono passate in funzioni o utilizzate in locale.  
  - **Le regole di stile** un controllo semplice, ma importante che esclude l'utilizzo di [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Questo è il primo passaggio per il miglioramento del codice di stile e l'utilizzo di espressioni e istruzioni di C++.  
  
  **Visual Studio 2017 versione 15.6**:
  - **Regole aritmetiche** regole per rilevare l'aritmetica [overflow](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [operazioni unsigned firmato](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) e [bit manipolazione](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).


 È possibile scegliere di limitare gli avvisi per uno o alcuni dei gruppi. Il **minimo Native** e **consigliato Native** regola imposta include regole di controllo di base C++ oltre agli altri controlli di PREfast. Per visualizzare il disponibili set di regole, aprire la finestra di dialogo proprietà del progetto, selezionare **codice Analysis\General**, aprire l'elenco a discesa nel **set di regole** casella combinata e selezione **scegliere più set di regole** . Per ulteriori informazioni sull'utilizzo di set di regole in Visual Studio, vedere [utilizzando il set di regole per raggruppare regole di analisi codice](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macro
 Il controllo di linee guida di base C++ viene fornito con un file di intestazione che definisce le macro che semplificano l'esclusione di intere categorie di avvisi nel codice:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Queste macro corrispondono al set di regole ed espandono in un elenco separato da spazi di numeri di avviso. Usando i costrutti di pragma appropriato, è possibile configurare il set di regole valido interessante per un progetto o una sezione di codice. Nell'esempio seguente, l'analisi del codice avvisa solo modificatori di costanti mancante:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributi
 Il compilatore Microsoft Visual C++ ha un supporto limitato per il GSL esclusione di attributo. E può essere utilizzato per eliminare gli avvisi in espressioni e istruzioni di blocco all'interno di una funzione.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Soppressione dei messaggi di analisi utilizzando le opzioni della riga di comando
 Anziché #pragmas, è possibile utilizzare le opzioni della riga di comando nella pagina delle proprietà del file per l'esclusione di avvisi per un progetto o un singolo file. Ad esempio, per disabilitare l'avviso 26400 per un file:
 
 1) Il file in **Esplora soluzioni**

 2) Scegliere **proprietà | C / C++ | Riga di comando**

 3) Nel **opzioni aggiuntive** finestra Aggiungi `/wd26400`.

 È possibile utilizzare l'opzione della riga di comando per disabilitare temporaneamente tutte le analisi del codice per un file specificando `/analyze-`. Viene prodotto un avviso *D9025 override '/ANALYZE' con ' /ANALYZE -'*, ricordare di abilitare di nuovo l'analisi del codice in un secondo momento.

 ## <a name="corecheck_per_file"></a>Abilitare il controllo di linee guida Core C++ nel file di progetto specifico
In alcuni casi può essere utile per l'analisi del codice con stato attivo, continuando a utilizzare l'IDE di Visual Studio. Per risparmiare tempo di compilazione e per renderne più semplice per i risultati del filtro, è possibile utilizzare lo scenario di esempio seguente per progetti di grandi dimensioni:

1.  Nella shell dei comandi impostare la `esp.extension` e `esp.annotationbuildlevel` le variabili di ambiente.
2.  Per ereditare queste variabili, avviare Visual Studio dalla shell dei comandi. 
3.  Caricare il progetto e aprirne le relative proprietà.
4.  Abilita analisi codice, selezionare i set di regole appropriate, ma non abilita le estensioni di analisi codice.
5.  Passare al file di cui che si desidera analizzare con il controllo di linee guida di base C++ e aprirne le relative proprietà.
6.  Scegliere **C / C++ \Command opzioni della riga di** e aggiungere`/analyze:plugin EspXEngine.dll`
7.  Disabilitare l'uso dell'intestazione precompilata (**C / C++ \Precompiled intestazioni**). Ciò è necessario perché il motore di estensioni può tentare di leggere informazioni interne dall'intestazione precompilata (PCH); Se il file PCH compilato con le opzioni di progetto predefinite, non sarà compatibile.
8.  Ricompilare il progetto. I controlli di PREFast comuni deve essere eseguito su tutti i file. Poiché il controllo di linee guida di base C++ non è abilitato per impostazione predefinita, deve essere eseguito solo sul file che è configurato per utilizzarla.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Come utilizzare il controllo di linee guida di base C++ all'esterno di Visual Studio
È possibile utilizzare i controlli di linee guida di base C++ nelle compilazioni automatiche.

### <a name="msbuild"></a>MSBuild
 Il controllo di analisi del codice nativo (PREfast) è integrato nell'ambiente di MSBuild dai file di destinazioni personalizzate. È possibile utilizzare le proprietà del progetto per attivarla e aggiungere il controllo di linee guida di base C++ (che è basato su PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Assicurarsi di aggiungere queste proprietà prima di importare il file Microsoft.Cpp.targets. È possibile selezionare i set di regole specifiche o creare un set di regole personalizzate o usare il set di regole predefinite che include altri controlli PREfast.

È possibile eseguire il controllo di base C++ solo nei file specificati utilizzando lo stesso approccio come [descritto in precedenza](#corecheck_per_file), ma l'utilizzo di file MSBuild. Per impostare le variabili di ambiente, è possono utilizzare il `BuildMacro` elemento:

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

Se non si desidera modificare il file di progetto, è possibile passare le proprietà della riga di comando:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Progetti non MSBuild
Se si utilizza un sistema di compilazione che non si basa su MSBuild è comunque possibile eseguire il controllo, ma è necessario acquisire familiarità con alcuni elementi interni della configurazione del motore di analisi del codice. Questi elementi interni non sono garantiti devono essere supportati in futuro.

È necessario impostare alcune variabili di ambiente e utilizzare le opzioni della riga di comando appropriate per il compilatore. È preferibile utilizzare nell'ambiente di "strumenti prompt dei comandi nativi" in modo che non è necessario eseguire la ricerca di percorsi specifici per il compilatore, includere le directory e così via.

1.  **Variabili di ambiente**
  - `set esp.extensions=cppcorecheck.dll`Ciò indica al motore di caricare il modulo di linee guida di base di C++.
  - `set esp.annotationbuildlevel=ignore`Disabilita la logica che elabora le annotazioni SAL. Le annotazioni non influiscono sull'analisi del codice nel controllo di linee guida di base C++, ma l'elaborazione richiede tempo (talvolta ora estesa). Questa impostazione è facoltativo ma consigliato.
  - `set caexcludepath=%include%`Si consiglia di disabilitare gli avvisi che attivano le intestazioni standard. È possibile aggiungere altri percorsi, ad esempio il percorso per le intestazioni comuni nel progetto.
2.  **Opzioni della riga di comando**
  - `/analyze`Abilita l'analisi del codice (è consigliabile utilizzare anche /analyze: solo e /analyze: quiet).
  - `/analyze:plugin EspXEngine.dll`Questa opzione Carica il motore di estensioni di analisi codice di PREfast. Questo motore, a sua volta, carica il controllo di linee guida di base C++.



## <a name="use-the-guideline-support-library"></a>Utilizzare la libreria di supporto delle linee guida  
 La libreria di supporto delle linee guida consentono di seguire le linee guida di base. Il GSL include le definizioni che consentono di sostituire i costrutti soggetta a errori con alternative più sicure. Ad esempio, è possibile sostituire un `T*, length` coppia di parametri con il `span<T>` tipo. È disponibile all'indirizzo di GSL [http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl). La libreria è open source, pertanto è possibile visualizzare le origini, commenti o collaborazione. Il progetto è reperibile in [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a>Utilizzare le linee guida C++ Core controllare nei progetti di Visual Studio 2015  
  Se si utilizza Visual Studio 2015, il set di regole analisi codice controllare Core C++ non sono installati per impostazione predefinita. È necessario eseguire alcuni passaggi aggiuntivi prima di poter attivare strumenti di analisi codice controllare Core C++ in Visual Studio 2015. Microsoft fornisce il supporto per i progetti di Visual Studio 2015 con un pacchetto Nuget. Il pacchetto viene denominato Microsoft.CppCoreCheck ed è disponibile all'indirizzo [http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Questo pacchetto richiede che almeno Visual Studio è 2015 con Update 1 installato.  
  
 Il pacchetto viene installato anche un altro pacchetto come una dipendenza, una sola intestazione delle linee guida per il supporto della libreria (GSL). Il GSL è disponibile anche in GitHub all'indirizzo [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  

 A causa della modalità che vengono caricate le regole di analisi codice, è necessario installare il pacchetto Microsoft.CppCoreCheck NuGet in ogni progetto di C++ che si desidera controllare all'interno di Visual Studio 2015.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Per aggiungere il pacchetto Microsoft.CppCoreCheck al progetto in Visual Studio 2015  
  
1.  In **Esplora**, pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione che si desidera aggiungere il pacchetto. Scegliere **Gestisci pacchetti NuGet** per aprire la **Gestione pacchetti NuGet**.  
  
2.  Nel **Gestione pacchetti NuGet** finestra, cercare Microsoft.CppCoreCheck.  
  
     ![Finestra di gestione pacchetti NuGet Visualizza pacchetto CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.PNG "CPPCoreCheck_Nuget_Window")  
  
3.  Selezionare il pacchetto Microsoft.CppCoreCheck e quindi scegliere il **installare** pulsante per aggiungere le regole per il progetto.  
  
 Il pacchetto NuGet aggiunge un'aggiuntive per MSBuild *targets* file al progetto che viene richiamato quando si abilita l'analisi del codice del progetto. Questo *targets* file aggiunge le regole di controllo di base C++ come un'estensione aggiuntiva allo strumento di analisi del codice di Visual Studio. Quando viene installato il pacchetto, è possibile utilizzare la finestra di dialogo Pagine delle proprietà per abilitare o disabilitare le regole è state rilasciate e sperimentale.  

## <a name="see-also"></a>Vedere anche
[Riferimenti di Visual Studio C++ Core controllo](code-analysis-for-cpp-corecheck.md).
  
