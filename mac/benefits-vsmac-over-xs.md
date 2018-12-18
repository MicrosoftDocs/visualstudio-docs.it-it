---
title: Vantaggi di Visual Studio per Mac rispetto a Xamarin Studio | Microsoft Docs
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.openlocfilehash: 08e693e92d6d07da21f8230f9c1de49f071c05e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Vantaggi di Visual Studio per Mac rispetto a Xamarin Studio 
 
Visual Studio per Mac ha sostituito Xamarin Studio come interfaccia IDE completa per Mac. Visual Studio per Mac offre funzionalità che consentono di sviluppare applicazioni e servizi Web, app multipiattaforma per desktop e dispositivi mobili e giochi. In più, facilita sensibilmente l'integrazione con Azure, sia per la pubblicazione in Azure che per la creazione di Funzioni di Azure. Visual Studio per Mac include tutto ciò che ci si aspetta da un IDE moderno, tra cui un editor standard completo, un potente debugger, un'area di lavoro personalizzabile, integrazione Git e un sistema di estensione avanzato, tutto progettato in modo nativo per Mac. 

Altre funzionalità: 

* IntelliSense C# basato su Roslyn, refactoring, analizzatori e correzioni di codice 
* Gestione dei pacchetti basata su NuGet 
* Formato dei progetti compatibile con Visual Studio 
* Motore di compilazione MSBuild 
* Testing unità integrato 
* Supporto per F# predefinito 

