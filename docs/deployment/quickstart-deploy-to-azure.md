---
title: Pubblicare in Azure App Service - Visual Studio | Documenti Microsoft
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
ms.workload: azure
ms.openlocfilehash: 52da1a2e618d9ececa1c8fd0d90a86e651cd7fde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Pubblicare un'applicazione ASP.NET o ASP.NET Core servizio App di Azure con Visual Studio

È possibile utilizzare il **pubblica** strumento per pubblicare le applicazioni ASP.NET, ASP.NET Core, Python, Node.js e .NET Core servizio App di Azure.

Se si dispone già di un account Azure, è possibile [iscriverti qui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)**(solo c#) o **applicazione Web di ASP.NET Core**, quindi fare clic su **OK**.

1. Scegliere **MVC**, assicurarsi che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Scegliere Pubblica](../deployment/media/quickstart-publish-aspnet.png "scegliere pubblica")

1. Nel **pubblica** riquadro scegliere **servizio App di Microsoft Azure**.

    ![Scegliere servizio App di Azure](../deployment/media/quickstart-publish-azure.png "scegliere servizio App di Azure")

1. Fare clic su **Pubblica**.

    Il **Crea servizio App** viene visualizzata la finestra di dialogo.

    ![Creare il servizio App](../deployment/media/quickstart-publish-settings-app-service.png "creare servizio App di Azure")
    
1. Se non è firmato in Visual Studio, eseguire l'accesso e le impostazioni di servizio app predefinite popolano i campi.

    Il profilo delle impostazioni viene visualizzata la finestra di dialogo di pubblicazione.

    ![Scegliere una cartella](../deployment/media/quickstart-publish-settings-web.png "scegliere cartella")

    Nella finestra di dialogo, è possibile selezionare la sottoscrizione in uso, selezionare o creare un gruppo di risorse e così via.

1. Scegliere **Crea**.

    Visual Studio distribuisce l'app del servizio App di Azure e carica l'app web nel browser.

    Nel riepilogo del **pubblica** riquadro, viene visualizzato l'URL del sito per il nuovo servizio App di Azure.

## <a name="next-steps"></a>Passaggi successivi

- [Distribuire un'applicazione ASP.NET di base in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Distribuzione continua di ASP.NET Core in Azure con Git](/aspnet/core/publishing/azure-continuous-deployment)
