---
title: IScriptNode::GetNumberOfChildren | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetNumberOfChildren
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetNumberOfChildren
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdb46527ca78d56b3c03a454c6194e80be19e945
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetnumberofchildren"></a>IScriptNode::GetNumberOfChildren
Restituisce il numero dei nodi figlio di `IScriptNode` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcsn`  
 [out] Il numero di nodi figlio che la `IScriptNode` oggetto ha.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)