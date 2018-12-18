---
title: IDebugProcessSecurity | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e78baf34a3ecb6d5b40162b424c11a104617669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` viene implementato da un fornitore di porta per avvisare l'utente che connessione al processo non sicura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessSecurity`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ottiene il nome utente dal fornitore porta.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Un utente viene avvisato che la connessione al processo di debug è unsafe.|  
  
## <a name="remarks"></a>Note  
 Implementare questa interfaccia per visualizzare un avviso e consentire all'utente di annullare il processo a cui si sta associando può essere considerato non sicuro.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Porte](../../../extensibility/debugger/ports.md)   
 [Fornitori di porte](../../../extensibility/debugger/port-suppliers.md)   
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)