---
title: IDebugApplicationNodeEvents::onDetach | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onDetach
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b5f1ccc35e83f4fa016b5ff3dae8fac867bb8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato scollegato da un nodo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce un evento indicante che l'oggetto nodo dell'applicazione di debug è stato scollegato da un nodo padre.  
  
 I responsabili dell'implementazione di `IDebugApplicationNode` interfaccia generare questo evento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)