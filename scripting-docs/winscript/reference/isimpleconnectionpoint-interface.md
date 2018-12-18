---
title: Interfaccia ISimpleConnectionPoint | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpoint-interface"></a>Interfaccia ISimpleConnectionPoint
Fornisce un modo semplice per la descrizione e l'enumerazione agli eventi generati in un punto di connessione specifica. Questa interfaccia consente inoltre di associare un `IDispatch` oggetto tali eventi. Questa interfaccia viene implementata dal processo di Debug Manager (PDM) e utilizzata dai motori di script.  
  
 Questa interfaccia è disponibile da `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oltre ai metodi ereditati da `IUnknown`, `ISimpleConnectionPoint` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Stabilisce una connessione tra l'oggetto punto di connessione semplice e il sink del client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Restituisce il nome per ogni evento e i DISPID in un intervallo specificato di eventi.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Restituisce il numero di eventi esposti su questa interfaccia.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)