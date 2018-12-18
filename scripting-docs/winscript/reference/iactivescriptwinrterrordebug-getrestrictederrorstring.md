---
title: IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ade51ae9852519d6a059193aacbfdde49ae82d19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Restituisce il Runtime di Windows limitato stringa di errore, se disponibile.  
  
> [!IMPORTANT]
>  [Interfaccia IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Parametri  
 `errorString`  
 [out] La stringa di errore con restrizioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)