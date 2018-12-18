---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d53b498ba88fae50cfaca106a65a2bb07d21a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Restituisce la funzionalità di SID per l'errore di Runtime di Windows, se disponibile.  
  
> [!IMPORTANT]
>  [Interfaccia IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parametri  
 `capabilitySid`  
 La funzionalità di SID dell'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)