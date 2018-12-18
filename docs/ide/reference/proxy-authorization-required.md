---
title: Correzione degli errori di autorizzazione del proxy richiesta | Microsoft Docs
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="proxy-authorization-required"></a>Autorizzazione del proxy richiesta

Generalmente questo errore si verifica quando gli utenti sono connessi a Internet tramite un server proxy e quest'ultimo blocca le chiamate di Visual Studio ad alcune risorse di rete.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali nella finestra di dialogo.

- Se il passaggio precedente non risolve il problema, è possibile che il server proxy usato richieda le credenziali per gli indirizzi http://go.microsoft.com, ma non per gli indirizzi *.visualStudio.com. Per questi server è necessario aggiungere l'elenco seguente di URL all'elenco di elementi consentiti per sbloccare tutti gli scenari di accesso in Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- In caso contrario, è possibile rimuovere l'indirizzo http://go.microsoft.com dall'elenco degli elementi consentiti in modo che al riavvio di Visual Studio venga visualizzata la finestra di dialogo di autenticazione del proxy per l'indirizzo http://go.microsoft.com e gli endpoint server.

    OR

- Se si desidera usare le credenziali predefinite con il proxy, è possibile eseguire le operazioni seguenti:

    1. Individuare **devenv.exe.config** (il file di configurazione di devenv.exe) in: **%Programmi%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. Nel file di configurazione trovare il blocco `<system.net>` e aggiungere il codice seguente:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.

    OR

- Si possono anche seguire le istruzioni in [questo post](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) per aggiungere il codice che consente di usare il proxy.
