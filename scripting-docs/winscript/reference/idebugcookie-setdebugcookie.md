---
title: IDebugCookie::SetDebugCookie | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1155b00750cfe2a91625ba0f531622f381467198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Imposta il cookie dell'applicazione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwDebugAppCookie`  
 [in] Cookie che identifica l'applicazione di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo imposta il cookie debug dell'applicazione, che consente a più di un debugger di connettersi a un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)