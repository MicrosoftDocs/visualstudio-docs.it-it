---
title: Interfaccia IJsDebugDataTarget | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatarget-interface"></a>Interfaccia IJsDebugDataTarget
Implementato dal debugger per fornire funzionalità di accedere e modificare lo stato del processo del debugger di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Riserva e/o viene eseguito il commit di un'area di memoria all'interno di spazio degli indirizzi virtuali del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumeratore per gli stack frame.|  
|[Metodo IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Rilascia e/o libera un'area di memoria all'interno di spazio degli indirizzi virtuali del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Contesto recuperato per dato thread.|  
|[Metodo IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Per il thread è in corso il debug, recupera il valore nello slot (TLS) di archiviazione locale di thread per l'indice specificato di TLS.|  
|[Metodo IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Legge un BSTR da destinazione di debug.|  
|[Metodo IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Legge la memoria del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Legge il numero specificato di caratteri dalla destinazione.|  
|[Metodo IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Legge la memoria del processo di destinazione.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)