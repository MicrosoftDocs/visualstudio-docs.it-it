---
title: Opzioni della riga di comando devenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f06722f4a6192323d92ce6828b25bc57666de8bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="devenv-command-line-switches"></a>Opzioni della riga di comando devenv
La riga di comando devenv consente di impostare varie opzioni per l'ambiente di sviluppo integrato (IDE, Integrated Development Environment) e di compilare, eseguire il debug e distribuire i progetti dalla riga di comando. Usare queste opzioni per eseguire l'IDE da uno script o un file con estensione bat, ad esempio uno script di compilazione notturna, o per avviare l'IDE in una configurazione particolare.  
  
> [!NOTE]
>  Per le attività relative alla compilazione, è ora consigliabile usare MSBuild anziché devenv. Per altre informazioni, vedere [Command-Line Reference](../../msbuild/msbuild-command-line-reference.md) (Informazioni di riferimento sulla riga di comando).  
  
> [!NOTE]
>  Per poter usare le opzioni [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) è necessario eseguire devenv come amministratore.  
  
## <a name="devenv-switch-syntax"></a>Sintassi delle opzioni devenv  
 Per impostazione predefinita, i comandi devenv passano le opzioni all'utilità devenv.com.  
  
 L'utilità devenv.com recapita l'output tramite flussi di sistema standard, ad esempio `stdout` e `stderr`, e determina il reindirizzamento I/O appropriato durante l'acquisizione dell'output, ad esempio, in un file con estensione txt. I comandi che iniziano con `devenv.exe` possono usare le stesse opzioni, ma saranno inviati al programma devenv.exe, ignorando l'utilità devenv.com.  
  
 Le regole di sintassi per le opzioni `devenv` sono simili a quelle di altre utilità della riga di comando DOS. Le regole di sintassi seguenti si applicano a tutte le opzioni `devenv` e ai relativi argomenti:  
  
-   I comandi iniziano con `devenv`.  
  
-   Le opzioni non distinguono tra maiuscole e minuscole.  
  
-   Quando si specifica una soluzione o un progetto, il primo argomento è il nome del file di soluzione o file di progetto, incluso il percorso del file.  
  
-   Se il primo argomento è un file che non è una soluzione o un progetto, tale file verrà aperto nell'editor appropriato, in una nuova istanza dell'IDE.  
  
-   Quando si specifica un nome di file di progetto anziché un nome di file di soluzione, un comando `devenv` cercherà nella cartella padre del file di progetto un file di soluzione con lo stesso nome. Ad esempio, il comando `devenv /build myproject1.vbproj` cercherà nella cartella padre un file di soluzione denominato "myproject1.sln".  
  
    > [!NOTE]
    >  Nella cartella padre deve trovarsi un solo e unico file che faccia riferimento a questo progetto. Se la cartella padre non contiene alcun file di soluzione che fa riferimento a questo progetto, o se la cartella padre contiene due o più file di soluzione che vi fanno riferimento, verrà creato un file di soluzione temporaneo, denominato per questo progetto e che vi fa riferimento.  
  
-   Quando i percorsi e i nomi dei file contengono spazi, è necessario racchiuderli tra virgolette doppie (""). Ad esempio, "c:\progetto a\\".  
  
-   Inserire uno spazio tra le opzioni e gli argomenti sulla stessa riga. Ad esempio, il comando **devenv /log output.txt** apre l'IDE e restituisce tutte le informazioni di registro per la sessione di output.txt.  
  
-   Nei comandi `devenv` non può essere usata la sintassi di corrispondenza dei modelli.  
  
## <a name="devenv-switches"></a>Opzioni devenv  
 Usare le opzioni della riga di comando seguenti per visualizzare l'IDE ed eseguire l'attività descritta.  
  
