---
title: IScriptNode::GetChild | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Restituisce l'elemento figlio in corrispondenza dell'indice specificato nel nodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `isn`  
 [in] Indice dell'elemento figlio dell'elemento padre.  
  
 `ppsn`  
 [out] L'indirizzo di una variabile che riceve un puntatore di `IScriptNode` interfaccia dell'istanza figlio.  
  
 Per `IScriptNode` gli oggetti che rappresentano una pagina Web, questo parametro restituisce un oggetto che contiene un blocco di script.  
  
 Per `IScriptEntry` oggetti che specificano un blocco di script, questo parametro restituisce un oggetto che specifica una funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione e per `IScriptScriptlet` oggetti, questo metodo non riesce perché non sono presenti voci figlio.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)