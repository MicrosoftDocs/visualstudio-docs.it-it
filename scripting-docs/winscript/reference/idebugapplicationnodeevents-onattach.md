---
title: IDebugApplicationNodeEvents::onAttach | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onAttach
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a45fff15ce4f7faf6cf8714cbf01289e69f67691
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato collegato a un nodo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prddpParent`  
 [in] Il nodo dell'applicazione di debug che rappresenta l'elemento padre del nodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato collegato a un nodo padre.  
  
 I responsabili dell'implementazione di `IDebugApplicationNode` interfaccia generare questo evento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)