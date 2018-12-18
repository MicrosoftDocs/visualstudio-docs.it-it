---
title: Introduzione ad ASP.NET Core
author: asb3993
ms.author: amburns
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.openlocfilehash: 998bd304f287fffdf53dd9c53cb3be1d83a407f3
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="getting-started-with-aspnet-core"></a>Introduzione ad ASP.NET Core

 Visual Studio per Mac semplifica lo sviluppo del servizio dell'app grazie al supporto della piattaforma di sviluppo Web ASP.NET Core più recente. Il funzionamento di ASP.NET Core si basa su .NET Core, l'evoluzione più recente di .NET Framework e del runtime. È stato ottimizzato per garantire prestazioni elevate, sottoposto a factoring per ridurre le dimensioni di installazione e riprogettato per consentirne l'esecuzione in Linux e macOS, oltre che in Windows.

## <a name="installing-net-core"></a>Installazione di .NET Core

.NET core 1.1 viene installato automaticamente quando si installa Visual Studio per Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Creazione di un'app ASP.NET Core in Visual Studio per Mac

Aprire Visual Studio per Mac. Nella pagina iniziale selezionare **Nuovo progetto...**.

![Finestra di dialogo Nuovo progetto](media/asp-net-core-image1.png)

Verrà visualizzata la finestra di dialogo Nuovo progetto, che consente di selezionare un modello per la creazione dell'applicazione.

Alcuni progetti offrono un modello predefinito utilizzabile per iniziare a creare l'applicazione ASP.NET Core. Questi sono:

- **.NET Core > Progetto ASP.NET Core vuoto**
- **.NET Core > App Web ASP.NET Core**
- **.NET Core > API Web ASP.NET Core**
- **Multi-piattaforma > App > Connected App** (App connessa)

![Opzioni di progetto ASP.NET](media/asp-net-core-image11.png)

Selezionare **Progetto ASP.NET Core vuoto** e premere **Avanti**. Assegnare un nome al progetto e premere **Crea**. Verrà creata una nuova app ASP.NET Core simile all'immagine riportata di seguito:

![Vista del nuovo progetto ASP.NET Core vuoto](media/asp-net-core-image4.png)

Progetto ASP.NET Core vuoto crea un'applicazione Web con due file predefiniti: **Program.cs** e **Startup.cs**, spiegati di seguito. Crea anche una cartella Dependencies (Dipendenze), che contiene le dipendenze del pacchetto NuGet del progetto, ad esempio ASP.NET Core, il framework .NET Core e le destinazioni di MSBuild per la compilazione del progetto:

