---
title: Pubblicare un sito Web - Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e324869eb90cd60cba68d9ed7b2e3fdb1ebb588d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Pubblicare un'app web o un'applicazione .NET Core in un sito web tramite lo strumento di pubblicazione di Visual Studio

È possibile utilizzare il **pubblica** strumento per la pubblicazione di applicazioni ASP.NET in un sito Web.

Questa procedura si applica a ASP.NET, ASP.NET di base, .NET Core e Python App in Visual Studio. Per Node.js, sono supportati i passaggi, ma l'interfaccia utente è diverso.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web di ASP.NET Core**, quindi fare clic su **OK**.

1. Scegliere **MVC**, assicurarsi che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="publish-to-a-web-site"></a>Pubblicare un sito web

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Scegliere Pubblica](../deployment/media/quickstart-publish-aspnet.png "scegliere pubblica")

1. Nel **pubblica** riquadro scegliere **IIS, FTP, e così via**.

    ![Scegliere di IIS, FTP e così via](../deployment/media/quickstart-publish-iis-ftp.png "scegliere IIS, FTP e così via.")

1. Fare clic su **Pubblica**.

    Il profilo delle impostazioni viene visualizzata la finestra di dialogo di pubblicazione.

    ![Scegliere una cartella](../deployment/media/quickstart-publish-settings-web.png "scegliere cartella")

1. Nel **metodo di pubblicazione** campo, scegliere un metodo, ad esempio **distribuzione Web** o **FTP**.

    Le impostazioni visualizzate accanto corrispondono al metodo di pubblicazione.

1. Configurare le impostazioni necessarie per il metodo di pubblicazione e fare clic su **convalida connessione**.

    Se il server o destinazione sia disponibile e le impostazioni siano corrette, si verrà visualizzato un messaggio che indica la connessione viene convalidato e si è pronti per la pubblicazione.

    ![Convalidare la connessione a](../deployment/media/quickstart-publish-web-deploy.png "convalidare la connessione a")

1. Se si desidera configurare altre impostazioni di distribuzione, fare clic su **impostazioni**.

    È possibile configurare opzioni, ad esempio se distribuire una configurazione di Debug o Release e quindi fare clic su **salvare**. Se si esegue il debug in modalità remota, è necessario una configurazione di Debug.

1. Per pubblicare, fare clic su **pubblica**.

    La finestra di Output Mostra i risultati e l'avanzamento della distribuzione.

## <a name="next-steps"></a>Passaggi successivi

- [Distribuire ASP.NET in IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
