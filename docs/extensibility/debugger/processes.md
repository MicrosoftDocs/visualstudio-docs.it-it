---
title: Processi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e69270c5d90c26cf653ee31b81bcb9f453b814e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="processes"></a>Processi
In termini di architettura del debugger, un **processo**:  
  
-   È un contenitore per un gruppo di programmi. È strettamente analoga a un processo di Windows, che è un contenitore per un set di thread.  
  
-   Grado di identificarsi per nome, identificatore o identificatore fisico.  
  
-   Possibile enumerare tutti i programmi in esecuzione (e i thread).  
  
-   Può descrivere se stesso, la porta in che è in esecuzione e il computer che lo contiene.  
  
-   Può creare uno o più programmi, terminare tutti i programmi viene creato o provocare un programma.  
  
-   È rappresentato da un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaccia, viene creato quando viene avviato il processo. Un processo viene avviato per la gestione a debug sessione (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Il pacchetto di debug può connettersi un motore di debug (DE) a un processo chiamando [collegamento](../../extensibility/debugger/reference/idebugprocess2-attach.md). Ciò significa che la Germania associa tutti i programmi possibili in esecuzione nel processo in grado di gestire. Ad esempio, se common language runtime DE si connette a un processo, allega solo per i programmi che eseguono codice gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)