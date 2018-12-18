---
title: Inserimento di URL nell'elenco elementi consentiti in una rete privata | Microsoft Docs
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="whitelisting-urls-in-a-private-network"></a>Inserimento di URL nell'elenco elementi consentiti in una rete privata

Se si usa Visual Studio in una rete privata che usa un'appliance di sicurezza, ad esempio un firewall, Visual Studio potrebbe non essere in grado di connettersi ad alcune risorse di rete. Queste risorse includono Visual Studio Team Services (VSTS) per l'accesso e la gestione delle licenze, NuGet e servizi di Azure. Se Visual Studio non è in grado di connettersi a una di queste risorse, viene visualizzato il messaggio di errore seguente:

  **Connessione sottostante chiusa: Errore imprevisto durante un'operazione di invio**

Visual Studio usa il protocollo Transport Layer Security (TLS) 1.2 per connettersi alle risorse di rete. Le appliance di sicurezza in alcune reti private bloccano determinate connessioni al server quando Visual Studio usa TLS 1.2. Per correggere l'errore, abilitare le connessioni per i seguenti URL:

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (per le connessioni di Azure)

- *.nuget.org (per le connessioni NuGet)

- *.visualstudio.com

- cdn.vsassets.io (host di contenuti della rete CDN)

- *.gallerycdn.vsassets.io (host di estensioni di Visual Studio Team Services)

- static2.sharepointonline.com (host di risorse usate da Visual Studio nel kit Office UI Fabric, ad esempio i tipi di carattere)

> [!NOTE]
> Gli URL di server NuGet gestiti in modo privato possono non essere inclusi nell'elenco precedente. Puoi controllare i server NuGet in uso aprendo %APPData%\Nuget\NuGet.Config.

## <a name="see-also"></a>Vedere anche

[Errore di autorizzazione del proxy richiesta](../ide/reference/proxy-authorization-required.md)  
[Installazione di Visual Studio protetto da un firewall o un server proxy](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
