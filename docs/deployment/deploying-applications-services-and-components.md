---
title: Panoramica della distribuzione - Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e05bf361515b45f3ebc7683fa0c83ec6116d9419
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-overview-in-visual-studio"></a>Panoramica della distribuzione in Visual Studio

Mediante la distribuzione, un'applicazione, un servizio o un componente viene distribuito per l'installazione in altri computer, dispositivi, server o nel cloud. Il metodo appropriato viene scelto in Visual Studio per il tipo di distribuzione necessaria. (Molti tipi di app supportano altri strumenti di distribuzione, ad esempio la distribuzione della riga di comando o NuGet che non sono descritte di seguito).

Vedere le esercitazioni per istruzioni dettagliate.

### <a name="deploy-to-local-folder"></a>Distribuire nella cartella locale

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, e **.NET Core**: utilizzare lo strumento di pubblicazione per distribuire a una variabile locale cartella. Le opzioni disponibili dipendono dal tipo di app. In Esplora risorse, mouse sul progetto e scegliere **pubblica**, quindi scegliere **cartella**. Per ulteriori informazioni, vedere [Distribuisci in una cartella locale](quickstart-deploy-to-local-folder.md).

    ![Scegliere Pubblica](../deployment/media/quickstart-publish.png)

- **Runtime di Visual C++**: È possibile distribuire il runtime di Visual C++ tramite la distribuzione locale o collegamento statico. Per ulteriori informazioni, vedere [la distribuzione di applicazioni Desktop Native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Pubblicazione sul Web o di distribuire in una condivisione di rete

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, e **.NET Core**: È possibile utilizzare lo strumento di pubblicazione per distribuire un sito Web tramite FTP o distribuzione Web. Per ulteriori informazioni, vedere [distribuzione a un sito web](quickstart-deploy-to-a-web-site.md).

    In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. Nello strumento di pubblicazione, scegliere l'opzione desiderato e quindi seguire i passaggi di configurazione.

    ![Scegliere IIS, FTP e così via.](../deployment/media/quickstart-publish-iis-ftp.png)

    È anche possibile distribuire applicazioni ASP.NET e servizi in diversi altri modi. Per ulteriori informazioni, vedere [servizi e applicazioni web ASP.NET distribuzione](http://www.asp.net/aspnet/overview/deployment).

- **Runtime di Visual C++**: È possibile distribuire il runtime di Visual C++ utilizzando la distribuzione centrale. Per ulteriori informazioni, vedere [la distribuzione di applicazioni Desktop Native (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Desktop Windows** è possibile pubblicare un'applicazione desktop di Windows in un server web o una condivisione di file di rete tramite la distribuzione ClickOnce. Gli utenti possono quindi installare l'applicazione con un solo clic. Per ulteriori informazioni, vedere [distribuire un'applicazione desktop tramite ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) e [distribuire un'applicazione nativa utilizzando ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Pubblicare in Azure

- **ASP.NET, ASP.NET Core, Python, Node.js e .NET Core** applicazioni web: È possibile utilizzare lo strumento di pubblicazione per distribuire rapidamente applicazioni di servizio App di Azure o a una macchina virtuale di Azure. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. Nella finestra di dialogo Pubblica scegliere **servizio App di Microsoft Azure** o **macchine virtuali di Microsoft Azure**, quindi seguire i passaggi di configurazione.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-azure.png "scegliere servizio App di Azure")

    Per pubblicare una macchina virtuale di Azure, scorrere verso destra e selezionare **macchine virtuali di Microsoft Azure**.

    Per una rapida introduzione, vedere [Publish to Azure](quickstart-deploy-to-azure.md). Vedere anche [pubblicare un'applicazione ASP.NET di base in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Per la distribuzione usando Git, vedere [la distribuzione continua di ASP.NET Core in Azure con Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Se si dispone già di un account Azure, è possibile [iscriverti qui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Altri **servizi di Azure**: vedere la specifica [servizio Azure](/azure/#pivot=products) documentazione per diverse opzioni di distribuzione che possono essere supportati da Visual Studio.

### <a name="publish-to-microsoft-store"></a>Pubblicare in Microsoft Store

Da Visual Studio, è possibile creare pacchetti di app per la distribuzione in Microsoft Store.

- **UWP**: È possibile pacchetto dell'app e distribuirlo utilizzando le voci di menu. Per ulteriori informazioni, vedere [il pacchetto di un'app UWP tramite Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Creare un pacchetto dell'app](../deployment/media/feature-tour-create-app-package.jpg)

- **Desktop Windows**: È possibile distribuire a Microsoft Store usando il Bridge Desktop a partire da Visual Studio 2017 versione 15.4. A tale scopo, creare innanzitutto un progetto di creazione del pacchetto di applicazione Windows. Per ulteriori informazioni, vedere [pacchetto di un'applicazione desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Bridge desktop](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Creare un pacchetto di installazione (client di Windows)

- È possibile creare un programma di installazione WiX basate su MSI utilizzando il [WiX set di strumenti di Visual Studio 2017 estensione](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) da Flexera Software possono essere utilizzate con Visual Studio 2017 (Community Edition non è supportata). Si noti che InstallShield Limited Edition non è più incluso in Visual Studio e non sono supportato in Visual Studio 2017; controllare con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sulla disponibilità future.

- Se si desidera creare un progetto di installazione (vdproj), installare il [estensione di progetti di installazione di Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- È possibile installare componenti dei prerequisiti per le applicazioni desktop configurando un programma di installazione generico, noto come un programma di avvio automatico. Per ulteriori informazioni, vedere [prerequisiti di distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Distribuire per eseguire il test lab

È possibile abilitare più sofisticate di sviluppo e test per la distribuzione di applicazioni in ambienti virtuali. Per ulteriori informazioni, vedere [Test in un ambiente lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>Distribuzione DevOps

In un ambiente di team, è possibile utilizzare Visual Studio Team Services (VSTS) per abilitare la distribuzione continua dell'app. Per ulteriori informazioni, vedere [di compilazione e versione](/vsts/build-release/index) e [Distribuisci in Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Distribuzione per gli altri tipi di app

| Tipo di app | Scenario di distribuzione | Collegamento |
| --- | --- | --- |
| **App di Office** | È possibile pubblicare un componente aggiuntivo per Office in Visual Studio. | [Distribuire e pubblicare il componente aggiuntivo di Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servizio WCF o OData**  | Altre applicazioni possono utilizzare servizi WCF RIA distribuiti in un server web. | [Sviluppo e distribuzione di WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch non è più supportata in Visual Studio 2017, ma può ancora essere distribuito da Visual Studio 2015 e versioni precedenti. | [Distribuzione di applicazioni LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

