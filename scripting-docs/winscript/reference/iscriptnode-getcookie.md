---
title: IScriptNode::GetCookie | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetCookie
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa68f528aeb405ca150cff717ab5e4bebb82027a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Restituisce un valore definito dall'applicazione che viene utilizzato per associare un scriptlet con l'oggetto host.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwCookie`  
 [out] Per un `IScriptEntry` dell'oggetto, restituisce il valore del cookie definito dall'applicazione.  
  
 Per un `IScriptNode` oggetto che rappresenta una pagina Web, restituisce 0.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)