---
title: IDebugApplicationNodeEvents::onAddChild | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df872cd14b6d7fcd455371d1601b2a4082fb39a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Gestisce l'evento quando un nodo figlio viene aggiunto a un oggetto nodo dell'applicazione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prddpChild`  
 [in] Il nodo dell'applicazione debug figlio che è stato aggiunto.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce l'evento quando un nodo figlio viene aggiunto a un oggetto nodo dell'applicazione di debug.  
  
 I responsabili dell'implementazione di `IDebugApplicationNode` interfaccia generare questo evento  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)