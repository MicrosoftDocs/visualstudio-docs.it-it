---
title: Eseguire il debug pacchetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ca438b7ed8c9b6a4b84693f975144040f998f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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