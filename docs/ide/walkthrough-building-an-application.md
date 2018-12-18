---
title: "Procedura dettagliata: compilazione di un'applicazione | Microsoft Docs"
ms.custom: ''
ms.date: 09/25/2017
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94f9b9ba60279c359ce7c6cc3c9646bfbbe7c5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-building-an-application"></a>Procedura dettagliata: compilazione di un'applicazione

Completando questa procedura dettagliata è possibile acquisire familiarità con numerose opzioni che possono essere configurate quando si compilano applicazioni con Visual Studio. Verrà illustrato come creare una configurazione della build personalizzata, nascondere alcuni messaggi di avviso e aumentare le informazioni di output di compilazione per un'applicazione di esempio.

## <a name="install-the-sample-application"></a>Installare l'applicazione di esempio

Scaricare l'esempio di [introduzione alla creazione di applicazioni WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Scegliere C# o Visual Basic. Dopo aver scaricato il file con estensione zip, estrarlo e aprire il file **ExpenseItIntro.sln** usando Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Creare una configurazione della build personalizzata

Quando si crea una soluzione, le configurazioni della build di versione e di debug e le relative destinazioni della piattaforma predefinite sono definite automaticamente per la soluzione. È quindi possibile personalizzare queste configurazioni o crearne di proprie. Le configurazioni della build specificano il tipo di compilazione. Le piattaforme di compilazione specificano il sistema operativo a cui è rivolta un'applicazione per la configurazione. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md), [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) e [Procedura: Impostare le configurazioni di debug e di versione](../debugger/how-to-set-debug-and-release-configurations.md).

È possibile modificare o creare configurazioni e impostazioni piattaforma usando la finestra di dialogo **Gestione configurazione**. In questa procedura si creerà una configurazione della build per il test.

### <a name="to-create-a-build-configuration"></a>Per creare una configurazione della build