|Switch della riga di comando|Descrizione|  
|-------------------------|-----------------|  
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Avvia l'IDE ed esegue il comando specificato.|  
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Carica un eseguibile [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] sotto il controllo del debugger. Questa opzione non è disponibile per gli eseguibili [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Per altre informazioni, vedere [Automatically start a process in the debugger](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger) (Avviare automaticamente un processo nel debugger).|  
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) o `/l`|Imposta la lingua predefinita per l'IDE. Se la lingua specificata non è inclusa nell'installazione di Visual Studio, questa impostazione viene ignorata.|  
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e registra tutte le attività nel file di registro.|  
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) o `/r`|Compila ed esegue la soluzione specificata.|  
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Compila ed esegue la soluzione specificata, riduce a icona l'IDE quando la soluzione viene eseguita e chiude l'IDE al termine dell'esecuzione della soluzione.|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Fa sì che l'IDE usi le variabili di ambiente PATH, INCLUDE e LIB per la compilazione [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] anziché le impostazioni specificate nella sezione Directory di VC++ delle opzioni **Progetti** nella finestra di dialogo **Opzioni**. Per altre informazioni, vedere [Impostazione delle variabili di percorso e di ambiente per la compilazione dalla riga di comando](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)|  
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Apre i file specificati in un'istanza dell'applicazione in esecuzione. Se non sono presenti istanze in esecuzione, verrà avviata una nuova istanza con un layout di finestra semplificato.|  
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Avvia un'istanza dell'IDE di Visual Studio senza caricare il componente aggiuntivo specificato.|  
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura, caricando solo l'ambiente e i servizi predefiniti e le versioni acquistate dei pacchetti di terze parti.|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Cancella tutti i tag SkipLoading aggiunti ai VSPackage da utenti che non vogliono caricare i VSPackage.|  
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Forza Visual Studio in modo che esegua il merge dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i VSPackage disponibili.|  
  
 Usare le opzioni della riga di comando seguenti per eseguire l'attività descritta. Queste opzioni della riga di comando non visualizzano l'IDE.  
  
|Switch della riga di comando|Descrizione|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Visualizza la guida per le opzioni devenv nella **finestra del prompt dei comandi**.<br /><br /> **Devenv /?**|  
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Compila la soluzione o il progetto specificati in base alla configurazione relativa.<br /><br /> **Devenv myproj.csproj /build**|  
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Elimina i file creati dal comando di compilazione, senza che ciò abbia effetto sui file di origine.<br /><br /> **Devenv myproj.csproj /clean**|  
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Compila la soluzione, in base alla configurazione relativa, insieme ai file necessari per la distribuzione.<br /><br /> **Devenv myproj.csproj /deploy**|  
|[/Diff](../../ide/reference/diff.md)|Confronta due file.  Accetta quattro parametri, ovvero SourceFile, TargetFile, SourceDisplayName (facoltativo), TargetDisplayName (facoltativo).|  
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Consente di registrare modelli di progetto o di elemento che si trovano in *\<VisualStudioInstallDir>*\Common7\IDE\ProjectTemplates o *\<VisualStudioInstallDir>*\Common7\IDE\ItemTemplates per potervi accedere dalle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**.<br /><br /> **Devenv /InstallVSTemplates**|  
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Consente di specificare un file per la ricezione di errori durante la compilazione.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|  
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Il progetto da compilare, pulire o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione /build, /rebuild, /clean o /deploy.|  
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Specifica la configurazione del progetto da compilare o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione /project.|  
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Pulisce e compila la soluzione o il progetto specificati in base alla configurazione relativa.|  
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Ripristina impostazioni predefinite di Visual Studio. Facoltativamente reimposta le impostazioni per il file con estensione vssettings specificato.|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Notifica a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che è necessario unire i pacchetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nel sistema e controllare se vi sono modifiche della cache MEF.|  
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Aggiorna il file di soluzione specificato e tutti i file di progetto relativi, o il file di progetto specificato, nei formati [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] correnti per tali file.|  
  
## <a name="see-also"></a>Vedere anche  
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)