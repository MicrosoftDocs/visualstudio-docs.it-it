---
title: IDebugExpression::GetResultAsString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Restituisce il risultato della valutazione dell'espressione come una stringa e valore restituito dell'operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phrResult`  
 [out] Valore restituito dell'operazione.  
  
 `pbstrResult`  
 [out] Il risultato della valutazione dell'espressione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_PENDING`|L'operazione è ancora in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il risultato della valutazione dell'espressione come una stringa e l'operazione `HRESULT`.  
  
 Questo metodo restituisce `S_OK` e `phrResult` restituisce `E_ABORT` se `Abort` interrompe l'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)