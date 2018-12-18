---
title: IEnumDebugCodeContexts::Clone | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Clone
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ae10efb0f3429d0355b270be69d073876ca1b74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontextsclone"></a>IEnumDebugCodeContexts::Clone
Crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppescc`  
 [out] Restituisce il `IEnumDebugCodeContexts` interfaccia del clone dell'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)