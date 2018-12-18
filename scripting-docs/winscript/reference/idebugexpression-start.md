---
title: IDebugExpression::Start | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Avvia la valutazione dell'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdecb`  
 [in] Callback per indicare quando la valutazione dell'espressione è stata completata. Se questo parametro è `NULL`, viene generato alcun evento e il client deve eseguire il polling dello stato di espressione utilizzando `QueryIsComplete`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo avvia la valutazione dell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)