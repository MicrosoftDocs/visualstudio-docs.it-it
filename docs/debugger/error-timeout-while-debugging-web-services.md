---
title: 'Errore: Timeout durante il debug di servizi Web | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 25b53910dd51dc9535ee2e9e6009fb435bd70735
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-timeout-while-debugging-web-services"></a>Errore: timeout durante il debug dei servizi Web
Durante l'accesso a un servizio Web XML dal codice chiamante, è possibile che si verifichi un timeout con conseguente interruzione del debug. Potrebbe essere visualizzato un messaggio di errore simile al seguente.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Soluzione  
 Per evitare che si verifichi questo problema, impostare il valore di timeout per la chiamata al servizio Web XML su un valore infinito, come illustrato nell'esempio riportato di seguito:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)