1. Aprire la finestra di dialogo **Gestione configurazione**.

   ![Menu Compila, comando Gestione configurazione](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  

1. Nell'elenco **Configurazione soluzione attiva** scegliere **\<Nuova...\>**.

1. Nella finestra di dialogo **Nuova configurazione soluzione** assegnare un nome alla nuova configurazione `Test`, copiare le impostazioni dalla configurazione per il debug esistente e quindi scegliere il pulsante **OK**.

   ![Finestra di dialogo Nuova configurazione soluzione](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  

1. Nell'elenco **Piattaforma soluzione attiva** scegliere **\<Nuova...\>**.

1. Nella finestra di dialogo **Nuova piattaforma soluzione** scegliere **x64** e non copiare le impostazioni dalla piattaforma x86.

   ![Finestra di dialogo Nuova piattaforma soluzione](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  

1. Fare clic sul pulsante **OK** .

   La configurazione della soluzione attiva è stata modificata su Test con la piattaforma della soluzione attiva impostata su x64.

   ![Gestione configurazione con configurazione di test](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  

1. Scegliere **Chiudi**.

È possibile verificare o modificare rapidamente la configurazione della soluzione attiva tramite l'elenco **Configurazioni soluzione** nella barra degli strumenti **Standard**.
  
![Opzione Configurazioni soluzione barra degli strumenti standard](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Compilare l'applicazione

Successivamente verrà creata la soluzione con la configurazione della build personalizzata.
  
### <a name="to-build-the-solution"></a>Per compilare la soluzione
  
-   Nella barra dei menu scegliere **Compila** > **Compila soluzione**.
  
    Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata.
  
## <a name="hide-compiler-warnings"></a>Nascondere gli avvisi del compilatore

A questo punto viene presentata la parte del codice che determina un avviso generato dal compilatore.

1. Nel progetto C# aprire il file **ExpenseReportPage.xaml.cs**. Nel metodo **ExpenseReportPage** aggiungere il codice seguente: `int i;`.

    OR

    Nel progetto Visual Basic aprire il file **ExpenseReportPage.xaml.vb**. Nel costruttore personalizzato **Public Sub New...**  aggiungere il codice seguente: `Dim i`.

1. Compilare la soluzione.

Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata, ma sono stati generati avvisi:

![Finestra Output di Visual Basic ](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

![Finestra Output di Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

È possibile nascondere temporaneamente determinati messaggi di avviso durante una compilazione anziché lasciare che ingombrino l'output di compilazione.

### <a name="to-hide-a-specific-c-warning"></a>Per nascondere un avviso specifico di C#

1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.

1. Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.
  
     Si apre la finestra **Creazione progetti**.

1. Scegliere la pagina **Compilazione** e specificare il numero di avviso **0168** nella casella **Non visualizzare avvisi**.
  
     ![Pagina Compilazione, Creazione progetti](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     Per altre informazioni, vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Compilare la soluzione.
  
     Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.
  
     ![Finestra Output, avvisi durante la compilazione di Visual C&#35;](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>Per eliminare tutti gli avvisi durante la compilazione di Visual Basic

1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.

1. Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.
  
     Si apre la finestra **Creazione progetti**.

1. Nella pagina **Compilazione** selezionare la casella di controllo **Disabilita tutti gli avvisi**.
  
     ![Pagina Compilazione, Creazione progetti](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     Per altre informazioni, vedere [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md) (Configurazione degli avvisi in Visual Basic).

1. Compilare la soluzione.
  
 Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.
  
 ![Finestra Output, avvisi durante la compilazione di Visual Basic ](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Per altre informazioni, vedere [Procedura: Non visualizzare avvisi del compilatore](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>Visualizzare dettagli di compilazione aggiuntivi nella finestra di output

È possibile modificare la quantità di informazioni sul processo di compilazione visualizzate nella finestra **Output**. Il livello di dettaglio di compilazione è in genere impostato su minimo, cioè nella finestra **Output** viene visualizzato solo un riepilogo del processo di compilazione insieme a eventuali errori o avvisi di priorità alta. È possibile visualizzare altre informazioni sulla compilazione tramite la [finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).
  
> [!IMPORTANT]
>  Se si visualizzano maggiori informazioni, il completamento della compilazione richiederà più tempo.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Per modificare la quantità di informazioni nella finestra Output

1. Aprire la finestra di dialogo **Opzioni**.
  
     ![Comando Opzioni nel menu Strumenti](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  

1. Scegliere la categoria **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.

1. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi **OK**.

1. Nella barra dei menu scegliere **Compilazione**, **Pulisci soluzione**.

1. Compilare la soluzione e quindi esaminare le informazioni nella finestra **Output**.
  
     Le informazioni sulla compilazione includono l'ora di inizio della compilazione (indicata all'inizio) e l'ordine in cui i file sono stati elaborati. Queste informazioni includono anche la sintassi del compilatore effettiva che Visual Studio esegue durante la compilazione.
  
     Ad esempio, nella compilazione di C#, l'opzione [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) elenca il codice di avviso, 1762, specificato in precedenza in questo argomento, insieme ad altri tre avvisi.
  
     Nella compilazione di Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) non include avvisi specifici da escludere, pertanto non viene visualizzato alcun avviso.
  
    > [!TIP]
    > È possibile cercare il contenuto della finestra **Output** se si visualizza la finestra di dialogo **Trova** scegliendo i tasti CTRL+F.

Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Creare una build di versione

È possibile compilare una versione dell'applicazione di esempio ottimizzata per la spedizione. Per la build di versione, si specificherà che il file eseguibile venga copiato in una condivisione di rete prima dell'avvio della compilazione.

Per altre informazioni, vedere [Procedura: Modificare la directory dell'output compilato](../ide/how-to-change-the-build-output-directory.md) e [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>Per specificare una build di versione per Visual Basic

1. Aprire **Creazione progetti**.
  
     ![Menu Visualizza, comando pagine delle proprietà](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Scegliere la pagina **Compilazione**.

1. Nell'elenco **Configurazione** scegliere **Versione**.

1. Nell'elenco **Piattaforma** scegliere **x86**.

1. Specificare un percorso di compilazione nella casella **Percorso dell'output di compilazione**.

     Ad esempio, è possibile specificare \\\mioserver\compilazioni.

    > [!IMPORTANT]
    > Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere il pulsante **OK** nella finestra di messaggio.

1. Compilare l'applicazione.

     ![Comando Compila soluzione dal menu Compila](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

### <a name="to-specify-a-release-build-for-c"></a>Per specificare una build di versione per Visual C# #

1. Aprire **Creazione progetti**.
  
     ![Menu Visualizza, comando pagine delle proprietà](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  

1. Scegliere la scheda **Compila**.

1. Nell'elenco **Configurazione** scegliere **Versione**.

1. Nell'elenco **Piattaforma** scegliere **x86**.

1. Specificare un percorso di rete nella casella **Percorso output**.
  
     Ad esempio, è possibile specificare \\\mioserver\compilazioni.
  
    > [!IMPORTANT]
    > Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere il pulsante **OK** nella finestra di messaggio.

1. Nella **barra degli strumenti Standard** impostare le opzioni Configurazioni soluzione su **Release** e Piattaforme soluzione su **x86**.

1. Compilare l'applicazione.

     ![Comando Compila soluzione dal menu Compila](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  

   Il file eseguibile viene copiato nel percorso di rete specificato. Il percorso sarà \\\mioserver\compilazioni\\*Nomefile*.exe.

Congratulazioni: questa procedura dettagliata è stata completata correttamente.
  
## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: compilazione di un progetto (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Panoramica della precompilazione del progetto di applicazione Web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md)
