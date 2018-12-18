---
title: Collegamento al programma | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75b532005bf4aeb471aa16ecfc6ac8ff508e3c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-to-the-program"></a>Collegamento al programma
Dopo avere registrato i programmi con la porta appropriata, è necessario connettere il debugger al programma che si desidera eseguire il debug.  
  
## <a name="choosing-how-to-attach"></a>Scelta di collegamento  
 Esistono tre modi in cui gestore di sessione di debug (SDM) tenta di collegare al programma in fase di debug.  
  
1.  Per i programmi che vengono avviati dal motore di debug tramite il [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo (tipica dei linguaggi interpretati, ad esempio), il SDM Ottiene il [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia da il [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associata al programma da connettere all'oggetto. Se il SDM può ottenere il `IDebugProgramNodeAttach2` interfaccia, chiama quindi il SDM il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo. Il `IDebugProgramNodeAttach2::OnAttach` restituisce `S_OK` per indicare che non è stato allegato al programma e che possono essere eseguiti altri tentativi per collegare al programma.  
  
2.  Se il SDM può ottenere il [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfaccia dal programma di cui viene associato, le chiamate SDM il [Connetti](../../extensibility/debugger/reference/idebugprogramex2-attach.md) (metodo). Questo approccio è tipico per i programmi che sono stati avviati in modalità remota dal fornitore porta.  
  
3.  Se il programma non può essere collegato tramite il `IDebugProgramNodeAttach2::OnAttach` o `IDebugProgramEx2::Attach` metodi, il SDM carica il motore di debug (se non è già caricato) chiamando il `CoCreateInstance` (funzione) e quindi chiama il [collegamento](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo. Questo approccio è tipico per i programmi localmente avviati da un fornitore di porta.  
  
     È inoltre possibile per un fornitore di porta personalizzato chiamare il `IDebugEngine2::Attach` nell'implementazione del fornitore porta personalizzata del metodo di `IDebugProgramEx2::Attach` metodo. In genere in questo caso, il fornitore della porta personalizzata consente di avviare il motore di debug nel computer remoto.  
  
 Allegato avviene quando il gestore di sessione di debug (SDM) chiama il [collegamento](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.  
  
 Se si esegue la Germania nello stesso processo dell'applicazione da sottoporre a debug, quindi è necessario implementare i metodi seguenti della [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Dopo il `IDebugEngine2::Attach` metodo viene chiamato, seguire questi passaggi nell'implementazione del `IDebugEngine2::Attach` metodo:  
  
1.  Inviare un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto evento per il SDM. Per ulteriori informazioni, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2.  Chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto passato per il `IDebugEngine2::Attach` (metodo).  
  
     Restituisce un `GUID` che viene utilizzato per identificare il programma. Il `GUID` devono essere archiviate nell'oggetto che rappresenta il programma di locale per la Germania e deve essere restituito quando il `IDebugProgram2::GetProgramId` metodo viene chiamato sul `IDebugProgram2` interfaccia.  
  
    > [!NOTE]
    >  Se si implementa il `IDebugProgramNodeAttach2` interfaccia, il programma `GUID` viene passato per il `IDebugProgramNodeAttach2::OnAttach` metodo. Questo `GUID` viene utilizzato per il programma `GUID` restituito dal `IDebugProgram2::GetProgramId` metodo.  
  
3.  Inviare un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) oggetto evento per notificare il SDM che locale `IDebugProgram2` oggetto è stato creato per rappresentare il programma per la Germania. Per informazioni dettagliate, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Questo non è lo stesso `IDebugProgram2` oggetto che è stato passato il `IDebugEngine2::Attach` metodo. Il valore passato in precedenza `IDebugProgram2` oggetto riconosciuto da solo la porta e un oggetto separato.  
  
## <a name="see-also"></a>Vedere anche  
 [Basato su avvio allegato](../../extensibility/debugger/launch-based-attachment.md)   
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Collegare](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)