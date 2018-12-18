---
title: Interfaccia IJsDebugFrame | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframe-interface"></a>Interfaccia IJsDebugFrame
Rappresenta uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Valutare un'espressione nel contesto dello stack frame corrente.|  
|[Metodo IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Restituisce un visualizzatore di proprietà per lo stack frame.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Restituisce la posizione corrente dello stack frame corrente all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Restituisce la posizione corrente dello stack frame corrente all'interno del documento a livello di utente.|  
|[Metodo IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Ottiene il nome descrittivo dello stack frame.|  
|[Metodo IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ottiene l'indirizzo del mittente inserito all'inizio' ' (vedere GetStackRange) del frame.|  
|[Metodo IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)