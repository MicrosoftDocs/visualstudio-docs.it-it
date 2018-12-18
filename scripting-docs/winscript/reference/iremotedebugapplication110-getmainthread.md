---
title: IRemoteDebugApplication110::GetMainThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc420f3c59a59373c6e3a2be9e7254eea451585
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Restituisce il thread principale per gli host che chiamano [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), in caso contrario restituisce E_FAIL.  
  
> [!IMPORTANT]
>  [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppThread`  
 [out] Il principale [interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interfaccia IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)