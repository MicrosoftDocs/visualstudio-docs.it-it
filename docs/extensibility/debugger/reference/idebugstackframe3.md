---
title: IDebugStackFrame3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3
helpviewer_keywords: IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a45859fe78df3907df680b7716f743ff411ca3f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Questa interfaccia estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per gestire le eccezioni intercettate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per supportare le eccezioni intercettate.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugStackFrame2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per lo stack frame corrente prima di eventuali eccezioni regolare.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto di codice se si verificasse uno svuotamento dello stack.|  
  
## <a name="remarks"></a>Note  
 Un'eccezione intercettata significa che un debugger può elaborare un'eccezione prima di qualsiasi routine di gestione delle eccezioni normale vengono chiamati dal runtime. Intercettazione di un'eccezione in pratica significa la fase di esecuzione si supponga che sia presente anche quando non vi è un gestore di eccezioni.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti gli eventi di callback di eccezione normale (l'unica eccezione è se si esegue il debug in modalità mista di codice gestito e codice non gestito, nel qual caso non è possibile intercettare l'eccezione durante il ultima possibilità callback). Se non implementa la Germania `IDebugStackFrame3`, o la Germania restituisce un errore da IDebugStackFrame3::`InterceptCurrentException` (ad esempio `E_NOTIMPL`), quindi il debugger gestirà in genere l'eccezione.  
  
 Mediante l'intercettazione di un'eccezione, il debugger può consentire all'utente di apportare modifiche allo stato del programma sottoposto a debug e quindi riprendere l'esecuzione nel punto in cui è stata generata l'eccezione.  
  
> [!NOTE]
>  Eccezioni intercettate sono consentite solo nel codice gestito, vale a dire, in un programma che è in esecuzione in Common Language Runtime (CLR).  
  
 Un motore di debug indica che supporta le eccezioni di intercettazione impostando "metricExceptions" su un valore pari a 1 in fase di esecuzione utilizzando il `SetMetric` (funzione). Per ulteriori informazioni, vedere [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)