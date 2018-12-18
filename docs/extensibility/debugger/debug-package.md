---
title: Eseguire il debug pacchetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2cbb124dcb2d2d7a0bbcba1bc57eb3c704dd770
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-package"></a>Eseguire il debug del pacchetto
Il pacchetto di debug viene eseguito nella shell di Visual Studio e gestisce tutti dell'interfaccia utente. Utilizza le interfacce di debug di Visual Studio e comunica con gestore di sessione di debug (SDM).  
  
 Gli eventi di interruzione inviati tramite il SDM passare dalla modalità di esecuzione nel debugger per modalità di interruzione e modificare lo stato attivo con il programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia lo stack frame e il thread dalle informazioni inviate dagli eventi.  
  
 Il pacchetto di debug non dispone di lingua o le dipendenze di ambiente di runtime. Non è necessario implementare o modificare il pacchetto di debug.  
  
 Il pacchetto di debug viene implementato da vsdebug.dll.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di Debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)