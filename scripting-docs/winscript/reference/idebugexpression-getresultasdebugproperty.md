---
title: IDebugExpression::GetResultAsDebugProperty | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ce67df5dd55bd8c1ae55bb19fe2a19aed9e40f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Restituisce il risultato della valutazione dell'espressione come una proprietà di debug e il valore restituito dell'operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phrResult`  
 [out] Valore restituito dell'operazione.  
  
 `ppdp`  
 [out] La proprietà di debug per l'espressione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_PENDING`|L'operazione è ancora in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il risultato della valutazione dell'espressione come un `IDebugProperty` e l'operazione `HRESULT`.  
  
 Questo metodo restituisce `S_OK` e `phrResult` restituisce `E_ABORT` se `Abort` interrompe l'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)