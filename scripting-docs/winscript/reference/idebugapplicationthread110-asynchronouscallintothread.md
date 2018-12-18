---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4275d42ec102557cce12127f47a33a53c4dba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Effettua una chiamata asincrona nel thread principale.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
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