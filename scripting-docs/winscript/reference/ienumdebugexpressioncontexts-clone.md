---
title: IEnumDebugExpressionContexts::Clone | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExpressionContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugExpressionContexts::Clone
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f548bf0872d042a131c743554d6f45ccca0ebe98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugexpressioncontextsclone"></a>IEnumDebugExpressionContexts::Clone
Crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppedec`  
 [out] Restituisce il `IEnumDebugExpressionContexts` interfaccia del clone dell'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)