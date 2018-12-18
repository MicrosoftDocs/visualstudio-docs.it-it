---
title: Interfaccia IDebugApplicationNodeEvents | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfaccia IDebugApplicationNodeEvents
Fornisce l'interfaccia di eventi per il `IDebugApplicationNode` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugApplicationNodeEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gestisce l'evento quando un nodo figlio viene aggiunto a un oggetto nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gestisce l'evento quando un nodo figlio viene rimosso da un oggetto nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato scollegato da un nodo padre.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato collegato a un nodo padre.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)