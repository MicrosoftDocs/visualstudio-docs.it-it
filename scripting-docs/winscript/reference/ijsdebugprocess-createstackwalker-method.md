---
title: 'Metodo ijsdebugprocess:: Createstackwalker | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ca7594f4e3c6ef44aa8cde1d92f17d46a9aa30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>Metodo IJsDebugProcess::CreateStackWalker
Metodo factory per walker dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 [in] ID del thread.  
  
 `ppStackWalker`  
 [out] Nuovo oggetto walker dello stack.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_UNKNOWN_THREAD se il thread non dispone di JavaScript su di esso. Questo metodo può essere chiamato solo durante il processo di destinazione viene arrestato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)