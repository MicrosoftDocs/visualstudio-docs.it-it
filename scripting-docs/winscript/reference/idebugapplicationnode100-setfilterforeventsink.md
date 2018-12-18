---
title: IDebugApplicationNode100::SetFilterForEventSink | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6db8ea26787427844a92417bf525dba271063cba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Imposta il filtro in un particolare [interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementazione. In questo modo il debugger di script filtrare i nodi figlio generato dal compilatore di applicazioni in modo da PDM non invierà più gli eventi quando questi vengono creati o rimosse. Per impostazione predefinita, verranno inviati tutti i nodi.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) è implementata da PDM v di 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 Il cookie del filtro.  
  
 `filter`  
 Filtro.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)