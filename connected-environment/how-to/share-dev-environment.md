---
title: Come condividere un ambiente di sviluppo | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>Condividere un ambiente di sviluppo

Con Connected Environment è possibile condividere l'ambiente di sviluppo con altri utenti nel team. Ogni sviluppatore può utilizzare uno spazio personale senza timore di disturbare il lavoro dei colleghi. Inoltre, la collaborazione in un singolo ambiente può consentire di eseguire test completi del codice senza dover creare mockup o simulare le dipendenze. Per altre informazioni, vedere la guida [Informazioni sullo sviluppo in team](../get-started-nodejs-06.md).

Per impostare un ambiente per più sviluppatori:
1. [Creare un ambiente Connected Environment in Azure](../get-started.md). È necessario disporre dell'accesso come Proprietario o Collaboratore per la sottoscrizione di Azure selezionata.
1. Configurare il **gruppo di risorse** dell'ambiente in modo da [concedere l'accesso come Collaboratore](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) a ogni membro del team. Per controllare il gruppo di risorse di un ambiente, è possibile eseguire questo comando: `vsce env list`
1. Chiedere ai membri del team di **selezionare l'ambiente** in cui eseguire le attività di sviluppo.
     * **Riga di comando o Visual Studio Code**: per visualizzare gli ambienti Connected Environment esistenti a cui si ha accesso: `vsce env list`. Per selezionare un ambiente: `vsce env select`.
     * **IDE di Visual Studio**: aprire un progetto in Visual Studio, selezionare **Connected Environment for AKS** (Ambiente connesso per AKS) dall'elenco a discesa delle impostazioni di avvio. Nella finestra di dialogo visualizzata selezionare un ambiente di sviluppo esistente.

![Elenco a discesa delle impostazioni di avvio di Visual Studio](../images/LaunchSettings.png)