---
title: Opzioni della riga di comando devenv in Visual Studio | Microsoft Docs
ms.date: 02/28/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3adde520b76de347da025c819ec39dce50660f2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="devenv-command-line-switches"></a>Opzioni della riga di comando devenv

La riga di comando devenv consente di impostare varie opzioni per l'ambiente di sviluppo integrato (IDE, Integrated Development Environment) e di compilare, eseguire il debug e distribuire i progetti dalla riga di comando. Usare queste opzioni per eseguire l'IDE da uno script o un file con estensione bat, ad esempio uno script di compilazione notturna, o per avviare l'IDE in una configurazione particolare.

> [!NOTE]
> Per le attività relative alla compilazione, è consigliabile usare MSBuild anziché devenv. Per altre informazioni, vedere [Riferimenti alla riga di comando di MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Sintassi delle opzioni devenv

Per impostazione predefinita, i comandi devenv passano le opzioni all'utilità devenv.com. L'utilità devenv.com restituisce output tramite flussi di sistema standard, ad esempio `stdout` e `stderr`. L'utilità determina il reindirizzamento I/O appropriato durante l'acquisizione dell'output, ad esempio in un file con estensione txt.

D'altra parte, i comandi che iniziano con `devenv.exe` possono usare le stesse opzioni, ma l'utilità devenv.com viene ignorata.

Le regole di sintassi per le opzioni `devenv` sono simili a quelle di altre utilità della riga di comando DOS. Le regole di sintassi seguenti si applicano a tutte le opzioni `devenv` e ai relativi argomenti:

- I comandi iniziano con `devenv`.

- Le opzioni non distinguono tra maiuscole e minuscole.

- Quando si specifica una soluzione o un progetto, il primo argomento è il nome del file di soluzione o file di progetto, incluso il percorso del file.

- Se il primo argomento è un file che non è una soluzione o un progetto, tale file viene aperto nell'editor appropriato, in una nuova istanza dell'IDE.

- Quando si specifica un nome di file di progetto anziché un nome di file di soluzione, un comando `devenv` cerca nella cartella padre del file di progetto un file di soluzione con lo stesso nome. Ad esempio, il comando `devenv /build myproject1.vbproj` cerca nella cartella padre un file di soluzione denominato "myproject1.sln".

    > [!NOTE]
    > Nella cartella padre deve trovarsi un solo e unico file che faccia riferimento a questo progetto. Se la cartella padre non contiene alcun file di soluzione che fa riferimento a questo progetto, o se la cartella padre contiene due o più file di soluzione che vi fanno riferimento, viene creato un file di soluzione temporaneo.

- Quando i percorsi e i nomi dei file contengono spazi, è necessario racchiuderli tra virgolette (""). Ad esempio, "c:\progetto a\\".

- Inserire uno spazio tra le opzioni e gli argomenti sulla stessa riga. Ad esempio, il comando **devenv /log output.txt** apre l'IDE e restituisce tutte le informazioni di registro per la sessione di output.txt.

- Nei comandi `devenv` non può essere usata la sintassi di corrispondenza dei modelli.

## <a name="devenv-switches"></a>Opzioni devenv

Le opzioni della riga di comando seguenti consentono di visualizzare l'IDE ed eseguire l'attività descritta.

|Switch della riga di comando|Descrizione|
|-------------------------|-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Avvia l'IDE ed esegue il comando specificato.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Carica un eseguibile C++ sotto il controllo del debugger. Questa opzione non è disponibile per gli eseguibili Visual Basic o C#. Per altre informazioni, vedere [Automatically start a process in the debugger](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger) (Avviare automaticamente un processo nel debugger).|
|[/LCID or /l](../../ide/reference/lcid-devenv-exe.md)|Imposta la lingua predefinita per l'IDE. Se la lingua specificata non è inclusa nell'installazione di Visual Studio, questa impostazione viene ignorata.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Avvia Visual Studio e registra tutte le attività nel file di registro.|
|[/Run or /r](../../ide/reference/run-devenv-exe.md)|Compila ed esegue la soluzione specificata.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Compila ed esegue la soluzione specificata, riduce a icona l'IDE quando la soluzione viene eseguita e chiude l'IDE al termine dell'esecuzione della soluzione.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Fa sì che l'IDE usi le variabili di ambiente PATH, INCLUDE e LIB per la compilazione C++ anziché le impostazioni specificate nella sezione Directory di VC++ delle opzioni **Progetti** nella finestra di dialogo **Opzioni**. Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per altre informazioni, vedere [Impostare le variabili di percorso e di ambiente per le compilazioni da riga di comando](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Apre i file specificati in un'istanza dell'applicazione in esecuzione. Se non sono presenti istanze in esecuzione, viene avviata una nuova istanza con un layout di finestra semplificato.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Avvia Visual Studio in modalità sicura, caricando solo l'ambiente e i servizi predefiniti e le versioni acquistate dei pacchetti di terze parti.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Cancella tutti i tag SkipLoading aggiunti ai VSPackage da utenti che non vogliono caricare i VSPackage.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Forza Visual Studio in modo che esegua il merge dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i VSPackage disponibili. È necessario eseguire questo comando come amministratore.|

Le opzioni della riga di comando seguenti non visualizzano l'IDE.

|Switch della riga di comando|Descrizione|
|-------------------------|-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Visualizza la guida per le opzioni devenv nella **finestra del prompt dei comandi**.<br /><br /> **Devenv /?**|
|[/Build](../../ide/reference/build-devenv-exe.md)|Compila la soluzione o il progetto specificati in base alla configurazione relativa.<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Elimina i file creati dal comando di compilazione, senza che ciò abbia effetto sui file di origine.<br /><br /> **Devenv myproj.csproj /clean**|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Compila la soluzione, in base alla configurazione relativa, insieme ai file necessari per la distribuzione.<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|Confronta due file. Accetta quattro parametri, ovvero SourceFile, TargetFile, SourceDisplayName (facoltativo), TargetDisplayName (facoltativo).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Consente di specificare un file per la ricezione di errori durante la compilazione.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project](../../ide/reference/project-devenv-exe.md)|Il progetto da compilare, pulire o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione /build, /rebuild, /clean o /deploy.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Specifica la configurazione del progetto da compilare o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione /project.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Pulisce e compila la soluzione o il progetto specificati in base alla configurazione relativa.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Ripristina impostazioni predefinite di Visual Studio. Facoltativamente reimposta le impostazioni per il file con estensione vssettings specificato.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Aggiorna il file di soluzione specificato e tutti i file di progetto relativi, o il file di progetto specificato, nei formati Visual Studio correnti per tali file.|

## <a name="see-also"></a>Vedere anche

* [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)