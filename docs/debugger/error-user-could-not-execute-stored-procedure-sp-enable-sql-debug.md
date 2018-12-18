---
title: 'Errore: Utente potrebbe non eseguire la Stored Procedure sp_enable_sql_debug | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e36c56f594b9858334f3b67042183278afa218df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug
Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:  
  
-   Un problema di connessione. È necessario disporre di una connessione stabile al server.  
  
-   Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.  
  
 Per ulteriori informazioni, vedere [procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Impostazione del debug SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)