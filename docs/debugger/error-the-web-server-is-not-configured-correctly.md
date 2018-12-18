---
title: "Errore: Il server web non è configurato correttamente | Documenti Microsoft"
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bd7ea7deea749831ebf26d3f8a406b1e3ad63fb0
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Errore: il server Web non è configurato in modo corretto

Dopo avere eseguito i passaggi descritti in questa sezione per risolvere il problema e prima di tentare nuovamente di eseguire il debug, è inoltre necessario reimpostare IIS. È possibile farlo aprendo un prompt dei comandi di amministratore e digitando `iisreset`.

Eseguire la procedura per risolvere il problema:

1. Se l'app web ospitata nel server è configurato come una build di rilascio, pubblicare di nuovo come una build di Debug e verificare che il file Web. config contiene `debug=true` nell'elemento di compilazione. Reimpostare IIS, quindi riprovare.

    Ad esempio, se si utilizza un profilo di pubblicazione per una build di rilascio, modificarlo per eseguire il Debug e pubblicare di nuovo. In caso contrario, l'attributo di debug verrà impostata `false` quando si pubblica.

2. (IIS) Verificare che il percorso fisico sia corretto. In IIS, disponibile questa impostazione in **le impostazioni di base > percorso fisico** (o **impostazioni avanzate** nelle versioni precedenti di IIS).

    Il percorso fisico può essere corretto se l'applicazione web è stato copiato in un computer diverso, rinominato manualmente o spostato. Reimpostare IIS, quindi riprovare.

3. Se esegue il debug in locale in Visual Studio, verificare che il server corretto sia selezionato nelle proprietà. (Aprire **proprietà > Web > server** o **proprietà > Debug** a seconda del tipo di progetto. Per un progetto di Web Form, aprire **pagine delle proprietà > Opzioni di avvio > Server**).

    Se si utilizza un server (personalizzato) esterno, ad esempio IIS, l'URL deve essere corretto. In caso contrario, selezionare IIS Express e riprovare.

4. (IIS) Assicurarsi che la versione corretta di ASP.NET sia installata nel server.

    Le versioni non corrispondenti di ASP.NET in IIS e nel progetto di Visual Studio possono causare questo problema. Si potrebbe essere necessario impostare la versione del framework in Web. config. Per installare ASP.NET in IIS, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oppure, per ASP.NET Core, [Host su Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Se il `maxConnection` limite in IIS è troppo basso e si dispone di un numero eccessivo di connessioni, potrebbe essere necessario [aumentare il limite di connessione](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto di ASP.NET in un Computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)