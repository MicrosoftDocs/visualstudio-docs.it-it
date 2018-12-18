---
title: Porta fornitore interfacce necessarie | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab243886341d720045fc2d1fbd7a813b7d81c9e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="required-port-supplier-interfaces"></a>Porta richiesta fornitore interfacce
Un fornitore di porta deve implementare il [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Poiché un fornitore di porta fornisce porte, è necessario implementare tali. Pertanto, deve implementare le interfacce seguenti:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Descrive la porta e può enumerare tutti i processi in esecuzione sulla porta.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fornisce per l'avvio e terminazione dei processi sulla porta.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornisce un meccanismo per i programmi in esecuzione nel contesto di questa porta per inviare una notifica di eliminazione e creazione di nodi di programma. Per ulteriori informazioni, vedere [programma nodi](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Fornisce un punto di connessione per [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operazione di porta fornitore  
 Il [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) sink riceve le notifiche quando il processo e i programmi vengono creati e distrutti su una porta. Per inviare è necessaria una porta [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminato definitivamente sulla porta. Una porta è inoltre necessario per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato definitivamente in un processo in esecuzione sulla porta.  
  
 Una porta in genere programma invia creazione ed eliminazione in risposta a eventi di [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metodi, rispettivamente.  
  
 Poiché una porta può avviare e terminare processi fisici sia logici programmi, queste interfacce devono essere implementate dal motore di debug:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Descrive il processo fisico. Almeno devono essere implementati i metodi seguenti:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fornisce un modo per il SDM collegare e scollegare stesso da un processo.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Viene descritto il programma logico. Almeno devono essere implementati i metodi seguenti:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Fornisce un modo per SDM associare a questo programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)