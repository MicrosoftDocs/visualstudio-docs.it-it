---
title: 'Procedura: trovare il nome del processo ASP.NET | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e542e58bab483a1f20029bb66a073ae07d45afba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Procedura: individuare il nome del processo ASP.NET
Per connettersi a un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in esecuzione, è necessario conoscere il nome del processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  

-   Se si esegue ASP.NET Core in IIS o IIS Express, il nome del processo è dotnet.exe.

-   Se si esegue ASP.NET in IIS 6.0 in un secondo momento, il nome sarà w3wp.exe.  
  
-   Se si esegue ASP.NET in una versione precedente di IIS, il nome è aspnet_wp.exe.

-   Se si esegue ASP.NET in IIS Express, il nome è iisexpress.exe.
  
Per le applicazioni compilate con le versioni di Visual Studio precedenti a Visual Studio 2012, la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] codice può risiedere nel file system ed essere il server di prova WebDev.WebServer.exe o WebDev.WebServer40.exe. In tal caso, è necessario allegare di WebDev.WebServer.exe o WebDev.WebServer40.exe anziché il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo. Questo scenario è valido solo per il debug locale.
  
Le applicazioni ASP più obsolete vengono eseguite nel processo IIS inetinfo.exe quando sono in esecuzione all'interno del processo.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Per determinare la versione di IIS in cui l'applicazione è in esecuzione  

1.  Assicurarsi che l'applicazione è in esecuzione e quindi da Visual Studio, usare il [Connetti a processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) comando.

2.  Digitare la prima lettera del nome di un processo come w3wp.exe per trovare rapidamente i processi di **processi disponibili** elenco.

    I processi disponibili in questo argomento nell'elenco indica le versioni di IIS sono disponibili, il processo che esegue l'applicazione.

    > [!NOTE]
    > A partire da Visual Studio 2017, è possibile utilizzare la casella di ricerca per cercare il nome del processo.
  
## <a name="see-also"></a>Vedere anche  
 [Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Prerequisiti per il debug di applicazioni Web remoto](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)