I vantaggi elencati in questa guida contrassegnati come **Anteprima** sono disponibili solo nel [canale alfa](https://docs.microsoft.com/visualstudio/mac/update#Changing_the_Updater_channel). 

## <a name="language-support"></a>Supporto per le lingue 

La scrittura di codice C# 7 nel Mac è disponibile solo in Visual Studio per Mac.

## <a name="net-core"></a>.NET Core  

[.NET core](https://www.microsoft.com/net/core#macos) è una piattaforma per la creazione di applicazioni che vengono eseguite in Windows, Linux e Mac. Visual Studio per Mac offre supporto per il caricamento, la creazione, l'esecuzione e il debug di progetti .NET Core. 

.NET Core, installato con Visual Studio per Mac, non richiede altri elementi.

Supporto di .NET Core: 

* IntelliSense C# e F#. 
* Modelli di progetto .NET Core per console, libreria e applicazioni Web. 
* Completo supporto per il debug, inclusi punti di interruzione, stack di chiamate, finestra Espressioni di controllo e così via. 
* Riferimenti ai pacchetti NuGet e ripristino basato su MSBuild. 
* Supporto per il testing unità integrato per test di esecuzione e di debug con la piattaforma di test di Visual Studio inclusa in .NET Core SDK. 
* Migrazione dal precedente formato project.json. 
* Supporto di progetti .NET standard.

## <a name="web-development"></a>Sviluppo Web  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio per Mac include modelli ASP.NET Core per progetti MVC e API Web predefiniti.
 
![IntelliSense per HTML](media/benefits-vsmac-over-xs-image3.png)

Visual Studio per Mac offre anche un nuovo supporto per strumenti Web per file HTML, CSS e JSON. 

### <a name="html"></a>HTML 

* Nuovo Modello HTML. 
* Rientro automatico e formattazione migliorati. 
* Colorazione migliorata. 
* Funzionalità IntelliSense migliorata. 
* Riduzione del codice (da abilitare). 
* Comando Unminify. 
* Modelli di codice migliorati (frammenti). 
* Racchiudi selezione in `<div>`. 
* L'opzione su/giù sposta il testo selezionato verso l'alto o verso il basso. 

### <a name="css"></a>CSS 

* Rientro automatico e formattazione migliorati. 
* Colorazione migliorata. 
* Funzionalità IntelliSense migliorata. 
* Riduzione del codice. 
* Molti modelli di codice (frammenti). 
* L'opzione su/giù sposta il testo selezionato verso l'alto o verso il basso. 

### <a name="json"></a>JSON 
* Selezione schemi con accesso a schemastore.org. 
* Convalida dallo schema. 
* IntelliSense dallo schema. 
* Rientro automatico e formattazione migliorati. 
* Colorazione migliorata. 
* Inserimento/rimozione di commenti. 
* Aggiunta di virgolette e corrispondenza parentesi graffe. 
* L'opzione su/giù sposta il testo selezionato verso l'alto o verso il basso. 

## <a name="publishing-to-azure"></a>Pubblicazione in Azure

Con Visual Studio per Mac è possibile pubblicare app e servizi Web ASP.NET Core nel Servizio app di Azure. 

![Pubblicare in Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Funzioni di Azure (**Anteprima**)

Funzioni di Azure rappresenta una soluzione efficace per eseguire facilmente piccole parti di codice, o funzioni, nel cloud. Visual Studio per Mac consente di scrivere il codice di Funzioni di Azure e di eseguirne il debug in locale. Per iniziare, cercare Funzioni di Azure in Cloud nella finestra di dialogo Nuovo progetto. 

### <a name="docker-support-preview"></a>Supporto per Docker (**Anteprima**)

È ora possibile pubblicare app ASP.NET Core in contenitori Docker ed eseguirli da un Servizio app di Azure. 

Per abilitare il supporto per Docker nel progetto, fare clic con il pulsante destro del mouse sull'app Web ASP.NET Core e selezionare **Aggiungi > Supporto Docker**. 

Per pubblicare l'app Web in un contenitore Docker, usare il flusso di lavoro **Pubblica > Pubblica in Azure** introdotto in Visual Studio per Mac.

## <a name="source-editor-improvements"></a>Miglioramenti apportati all'editor 

Oltre a IntelliSense C# basato su Roslyn, refactoring, analizzatori e correzioni di codice, rispetto a Xamarin Studio l'editor di Visual Studio per Mac presenta i miglioramenti seguenti: 

### <a name="language-bundles"></a>Bundle lingua 

Visual Studio per Mac offre supporto per i bundle lingua TextMate(`.tmBundle`) e sublime 3 (`.sublime`), che possono essere usati per aggiungere gli elementi seguenti: 

* Temi colori dell'editor 
* Frammenti di codice 
* Grammatiche per nuove lingue con evidenziazione abilitata e IntelliSense di base 

È possibile aggiungere questi bundle in **Preferenze > Editor di testo > Bundle lingua**. 

### <a name="color-theme-support"></a>Supporto dei temi colori 

In Visual Studio per Mac sono supportati i formati di tema colori seguenti: 

* Visual Studio (`.vssettings`) 
* Xamarin Studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) è uno strumento per la creazione di giochi che è possibile usare per creare giochi multipiattaforma 2D e 3D di alta qualità per tutte le piattaforme principali: dispositivi mobili, desktop, console, dispositivi AR e VR e persino per il Web. 

A partire da Unity 5.6.1, è possibile scrivere giochi Unity ed eseguirne il debug con Visual Studio per Mac. Per iniziare, impostare Visual Studio come editor di script di Unity 5.6.1. 

Tools per Unity include: 

* Supporto per gli script scritti in C#. 
* Riquadro della soluzione Unity. 
* Debug con un clic dell'editor di Unity. 
* Messaggi IntelliSense per Unity. 
* Colorazione del codice per gli shader di Unity. 
* Accesso alla documentazione di Unity. 

## <a name="xamarin"></a>Xamarin 

Mentre le funzionalità multipiattaforma di Xamarin sono sempre state il fiore all'occhiello di Xamarin Studio, alcune funzionalità di Xamarin sono disponibili solo in Visual Studio per Mac 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O sarà supportato solo in Visual Studio per Mac, non in Xamarin Studio 

### <a name="ios-and-mac"></a>iOS e Mac 

* [Aggiornamenti del flusso di lavoro di firma di iOS](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Creare identità di firma e installarle nella keychain locale. 
    * Creare profili di provisioning. 
    * Aggiungere un'identità di firma a un profilo esistente.
    *  Eseguire il provisioning di dispositivi: registrare un dispositivo nel portale Apple Developer e aggiungerlo a un profilo di provisioning.
* iOS 11, watchOS 4 e tvOS 2 saranno supportati solo in Visual Studio per Mac, non in Xamarin Studio 
* MacOS High Sierra sarà supportato solo in Visual Studio per Mac, non in Xamarin Studio 

### <a name="cross-platform"></a>Multipiattaforma 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**Anteprima**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**Anteprima**) 
 