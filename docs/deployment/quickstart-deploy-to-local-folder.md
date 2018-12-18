---
title: Distribuire in una cartella locale, Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e575a6d885b079c1c5afd0af6cbdadcd1d38d96
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Distribuire un'app web o .NET Core in una cartella locale utilizzando lo strumento di pubblicazione di Visual Studio

È possibile utilizzare il **pubblica** strumento per pubblicare l'app in una cartella locale. 

Questa procedura si applica a ASP.NET, ASP.NET di base, .NET Core e Python App in Visual Studio. Per Node.js, sono supportati i passaggi, ma l'interfaccia utente è diverso.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. In **Visual c#** o **Visual Basic**, scegliere **.NET Core**, quindi nel riquadro centrale scegliere **applicazione Console (.NET Core)**.

1. Digitare un nome come **MyLocalApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

## <a name="deploy-to-a-local-folder"></a>Distribuire in una cartella locale

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

    ![Scegliere Pubblica](../deployment/media/quickstart-publish.png "scegliere pubblica")

1. Nel **pubblica** riquadro scegliere **cartella**.

    ![Scegliere una cartella](../deployment/media/quickstart-publish-folder.png "scegliere cartella")

1. Immettere un percorso o fare clic su **Sfoglia** per selezionare una cartella locale.

1. Fare clic su **Pubblica**.

    Visual Studio compila il progetto e verrà pubblicato nella cartella specificata.

    Il riquadro di pubblicazione viene illustrato un profilo di riepilogo.

1. Per configurare le impostazioni di distribuzione, fare clic su **impostazioni** nel profilo di riepilogo.

    ![Impostazioni del profilo](../deployment/media/quickstart-profile-settings.png "impostazioni del profilo") 

1. Configurare le opzioni, ad esempio se distribuire una configurazione di Debug o Release e quindi fare clic su **salvare**.

1. Per pubblicare, fare clic su **pubblica**.

Distribuire i file pubblicati con il metodo desiderato. Ad esempio, è possibile includerli in un file Zip, usare un comando di copia semplice o distribuirli con qualsiasi pacchetto di installazione di propria scelta.

## <a name="next-steps"></a>Passaggi successivi

- [Distribuire un'applicazione .NET Core con lo strumento di pubblicazione](/dotnet/core/deploying/deploy-with-vs)
- [Creare un pacchetto dell'applicazione desktop per Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Distribuire .NET Framework e applicazioni](/dotnet/framework/deployment/)
