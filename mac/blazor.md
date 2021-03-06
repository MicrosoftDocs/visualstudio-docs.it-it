---
title: Crea Blazor app Web
description: Fornisce informazioni sul Blazor supporto nelle app ASP.NET Core in Visual Studio per Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 30e9a62e8bf0364a76cbd43995cbb77c1a5bd0c4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729418"
---
# <a name="create-no-locblazor-web-apps"></a>Crea Blazor app Web

Questa guida offre un'introduzione alla creazione della prima Blazor app Web. Per istruzioni più dettagliate, vedere [Introduzione a ASP.NET Core Blazor ](/aspnet/core/blazor/index).

ASP.NET Core Blazor supporta due diverse opzioni di hosting: Blazor WebAssembly (WASM) o Blazor Server. Visual Studio per Mac supporta entrambi i modelli di hosting. Visual Studio per Mac 8.4 + supporta Blazor Server e Visual Studio per Mac 8.6 + supporta entrambi. Per ulteriori informazioni sui Blazor modelli di hosting, vedere [ASP.NET Core Blazor modelli di hosting ](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true). Il supporto per Blazor WebAssembly il debug di progetti in Visual Studio per Mac è disponibile nella versione di anteprima della versione 8.8 (disponibile tramite il canale di aggiornamento dell'anteprima nel menu **> verifica della disponibilità di aggiornamenti di Visual Studio** ).

Che cos'è Blazor? Blazor è un Framework per la creazione di un'interfaccia utente Web interattiva sul lato client con .NET, che offre agli sviluppatori Web i vantaggi seguenti:

* scrivere codice in C# invece che in JavaScript.
* Permette di sfruttare l'ecosistema .NET esistente di librerie .NET.
* Permette di condividere la logica dell'app tra server e client.
* Trarre vantaggio da. Prestazioni, affidabilità e sicurezza di NET.
* È sempre più produttivo con Visual Studio su PC, Linux e macOS.
* basato su un set comune di linguaggi, framework e strumenti che sono stabili, ricchi di funzionalità e facili da usare.

## <a name="create-a-new-no-locblazor-webassembly-project"></a>Creazione di un nuovo Blazor WebAssembly progetto
1. Nella **finestra Start** selezionare **nuovo** per creare un nuovo progetto:

   ![Visual Studio per Mac finestra di avvio con la nuova selezione evidenziata](media/blazor-new-project.png)

1. Nella finestra di dialogo **nuovo progetto** selezionare app **app .NET Core** e quindi fare clic su >  > **Blazor WebAssembly** **Avanti**: ![ screenshot della finestra di dialogo nuovo progetto con::: NO-LOC (webassembly WebBlazer)::: app evidenziata nel riquadro app sotto ASP.NET Core e il pulsante Avanti selezionato.](media/blazor-wasm-project-template.png)

1. Selezionare .NET Core 3,1 come Framework di destinazione, quindi fare clic su **Avanti**. 
   ![Configurare la nuova finestra di dialogo::: NO-LOC (webassembly Blazer)::: app visualizzata con il Framework di destinazione selezionato per .NET Core 3,1](media/blazor-wasm-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se lo si desidera. Selezionare **Crea** per creare il progetto.
    ![Configurare la nuova finestra di dialogo::: NO-LOC (webassembly Blazer)::: app visualizzata quando si immette il nome del progetto](media/blazor-wasm-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra di layout del codice.

1. Selezionare **Esegui**  >  **Avvia senza eseguire debug** per eseguire l'app.

   Visual Studio avvia [gheppio](/aspnet/core/fundamentals/servers/kestrel), apre un browser a `https://localhost:5001` e visualizza l' Blazor app Web.

   ![::: NO-LOC (Blazer)::: app Web in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-no-locblazor-server-project"></a>Creazione di un nuovo Blazor progetto server

1. Nella **finestra Start** selezionare **nuovo** per creare un nuovo progetto:

   ![Visual Studio per Mac finestra di avvio con la nuova selezione evidenziata](media/blazor-new-project.png)
1. Nella finestra di dialogo **nuovo progetto** selezionare  >  > **Blazor app Server** app .NET Core e fare clic su **Avanti**: ![ screenshot della finestra di dialogo nuovo progetto con::: NO-LOC (Blazer)::: Server App evidenziato nel riquadro dell'app in ASP.NET Core e il pulsante Avanti selezionato.](media/blazor-project-template.png)

1. Selezionare .NET Core 3,1 come Framework di destinazione, quindi fare clic su **Avanti**. 
   ![Configurare la finestra di dialogo nuova app::: NO-LOC (Blazer)::: Server visualizzata con il Framework di destinazione selezionato per .NET Core 3,1](media/blazor-select-target-framework.png)

1. Scegliere un nome per il progetto e aggiungere il supporto Git, se lo si desidera. Selezionare **Crea** per creare il progetto.
   ![Configurare la nuova finestra di dialogo app::: NO-LOC (Blazer)::: Server visualizzata quando si immette il nome del progetto](media/blazor-name-project.png)

   Visual Studio per Mac apre il progetto nella finestra di layout del codice.
1. Selezionare **Esegui**  >  **Avvia senza eseguire debug** per eseguire l'app.

   Visual Studio avvia [gheppio](/aspnet/core/fundamentals/servers/kestrel), apre un browser a `https://localhost:5001` e visualizza l' Blazor app Web.

   ![::: NO-LOC (Blazer)::: app Web in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Blazor supporto in Visual Studio per Mac

Visual Studio per Mac (a partire dalla versione 8,4) include nuove funzionalità che consentono di creare nuovi Blazor progetti server. Fornisce inoltre il supporto standard che ci si aspetta, ad esempio la compilazione, l'esecuzione e il debug di Blazor progetti. In Visual Studio per Mac 8,6 è stato aggiunto il supporto per la creazione, la compilazione e l'esecuzione di Blazor WebAssembly progetti.

Nella procedura dettagliata precedente è stato illustrato come il Blazor modello di progetto di app Server consente di creare una nuova Blazor app Server o un nuovo Blazor WebAssembly progetto di app. Verranno ora esaminate alcune delle funzionalità aggiuntive di Visual Studio per Mac per supportare Blazor lo sviluppo di progetti.

### <a name="editor-support-for-razor-files"></a>Supporto dell'editor per file con *estensione Razor*
Visual Studio per Mac include il supporto per la modifica di file con estensione Razor, la maggior parte dei file che verranno usati durante la creazione di Blazor applicazioni. Visual Studio per Mac offre supporto completo per la colorazione e il completamento per i file Razor, inclusi i completamenti per i componenti Razor dichiarati nel progetto.

![Visual Studio per Mac finestra dell'editor che mostra IntelliSense per::: NO-LOC (Blazer):::](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>Pubblicazione Blazor di applicazioni nel servizio app Azure
È anche possibile pubblicare Blazor applicazioni direttamente nel servizio app Azure. Se non si ha un account Azure per eseguire l' Blazor app in Azure, è sempre possibile [iscriversi per ottenere un account gratuito](https://azure.microsoft.com/free) , disponibile anche con 12 mesi di servizi diffusi gratuiti, $200 in crediti di Azure gratuiti e oltre 25 servizi sempre gratuiti.

![Visual Studio per Mac che illustra l'esperienza di pubblicazione di Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia del progetto

Blazor per impostazione predefinita, le app Web includono alcune directory e file. Come si inizia, di seguito sono riportate le informazioni principali che è necessario conoscere:

### <a name="pages-folder"></a>Cartella Pages

Questa cartella contiene le pagine Web di un progetto che usano l'estensione di file *Razor* .

### <a name="shared-folder"></a>Cartella condivisa

Questa cartella include i componenti condivisi, usando anche l'estensione *Razor* . Si noterà che questo include *MainLayout. Razor*, che viene usato per definire il layout comune nell'applicazione. Include anche il componente Shared *NavMenu. Razor* , che viene usato in tutte le pagine. Se si stanno creando componenti riutilizzabili, questi verranno inseriti nella cartella **condivisa** .

### <a name="app-settings"></a>Impostazioni app

Il *appSettings.jsnel* file contiene i dati di configurazione, ad esempio le stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la pagina relativa alla [configurazione nella Guida di ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Cartella wwwroot

Questa cartella contiene file statici, ad esempio file HTML, JavaScript e CSS. Per altre informazioni, vedere [File statici in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Questo file contiene il punto di ingresso per il programma. Per altre informazioni, vedere [Host Web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="no-locblazor-server-app-specific-files"></a>Blazor File specifici dell'app Server
#### <a name="app-settings"></a>Impostazioni app

Il *appSettings.jsnel* file contiene i dati di configurazione, ad esempio le stringhe di connessione.

Per ulteriori informazioni sulla configurazione, vedere la pagina relativa alla [configurazione nella Guida di ASP.NET](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Questo file contiene il codice che configura il comportamento dell'app, ad esempio se l'app richiede il consenso per i cookie. Per altre informazioni, vedere [Avvio delle app in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Riepilogo
In questa esercitazione è stato illustrato come creare una nuova app Blazor o app Server Blazor WebAssembly in Visual Studio per Mac e sono state apprese alcune delle funzionalità offerte da Visual Studio per Mac per facilitare la creazione di Blazor applicazioni.

## <a name="see-also"></a>Vedi anche

Per una guida più completa alla creazione di Blazor app Web, vedere [introduzione a Blazor ASP.NET Core ](/aspnet/core/blazor/index).