---
title: IScriptNode::Alive | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0631690cbd961273175cf8dfbe35550980d4994d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indica se un oggetto è ancora attivo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il nodo di script è ancora attivo.|  
  
## <a name="remarks"></a>Note  
 Se l'oggetto non è attivo, il modello COM (Component Object) restituisce un errore dal proxy di marshalling per le chiamate a questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)