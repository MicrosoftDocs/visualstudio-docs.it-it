---
title: Interfaccia IDebugApplication110 | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110-interface"></a>Interfaccia IDebugApplication110
Il `IDebugApplication110` interfaccia estende la funzionalità del [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md). È possibile ottenere un'istanza di questa interfaccia tramite la chiamata QueryInterface su un'implementazione di [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplication110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Effettua una chiamata sincrona nel thread principale.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Effettua una chiamata asincrona nel thread principale.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Attende che uno degli handle specificati per ricevere il segnale consentendo chiamata tra thread a questo thread. Questo metodo deve essere chiamato dal thread del debugger.|