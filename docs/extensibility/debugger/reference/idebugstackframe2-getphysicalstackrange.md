---
title: IDebugStackFrame2::GetPhysicalStackRange | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be53b50bc21d81c60f7131e8ed437ecb2ac2f16c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ottiene una rappresentazione dipendenti dal computer dell'intervallo di indirizzi fisici associati a uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `paddrMin`  
 [out] Restituisce l'indirizzo fisico più basso associata a questo stack frame.  
  
 `paddrMax`  
 [out] Restituisce l'indirizzo fisico più alto associata a questo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le informazioni restituite da questo metodo viene utilizzate dal gestore di sessione di debug (SDM) per ordinare gli stack frame.  
  
 Si presuppone che lo stack di chiamate si espande verso il basso, ovvero, vengono aggiunti al nuovo stack frame inferiore sempre più indirizzi di memoria. Un'architettura della fase di esecuzione è necessario fornire intervalli stack fisico che corrispondono a questo presupposto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)