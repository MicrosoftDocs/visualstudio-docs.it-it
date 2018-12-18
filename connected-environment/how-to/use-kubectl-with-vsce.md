---
title: Come usare kubectl con Connected Environment | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usare `kubectl` con Connected Environment

È possibile accedere al cluster Kubernetes all'interno di un ambiente Connected Environment e usare strumenti esistenti di Kubernetes come `kubectl`.

L'esecuzione di `vsce env create` o `vsce env select` aggiungerà automaticamente un contesto di configurazione `kubectl` per l'utente, quindi kubectl deve essere già connesso al cluster VSCE Kubernetes. Esempi:
- Confermare il contesto corrente: `kubectl config current-context`
- Elencare tutti i contesti disponibili: `kubectl config get-contexts`. Il nome di un cluster Kubernetes creato da VSCE sarà nel formato "vsce -<guid>".
- Modificare il contesto: `kubectl config use-context <context-name>`
- Visualizzare il dashboard di Kubernetes: eseguire `kubectl proxy`, quindi aprire il browser all'indirizzo restituito da questo comando (accodare `/ui` all'URL per passare al dashboard di Kubernetes).
- Elencare i servizi in esecuzione nello spazio VSCE predefinito denominato *mainline*: `kubectl get services --namespace=mainline`

