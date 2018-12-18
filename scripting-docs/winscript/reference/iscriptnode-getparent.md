---
title: IScriptNode::GetParent | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da2f68de40a66b98b97ab7c7eb1d63748f1e07a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Restituisce il `IScriptNode` oggetto che rappresenta l'elemento padre di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppsnParent`  
 [out] L'indirizzo di una variabile che riceve un puntatore di `IScriptNode` interfaccia dell'istanza padre.  
  
 Se la classe implementa `IScriptEntry` o `IScriptScriptlet`, un `IScriptNode` viene restituito l'oggetto.  
  
 Se la classe implementa `IScriptNode` (che rappresenta una pagina Web), viene restituito NULL.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)