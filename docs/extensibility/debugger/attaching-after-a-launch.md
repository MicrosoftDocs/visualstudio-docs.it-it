---
title: Dopo il lancio di un collegamento di | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 890023b8336f130cf3b8cfcfe640da46af9cf0d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-after-a-launch"></a>Dopo il lancio di un collegamento di
Dopo che è stato avviato un programma, la sessione di debug è possibile collegare il motore di debug (DE) a tale programma.  
  
## <a name="design-decisions"></a>Decisioni di progettazione  
 Poiché la comunicazione è più semplice in uno spazio di indirizzi condiviso, è necessario decidere se è opportuno per facilitare la comunicazione tra la sessione di debug e la Germania, o tra la Germania e il programma. Scegliere tra le operazioni seguenti:  
  
-   Se è opportuno per facilitare la comunicazione tra la sessione di debug e la Germania, la sessione di debug creato la Germania e DE per collegare il programma richiesto. In questo modo la sessione di debug e DE insieme in uno spazio degli indirizzi e l'ambiente di runtime e il programma riuniti in un altro.  
  
-   Se è opportuno per facilitare la comunicazione tra la Germania e il programma, quindi l'ambiente in fase di esecuzione creato la Germania. In questo modo riuniti in un altro SDM in uno spazio degli indirizzi e per la Germania, ambiente di runtime e programma. È tipico di un DE implementato con un interprete per eseguire i linguaggi di script.  
  
    > [!NOTE]
    >  Come la Germania collega al programma è dipendente dall'implementazione. La comunicazione tra la Germania e il programma è dipendente dall'implementazione.  
  
## <a name="implementation"></a>Implementazione  
 A livello di codice quando gestore di sessione di debug (SDM) riceve il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma da avviare, chiama il [collegamento](../../extensibility/debugger/reference/idebugprogram2-attach.md) metodo, passando un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto, che è successiva utilizzato per passare di nuovo gli eventi di debug di SDM. Il `IDebugProgram2::Attach` chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo. Per ulteriori informazioni sul modo in cui riceve il SDM il `IDebugProgram2` interfaccia, vedere [la porta di notifica](../../extensibility/debugger/notifying-the-port.md).  
  
 Se la Germania deve essere eseguito nello stesso spazio di indirizzi del programma sottoposto a debug, in genere perché la Germania fa parte di un interprete eseguendo uno script, il `IDebugProgramNodeAttach2::OnAttach` restituisce `S_FALSE`, che indica che completato il processo di collegamento.  
  
 Se, invece, la Germania viene eseguito nello spazio degli indirizzi di SDM, il `IDebugProgramNodeAttach2::OnAttach` restituisce `S_OK` o [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia non è implementata tutti scegliere il [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma in fase di debug. In questo caso, il [collegamento](../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato alla fine per completare l'operazione di collegamento.  
  
 Nel secondo caso, è necessario chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo il `IDebugProgram2` oggetto passato al `IDebugEngine2::Attach` (metodo), archivio di `GUID` nel programma locale dell'oggetto e restituiscono questo `GUID` quando il `IDebugProgram2::GetProgramId` metodo successivamente viene chiamato su questo oggetto. Il `GUID` viene utilizzato per identificare in modo univoco il programma per i vari componenti di debug.  
  
 Si noti che nel caso del `IDebugProgramNodeAttach2::OnAttach` metodo che restituisce `S_FALSE`, `GUID` da utilizzare per il programma viene passato a tale metodo ed è il `IDebugProgramNodeAttach2::OnAttach` metodo che imposta il `GUID` sull'oggetto di programmi locali.  
  
 La Germania è ora associato al programma e pronta per l'invio di tutti gli eventi di avvio.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [La porta di notifica](../../extensibility/debugger/notifying-the-port.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Collegare](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)