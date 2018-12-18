---
title: 'Errore: Esecuzione Transact-SQL terminata senza debug | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3ccb86621295bb102738e5154f30bd45c6db358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: esecuzione Transact-SQL terminata senza debug
Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug da SQL Server.  
  
 L'errore può essere dovuto a problemi di rete o a problemi su SQL Server, ma con maggiore probabilità è dovuto a un problema di autorizzazioni.  
  
 Questo problema riguarda due account:  
  
-   L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Nel caso di una connessione con autenticazione SQL, questo account non corrisponde necessariamente all'identità utilizzata per l'esecuzione di Visual Studio.  
  
 Per il debug SQL è necessario che l'account dell'applicazione corrisponda a quello di connessione oppure che sia sysadmin.  
  
 Se si utilizza un account di accesso SQL quale sa, l'account dell'applicazione deve essere configurato su SQL Server come sysadmin. Per impostazione predefinita, gli amministratori del computer sul quale è in esecuzione SQL Server sono configurati come account sysadmin.  
  
 Per correggere questo errore, è possibile:  
  
-   Verificare le impostazioni delle autorizzazioni. Per ulteriori informazioni, vedere [procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Assicurarsi che il debug SQL sia configurato correttamente.  
  
-   Consultare l'amministratore della rete o del database.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione del debug SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Procedura: impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Debug remoto](../debugger/remote-debugging.md)