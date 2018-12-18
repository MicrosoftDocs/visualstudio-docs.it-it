---
title: IDebugModule2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2
helpviewer_keywords: IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
Questa interfaccia rappresenta un modulo, vale a dire un'unità eseguibile di un programma, ad esempio una DLL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un modulo e per fornire accesso alle informazioni su tale modulo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) restituisce questa interfaccia. Invia il DE la [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfaccia per la gestione di debug della sessione (SDM) utilizzando il [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo).  
  
 Questa interfaccia può essere restituita anche un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura (quale deve essere restituito da una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce anche questa interfaccia ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce il [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugModule2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che descrive questo modulo.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.|  
  
## <a name="remarks"></a>Note  
 È possibile visualizzare informazioni sul modulo di **moduli** finestra dell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)