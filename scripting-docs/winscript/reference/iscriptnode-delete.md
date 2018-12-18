---
title: IScriptNode::Delete | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d1404d90cc1edd882505e463938a2c1a5e8aea8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Elimina questo albero di oggetti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Dopo il `Delete` metodo viene chiamato, il [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) metodo dovrebbe indicare tale nodo di script non è attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)