---
title: IDebugApplicationNode::Attach | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 393186330979d464fe54bde339806a5d8335a859
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Aggiunge il nodo dell'applicazione per la struttura del progetto specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdanParent`  
 [in] La struttura del progetto in cui è necessario aggiungere il nodo dell'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiunge questo nodo dell'applicazione per il progetto ad albero, utilizzando `pdanParent` come elemento padre. Se `pdanParent` è `NULL`, il nodo dell'applicazione sarà il nodo di primo livello.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)