![Riquadro della soluzione che visualizza le dipendenze](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Aprire ed esaminare il file **Program.cs** nel progetto. Si noti che nel metodo `Main`, il punto di inizio dell'app, avvengono due cose:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```
Un'app ASP.NET Core crea un server Web nel metodo Main configurando e avviando un host tramite un'istanza di [ `WebHostBuilder` ](https://docs.microsoft.com/aspnet/core/fundamentals/hosting). Questo generatore offre alcuni metodi che consentono la configurazione dell'host. Nell'app modello vengono usate le configurazioni seguenti:

 * `UseKestrel`: specifica il server Kestrel che verrà usato dall'app
 * `UseContentRoot(Directory.GetCurrentDirectory())`: usa la cartella radice del progetto Web come radice del contenuto dell'app quando quest'ultima viene avviata da questa cartella
 * `.UseIISIntegration()`: specifica che l'app deve funzionare con IIS. Per usare IIS con ASP.NET Core, è necessario specificare sia `UseKestrel` che `UseIISIntegration`.
 * `.UseStartup<Startup>()`: specifica la classe di avvio.

 I metodi Build e Run creano l'elemento IWebHost che ospiterà l'app e lo avviano in ascolto di richieste HTTP in ingresso.

### <a name="startupcs"></a>Startup.cs

La classe di avvio dell'app viene specificata nel metodo `UseStartup()` in `WebHostBuilder`. È in questa classe che si specifica la pipeline di gestione delle richieste e si configurano eventuali servizi.

Aprire ed esaminare il file **Startup.cs** nel progetto:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

La classe di avvio deve sempre rispettare le regole seguenti:

 - Deve essere sempre pubblica
 - Deve contenere i due metodi pubblici `ConfigureServices` e `Configure`

Il metodo `ConfigureServices` consente di definire i servizi che verranno usati dall'app.

Il metodo `Configure` consente di comporre pipeline delle richieste tramite [middleware](https://docs.microsoft.com/aspnet/core/fundamentals/middleware). Si tratta di componenti usati all'interno delle pipeline delle applicazioni ASP.NET per la gestione delle richieste e delle risposte. La pipeline HTTP è costituita da un certo numero di delegati di richiesta, chiamati in sequenza. Ogni delegato può scegliere di gestire la richiesta o di passarla al delegato successivo.

È possibile configurare i delegati tramite i metodi `Run`,`Map` e `Use` in `IApplicationBuilder`. Il metodo `Run`, tuttavia, non chiama mai il delegato successivo e deve essere sempre usato alla fine della pipeline.

Il metodo `Configure` del modello predefinito è destinato all'esecuzione di alcune operazioni. Prima configura una pagina di gestione delle eccezioni da usare durante lo sviluppo. Quindi invia una risposta alla pagina Web di richiesta con la semplice frase "Hello World".

Questo semplice progetto "Hello World"può ora essere eseguito senza l'aggiunta di altro codice. Per eseguire l'app e visualizzarla nel browser, fare clic sul pulsante Esegui (il triangolo) sulla barra degli strumenti:

![Esegui l'app](media/asp-net-core-image5.png)

Per avviare il progetto Web, Visual Studio per Mac usa una porta casuale. Per individuare la porta usata, aprire Output applicazione, disponibile in **Vista > Riquadri**. L'output dovrebbe essere simile a quello illustrato di seguito:

![Output applicazione con la porta di ascolto](media/asp-net-core-image6.png)

Aprire il browser preferito e immettere `http://localhost:5000/`, sostituendo `5000` con la porta presente nell'output di Visual Studio visualizzato in Output applicazione. Dovrebbe essere visualizzato il testo `Hello World!`:

![Browser con il testo](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Aggiunta di un controller

Le app ASP.NET Core usano lo schema progettuale Model-View-Controller (MVC) per stabilire una separazione logica delle responsabilità di ogni parte dell'app. Lo schema MVC è costituito come segue:

- **Model** (Modello): classe che rappresenta i dati dell'app.
- **View** (Vista): visualizza l'interfaccia utente dell'app. Spesso corrisponde ai dati del modello.
- **Controller**: classe che gestisce le richieste del browser e risponde all'input e all'interazione dell'utente.

Per altre informazioni sull'uso dello schema MVC, vedere la guida [Overview of ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/mvc/overview) (Panoramica di MVC ASP.NET Core).

Per aggiungere un controller, eseguire le operazioni seguenti:

1. Fare clic con il pulsante destro del mouse sul nome del progetto e selezionare **Aggiungi > Nuovo file**. Selezionare **Generale > Classe vuota** e quindi immettere un nome di controller:

    ![Finestra di dialogo Nuovo file](media/asp-net-core-image8.png)

2. Aggiungere al nuovo controller il codice seguente:

    ```
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Aggiungere la dipendenza `Microsoft.AspNetCore.Mvc` al progetto facendo clic con il pulsante destro del mouse sulla cartella **Dependency** (Dipendenza) e selezionando **Aggiungi pacchetto...** .

4. Usare la casella di ricerca per cercare `Microsoft.AspNetCore.Mvc` all'interno della libreria NuGet e selezionare **Aggiungi pacchetto**. L'installazione potrebbe richiedere alcuni minuti e potrebbe essere richiesto di accettare diverse licenze per le dipendenze necessarie:

    ![Aggiungi Nuget](media/asp-net-core-image9.png)

5. Nella classe di avvio rimuovere l'espressione lambda `app.Run` e impostare come illustrato di seguito la logica di routing degli URL usata da MVC per determinare il codice da chiamare:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Assicurarsi di rimuovere l'espressione lambda `app.Run`, poiché questa eseguirebbe l'override della logica di routing.

    Per determinare il codice da eseguire, MVC usa il formato seguente:

    `/[Controller]/[ActionName]/[Parameters]`

    Quando si aggiunge il frammento di codice precedente, si indica all'app di usare come impostazioni predefinite il controller `HelloWorld` e il metodo di azione `Index`.

6. Aggiungere la chiamata a `services.AddMvc();` al metodo `ConfigureServices`, come illustrato di seguito:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    È anche possibile passare le informazioni per i parametri dall'URL al controller.

7. Aggiungere un altro metodo a HelloWorldController, come illustrato di seguito:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Se ora si esegue l'app, il browser dovrebbe aprirsi automaticamente:

    ![Esecuzione dell'app nel browser](media/asp-net-core-image13.png)

9. Tentare di passare a `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (sostituire `xxxx` con la porta corretta). Dovrebbe essere visualizzato quanto segue:

    ![Esecuzione dell'app nel browser con argomenti](media/asp-net-core-image10.png)


## <a name="troubleshooting"></a>Risoluzione dei problemi

Se è necessario installare manualmente .NET Core in Mac OS 10.11 (El Capitan) e versioni successive, eseguire le operazioni seguenti:

1. Prima di iniziare l'installazione di .NET Core, assicurarsi che siano stati eseguiti tutti gli aggiornamenti del sistema operativo fino alla versione stabile più recente. Per eseguire questa verifica, passare all'applicazione App Store e selezionare la scheda Aggiornamenti.

2. Seguire i passaggi elencati nel [sito .NET Core](https://www.microsoft.com/net/core#macos).

Per installare correttamente .NET Core, assicurarsi che tutti i quattro passaggi vengano completati in modo appropriato.

## <a name="summary"></a>Riepilogo

Questa guida offre un'introduzione ad ASP.NET Core. Descrive che cos'è e quando usarlo e fornisce informazioni per l'uso in Visual Studio per Mac.
Per altre informazioni sui passaggi successivi, fare riferimento alle guide seguenti:
- Documentazione di [ASP.NET Core](https://docs.microsoft.com/aspnet/core/#build-web-ui-and-web-apis-using-aspnet-core-mvc).
- [Creating Backend Services for Native Mobile Applications](https://docs.microsoft.com/aspnet/core/mobile/native-mobile-backend) (Creazione di servizi back-end per applicazioni per dispositivi mobili native), che illustra come creare un servizio REST tramite ASP.NET Core per un'app Xamarin.Forms.
- [ASP.NET Core hands-on lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) (Esercitazione pratica su ASP.NET Core).
