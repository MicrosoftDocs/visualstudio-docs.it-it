---
title: IDebugExpression::QueryIsComplete | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d72b2a2d41b748954f2e4b2b4aa9f0011ca670
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Determina se l'operazione è stata completata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito e l'operazione è stata completata.|  
|`S_FALSE`|L'operazione è ancora in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se l'operazione è stata completata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)