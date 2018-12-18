---
title: Introduzione a C# e ad ASP.NET Core in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c4d67a57063854f859a766068084d63902ba038e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-c-and-aspnet-in-visual-studio"></a>Introduzione a C# e ad ASP.NET Core in Visual Studio
In questa esercitazione per lo sviluppo in C# con ASP.NET Core tramite Visual Studio si creerà un'app Web ASP.NET Core C# e si aggiungerà codice all'app. Si esploreranno poi alcune funzionalità dell'ambiente IDE e si eseguirà l'app.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="before-you-begin"></a>Prima di iniziare
Ecco una rapida serie di domande frequenti per presentare alcuni concetti chiave.
### <a name="what-is-c"></a>Che cos'è C#?
[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) è un linguaggio di programmazione indipendente dai tipi e orientato agli oggetti progettato per garantire solidità e facilità di apprendimento.
### <a name="what-is-aspnet-core"></a>Che cos'è ASP.NET Core?
ASP.NET Core è un framework open source e multipiattaforma per la compilazione di applicazioni connesse a Internet, ad esempio applicazioni e servizi Web. Le app ASP.NET Core possono essere eseguite in .NET Core o in .NET Framework. È possibile sviluppare ed eseguire app ASP.NET Core multipiattaforma in Windows, Mac e Linux. ASP.NET Core è disponibile open source in [GitHub](https://github.com/aspnet/home).
### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?
Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.  

## <a name="start-developing"></a>Iniziare a sviluppare
È arrivato il momento di iniziare a sviluppare.

### <a name="create-a-project"></a>Creare un progetto
Prima di tutto è necessario creare un progetto ASP.NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual C#**, espandere **Web** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**, assegnare al file il nome *MyCoreApp* e quindi scegliere **OK**.   

   ![Modello di progetto di applicazione Web ASP .NET Core nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Aggiungere un carico di lavoro (facoltativo)
Se il modello di progetto **Applicazione Web ASP.NET Core** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo ASP.NET e Web**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto
1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

  ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti
1. Chiudere la finestra di dialogo **Nuovo progetto** e dalla barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**.

2. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.   

#### <a name="add-a-project-template"></a>Aggiungere un modello di progetto
1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** scegliere il modello di progetto **Applicazione Web (MVC)**.  

2. Selezionare **ASP.NET Core 2.0** dal menu a discesa superiore. (Se non viene visualizzato **ASP.NET Core 2.0** nell'elenco, installarlo seguendo il collegamento **Download** visualizzato in una barra gialla nella parte superiore della finestra di dialogo.) Scegliere **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Informazioni sulla soluzione
Questa soluzione segue il criterio architetturale MVC (Model-View-Controller), che suddivide le app in tre componenti principali:

* **Modelli**, che includono classi che rappresentano i dati dell'app. Le classi modello usano la logica di convalida per applicare le regole business per tali dati. In genere, gli oggetti del modello recuperano e archiviano lo stato del modello in un database.
* **Visualizzazioni**, che visualizzano l'interfaccia utente dell'app. In genere questa interfaccia utente presenta i dati del modello.
* **Controller**, che includono classi che gestiscono le richieste del browser. Recuperano i dati del modello e chiamano i modelli di vista che restituiscono una risposta. In un'app MVC, la visualizzazione presenta solo le informazioni, mentre il controller gestisce e risponde all'input e alle azioni di interazione dell'utente.

Il criterio MVC consente di creare app più facili da testare e da aggiornare rispetto alle app monolitiche tradizionali.

### <a name="tour-your-solution"></a>Presentazione della soluzione
1. Il modello di progetto crea una soluzione con un unico progetto ASP.NET Core denominato **MyCoreApp**. Espandere il nodo del progetto per esporne il contenuto.

    ![Esplora soluzioni di ASP.NET in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

1. Aprire il file **HomeController.cs** dalla cartella **Controller**.

      ![File HomeController.cs in Esplora soluzioni in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

2. Visualizzare il file **HomeController.cs**

  ![HomeController.cs nella finestra del codice di Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

4. Il progetto ha anche una cartella **Visualizzazioni** contenente altre cartelle mappate a ognuno dei controller, oltre a una cartella per le visualizzazioni **condivise**. Ad esempio, il file CSHTML (estensione del linguaggio HTML) di visualizzazione per il percorso **/Home/About** si troverebbe in **Visualizzazioni/Home/About.cshtml**. Aprire il file.

  ![File About.cshtml in Esplora soluzioni in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

5. Questo file CSHTML usa la sintassi Razor per eseguire il rendering HTML in base a una combinazione di tag standard e C# inline.

  ![About.cshtml nella finestra del codice di Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

 >[!NOTE]
 > Per altre informazioni, vedere la pagina [Introduzione a C# e ASP.NET tramite la sintassi Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

6. La soluzione contiene anche una cartella **wwwroot** per il sito Web. È possibile inserire contenuto statico del sito, ad esempio fogli di stile CSS, immagini e librerie JavaScript, direttamente nei percorsi ad essi destinati al momento della distribuzione del sito stesso.

 ![Cartella wwwroot in Esplora soluzioni in Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

7. Sono presenti anche diversi file di configurazione che consentono di gestire il progetto, i pacchetti di questo e l'applicazione in fase di runtime. La [configurazione](/aspnet/core/fundamentals/configuration) predefinita dell'applicazione, ad esempio, è archiviata in **appsettings.json**. È tuttavia possibile ignorare alcune di queste impostazioni, oppure ignorarle tutte, a seconda dell'ambiente, ad esempio tramite un file **appsettings.Development.json** per l'ambiente **Development**.

 ![File di configurazione in Esplora soluzioni in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Esecuzione e debug dell'applicazione

1. Scegliere il pulsante **IIS Express** nell'IDE per compilare ed eseguire l'app in modalità di debug. In alternativa, premere **F5**, oppure scegliere **Debug > Avvia debug** dalla barra dei menu.

  ![Fare clic sul pulsante IIS Express in Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Se viene visualizzato il messaggio di errore **Non è possibile connettersi al server Web 'IIS Express'**, chiudere Visual Studio e quindi aprirlo usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

1. Visual Studio apre una finestra del browser. Selezionare **Informazioni su**.

 ![Selezionare Informazioni su nella finestra del browser per l'app](../ide/media/csharp-aspnet-browser-page.png)

 Oltre ad altre operazioni, la pagina Informazioni su nel browser esegue il rendering del testo impostato nel file HomeController.cs.

   ![Visualizzare il testo nella pagina informazioni su](../ide/media/csharp-aspnet-browser-page-about.png)

1. Mantenere aperta la finestra del browser e tornare a Visual Studio. Aprire il file **Controller/HomeController.cs** se non è già aperto.

 ![Aprire il file HomeController.cs da Esplora soluzioni in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Impostare un punto di interruzione nella prima riga del metodo **About**. A tale scopo, fare clic sul margine o posizionare il cursore sulla riga e premere **F9**.

  Questa riga imposta alcuni dati nella raccolta **ViewData** di cui viene eseguito il rendering della pagina CSHTML in **Visualizzazioni/Home/About.cshtml**.

 ![Impostare un punto di interruzione in corrispondenza della prima riga del metodo About in About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Tornare al browser e aggiornare la pagina Informazioni su. Questa operazione attiverà il punto di interruzione in Visual Studio.

1. In Visual Studio far passare il mouse sopra il membro **ViewData** per visualizzarne i dati.

 ![Visualizzare il membro ViewData del metodo About per visualizzare altre informazioni](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Rimuovere il punto di interruzione dell'applicazione con lo stesso metodo usato per aggiungerlo.

1. Aprire **Visualizzazioni/Home/About.cshtml**.

 ![Selezionare About.cshtml in Esplora soluzioni](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Modificare il testo **"additional"** in **"changed"** e salvare il file.

 ![Modificare il testo "additional" in "changed"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Tornare alla finestra del browser per visualizzare il testo aggiornato. Se il testo modificato non viene visualizzato, aggiornare il browser.

  ![Aggiornare la finestra del browser per visualizzare il testo modificato](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Scegliere il pulsante **Termina debug** dalla barra degli strumenti per interrompere il debug. In alternativa, premere **Maiusc**+**F5**, o scegliere **Debug** > **Termina debug** dalla barra dei menu.

 ![Fare clic sul pulsante Termina debug sulla barra degli strumenti](../ide/media/csharp-aspnet-stop-debugging.png)


L'esercitazione è stata completata.

## <a name="see-also"></a>Vedere anche
* [Introduzione ad ASP.NET Core MVC e Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)
* [Introduzione all'uso di pagine Razor in ASP.NET Core](/aspnet/core/tutorials/razor-pages/razor-pages-start)
* [Novità di C#](/dotnet/csharp/whats-new)
* [Riferimenti per il linguaggio C#](/dotnet/csharp/language-reference/index)
* Esercitazione video [C# Fundamentals for Absolute Beginners](https://mva.microsoft.com/en-US/training-courses/c-fundamentals-for-absolute-beginners-16169) (Concetti di base su C# per principianti)
