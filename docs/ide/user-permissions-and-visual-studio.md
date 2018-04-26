---
title: Autorizzazioni utente e Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96835e0f884494f4a6b94aa1a311b40e8a9d8ad9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio

Per motivi di sicurezza è necessario, quando possibile, eseguire Visual Studio come utente normale.

> [!WARNING]
> Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.

È possibile usare quasi tutte le funzioni dell'IDE di Visual Studio come utente normale, tuttavia è necessario disporre delle autorizzazioni di amministratore per completare le seguenti attività:

|Area|Attività|Per altre informazioni|
|----------|----------|--------------------------|
|Installazione|Installare Visual Studio.|[Installare Visual Studio](../install/install-visual-studio.md)|
||Installazione, aggiornamento o rimozione del contenuto della Guida locale.|[Installare e gestire il contenuto locale](../ide/install-and-manage-local-content.md)|
|Tipi di applicazioni|Sviluppo di soluzioni per SharePoint.|[Requisiti per lo sviluppo di soluzioni SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|
||Acquisizione di una licenza per sviluppatori per [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Ottenere una licenza per sviluppatori](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Casella degli strumenti|Aggiunta di controlli COM classici alla **casella degli strumenti**.|[Casella degli strumenti](../ide/reference/toolbox.md)|
|Componenti aggiuntivi|Installazione e utilizzo di componenti aggiuntivi scritti tramite COM classico nell'IDE.|[Creazione di componenti aggiuntivi e di procedure guidate](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilazione|Utilizzo di eventi di post-compilazione che registrano un componente.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Aggiunta di un passaggio di registrazione durante la compilazione di progetti C++.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|Debug|Debug di applicazioni eseguite con autorizzazioni elevate.|[Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)|
||Debug di applicazioni eseguite con un account utente diverso, come i siti Web ASP.NET.|[Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debug nell'area di sicurezza per applicazioni browser XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Utilizzo dell'emulatore per eseguire il debug di progetti di servizio cloud per Microsoft Azure.|[Debug di un servizio cloud in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Configurazione di un firewall per il debug remoto.|[Debug remoto](../debugger/remote-debugging.md)|
|Strumenti per le prestazioni|Profilatura di un'applicazione.|[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)|
|Distribuzione|Distribuzione di un'applicazione Web in Internet Information Services (IIS) su un computer locale.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment](http://go.microsoft.com/fwlink/?LinkId=266478) (Distribuzione di un'applicazione Web ASP.NET a un provider di hosting usando Visual Studio o Visual Web Developer: distribuzione a IIS come ambiente di test)|

## <a name="running-visual-studio-as-an-administrator"></a>Esecuzione di Visual Studio come amministratore

È possibile avviare Visual Studio con autorizzazioni amministrative ogni volta che si avvia l'IDE oppure modificare il collegamento dell'applicazione in modo che venga eseguita sempre con autorizzazioni amministrative. Per altre informazioni, vedere la Guida di Windows.

### <a name="to-run-visual-studio-with-administrative-permissions"></a>Per eseguire Visual Studio con autorizzazioni amministrative

Queste istruzioni sono relative a Windows 10. Sono simili per le altre versioni di Windows.

1. Aprire il menu **Start** e scorrere fino Visual Studio 2017.

1. Dal menu di scelta rapida o contestuale di **Visual Studio 2017** scegliere **Altro** > **Esegui come amministratore**.

     All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

## <a name="see-also"></a>Vedere anche

- [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Installare Visual Studio](../install/install-visual-studio.md)