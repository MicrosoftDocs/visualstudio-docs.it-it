---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Restituisce il numero di richieste di thread da thread del PDM cambio meccanismi che in fase di elaborazione. In genere, questo numero è 0 o 1. Tuttavia, il numero potrebbe essere elevato se una chiamata thread inizia l'elaborazione ma attiva una chiamata sincrona da thread, in caso contrario sospende il thread e consente le chiamate in ingresso da elaborare nuovamente (ad esempio, generando un [ Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) evento, viene generato sul thread del debugger).  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametri  
 `puiThreadRequests`  
 [out] Il numero di richieste di thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)