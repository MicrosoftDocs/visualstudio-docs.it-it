---
title: 'Errore: Il servizio di Visual Studio Remote Debugger nel computer di destinazione non è possibile connettersi a questo computer | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: 3cfd2db1e4bf5b87d12eb5d5ffcf94d06e142516
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Errore: il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer
Il messaggio di errore viene visualizzato per segnalare che l'account utente utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio non è in grado di eseguire l'autenticazione per la connessione al computer dal quale viene eseguito il debug.  
  
 Nella tabella riportata di seguito sono indicati gli account in grado di accedere al computer:  
  
|||||  
|-|-|-|-|  
||Account LocalSystem|Account di dominio|Account locali con lo stesso nome utente e la stessa password in entrambi i computer|  
|Entrambi i computer nello stesso dominio|Yes|Sì|Yes|  
|Entrambi i computer in domini con trust bidirezionale|No|No|Yes|  
|Uno o entrambi i computer in un gruppo di lavoro|No|No|Yes|  
|Computer in domini diversi|No|No|Yes|  
  
 Si tenga inoltre presente quanto segue:  
  
-   L'account utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio deve essere un account amministrativo nel computer remoto in modo da poter eseguire il debug di qualsiasi processo.  
  
-   È inoltre necessario concedere questo account il `Log on as a service` privilegi nel computer remoto che utilizza il **criteri di sicurezza locali** strumento di amministrazione.  
  
-   Se si intende utilizzare un accesso al computer con account locale, è necessario eseguire il servizio Debugger remoto di Visual Studio con un account locale.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Assicurarsi che il servizio Debugger remoto di Visual Studio sia configurato in modo corretto nel computer remoto. Per ulteriori informazioni, vedere [il debug remoto](../debugger/remote-debugging.md).  
  
2.  Eseguire il servizio Debugger remoto utilizzando un account in grado di accedere al computer host del debugger, come indicato nella tabella precedente.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Per aggiungere un privilegio "Accesso come servizio"  
  
1.  Nel **avviare** menu, scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo, scegliere **visualizzazione classica**, se necessario.  
  
3.  Fare doppio clic su **Strumenti di amministrazione**.  
  
4.  Nella finestra Strumenti di amministrazione, fare doppio clic su **criteri di sicurezza locali**.  
  
5.  Nel **impostazioni protezione locale** finestra, espandere il **criteri locali** cartella.  
  
6.  Fare clic su **Assegnazione diritti utente**.  
  
7.  Nel **criteri** colonna, fare doppio clic su **accedere come servizio** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nel **accedere come servizio** la finestra di dialogo.  
  
8.  Per aggiungere nuovi utenti, fare clic su di **Aggiungi utente o gruppo** pulsante.  
  
9. Al termine, fare clic su **OK**.  
  
### <a name="to-work-around-this-error"></a>Per risolvere il problema  
  
-   Eseguire Remote Debugging Monitor come applicazione anziché come servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)