---
title: La porta di notifica | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1420ca8768ddf1eaedc0d515810bc88b3491c4db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="notifying-the-port"></a>La porta di notifica
Dopo aver avviato un programma, la porta deve ricevere una notifica, come indicato di seguito:  
  
1.  Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma alla sessione di debug L'evento è caratterizzata da un'interfaccia che rappresenta il programma.  
  
2.  La sessione di debug del programma per l'identificatore di un motore di debug (DE) che è possibile collegare a una query.  
  
3.  La sessione di debug controlla se la Germania sia incluso nell'elenco di DEs consentito per il programma. La sessione di debug, tale elenco viene dalle impostazioni del programma attivo della soluzione, origine passate al metodo tramite il pacchetto di debug.  
  
     La Germania deve essere presente nell'elenco consentito, altrimenti la Germania non verrà collegato al programma.  
  
 A livello di codice quando una porta riceve un nuovo nodo di programma, viene creato un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per rappresentare il programma.  
  
> [!NOTE]
>  Non deve essere confuso con il `IDebugProgram2` interfaccia creata in un secondo momento dal motore di debug (DE).  
  
 La porta invia un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento di creazione di programma al gestore di debug di sessione (SDM) tramite COM `IConnectionPoint` interfaccia.  
  
> [!NOTE]
>  Non deve essere confuso con il `IDebugProgramCreateEvent2` interfaccia, che viene inviato in un secondo momento per la Germania.  
  
 Con l'interfaccia di evento stessa, la porta invia il [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfacce che rappresentano la porta, elaborano, e programma, rispettivamente. Le chiamate SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID della DE che è possibile eseguire il debug del programma. Il GUID è stato ottenuto in origine dal [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia.  
  
 Il SDM controlla se la Germania sia incluso nell'elenco di DEs consentito. Il SDM ottiene questo elenco dalle impostazioni del programma attivo della soluzione, origine passate al metodo tramite il pacchetto di debug. La Germania deve essere presente nell'elenco consentito, altrimenti non verrà collegato al programma.  
  
 Una volta che l'identità della DE è nota, il SDM è pronto per collegarlo al programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Un programma di avvio](../../extensibility/debugger/launching-a-program.md)   
 [Dopo il lancio di un collegamento di](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)