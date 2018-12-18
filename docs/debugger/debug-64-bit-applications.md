---
title: Eseguire il debug di applicazioni a 64 Bit | Documenti Microsoft
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
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5c3840cc7d43c3e30dda0317674ffb8cd664a262
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-64-bit-applications"></a>Eseguire il debug di applicazioni a 64 bit
È possibile eseguire il debug di un'applicazione a 64 bit in esecuzione nel computer locale o in un computer remoto.  
  
 Per eseguire il debug di un'applicazione a 64 bit in esecuzione in un computer remoto, vedere [Remote Debugging](../debugger/remote-debugging.md).  
  
 Per eseguire il debug delle applicazioni a 64 bit in locale, Visual Studio usa un processo di lavoro a 64 bit (msvsmon.exe) per eseguire le operazioni a basso livello che non possono essere eseguite all'interno del processo di Visual Studio a 32 bit.  
  
 Il debug in modalità mista non è supportato per i processi a 64 bit che usano .NET Framework 3.5 o versioni precedenti.  
  
## <a name="debug-a-64-bit-application"></a>Debug di un'applicazione a 64 bit  
 Per provare a eseguire il debug di applicazioni a 64 bit:  
  
1.  Creare una soluzione di Visual Studio, ad esempio un'applicazione console C#.  
  
2.  Impostare la configurazione su 64 bit tramite Gestione configurazione. Per altre informazioni, vedere [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  A questo punto verrà avviata la versione a 64 bit del debugger remoto (msvsmon.exe). Questa viene eseguita finché la soluzione con la configurazione a 64 bit è aperta.  
  
4.  Avviare il debug. L'esperienza dovrebbe corrispondere a quella di una configurazione a 32 bit. Se si verificano errori, vedere la sezione relativa alla risoluzione dei problemi di seguito.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Risoluzione dei problemi di debug a 64 bit  
 Potrebbe essere visualizzato un errore: "un'operazione di debug a 64 bit richiede più tempo del previsto." In questo caso, Visual Studio ha inviato una richiesta alla versione a 64 bit di msvsmon.exe ed è stato necessario molto tempo per la restituzione del risultato di tale richiesta.  
  
 Questo errore può avere due cause principali:  
  
-   Nel computer è installato software di sicurezza di rete che ha reso non affidabile lo stack di rete e ha eliminato alcuni pacchetti trasmessi tramite localhost. Provare a disabilitare tutto il software di sicurezza di rete e determinare se questo consente di risolvere il problema. In questo caso, segnalare al fornitore del software di sicurezza di rete che il software interferisce con traffico di localhost.  
  
-   Si è verificato un blocco o un problema di prestazioni di Visual Studio. Se il problema si verifica regolarmente, è possibile raccogliere dump di Visual Studio (devenv.exe) e del processo di lavoro (msvsmon.exe) e inviarli a Microsoft. Per informazioni sulla segnalazione di un problema, vedere [How to Report a Problem with Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md).
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni a 64 bit](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Configurazione di programmi per 64 Bit](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Supporto a 64 bit di Visual Studio IDE](../ide/visual-studio-ide-64-bit-support.md)   
 [Utilizzo dei file di Dump](../debugger/using-dump-files.md)   
 [Debug remoto](../debugger/remote-debugging.md)