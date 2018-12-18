---
title: IDebugApplication110::AsynchronousCallInMainThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 236a6585d5d5844f282d8ecf5820ac8fdfb49648
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Effettua una chiamata asincrona nel thread principale.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pptc`  
 Il [interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) oggetto da chiamare.  
  
 `dwParam1`  
 Il primo parametro della chiamata.  
  
 `dwParam1`  
 Il primo parametro della chiamata.  
  
 `dwParam2`  
 Il secondo parametro della chiamata.  
  
 `dwParam3`  
 Il terzo parametro della chiamata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)