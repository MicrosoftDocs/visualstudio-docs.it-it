---
title: 'Errore: Microsoft Visual Studio Remote Debugging Monitor nel computer remoto è in esecuzione come utente diverso | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2bdc731b65a8d451b6882914e8bed1abca2139b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
 Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso.  
  
## <a name="cause"></a>Causa  
 Questo messaggio viene visualizzato quando si esegue il debug in modalità Nessuna autenticazione e l'utente che ha avviato msvsmon non è lo stesso che esegue Visual Studio.  
  
## <a name="solution"></a>Soluzione  
 La soluzione ottimale, anche dal punto di vista della sicurezza, consiste nell'eseguire Remote Debugging Monitor (msvsmon.exe) utilizzando lo stesso account utente di Visual Studio. Se non è, è possibile eseguire Remote Debugging Monitor utilizzando l'altro account con il **consentire agli utenti di eseguire il debug** opzione selezionata in Remote Debugging Monitor **opzioni** la finestra di dialogo.  
  
> [!CAUTION]
>  Se si concede ad altri utenti l'autorizzazione per la connessione, è possibile che si verifichino problemi di connessione alla sessione di debug remoto errata. Debug in **Nessuna autenticazione** modalità non è sicura e deve essere utilizzata con cautela.
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)