---
title: Risoluzione dei problemi di debug remoto di Azure per Python | Microsoft Docs
description: Come risolvere i problemi durante il tentativo di eseguire il debug di un'applicazione Python in esecuzione in Servizio app di Azure con Visual Studio.
ms.custom: ''
ms.date: 07/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 92429ea893c4eccee75f3a70ffda44eac8f91aa9
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Risoluzione dei problemi di debug remoto per Python e Azure

Visual Studio non riesce a collegarsi a un [servizio app di Azure per il debug remoto](debugging-remote-python-code-on-azure.md) per uno qualsiasi dei motivi seguenti:

| Motivo | Risoluzione |
| --- | --- |
| Non sono disponibili Visual Studio 2013 Update 4 o versione successive. | Installare una versione appropriata da [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Il progetto distribuito nel servizio app non corrisponde a quello aperto in Visual Studio. | Caricare il progetto corretto in Visual Studio. |
| Il progetto non è stato distribuito con la configurazione per il debug. | Ridistribuire l'applicazione facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliendo **Pubblica**. Nella scheda **Impostazioni** assicurarsi che la configurazione selezionata sia **Debug**. |
| Il servizio app non è in esecuzione. | Avviarlo da Esplora Server in Visual Studio o dal portale di Azure. |
| Il servizio app non è configurato con WebSocket. | Passare al [portale di Azure](https://portal.azure.com) e al servizio app in questione, aprire il pannello **Impostazioni > Impostazioni applicazione**, impostare **Impostazioni generali > Web Socket** su **Attivato** e selezionare **Salva**. (Si noti che le opzioni **Debug** visualizzate in questo pannello *non* si applicano al debug Python.) |
| `web.debug.config` è stato modificato per disabilitare il proxy di debug. | Eliminare il file e ripubblicare il progetto nel servizio app. Durante l'operazione, Visual Studio ricrea il file. |

Vedere anche:

- [Debug remoto di codice Python in Azure](debugging-remote-python-code-on-azure.md)
