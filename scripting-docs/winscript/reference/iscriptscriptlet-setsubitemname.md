---
title: IScriptScriptlet::SetSubItemName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0d038330d502dd9a230fdb82c14d36732fed7e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Imposta l'ultimo identificatore nel nome completo dell'host di scriptlet oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 Se l'host completo del nome di scriptlet ha più di un livello, `psz` è l'indirizzo del buffer dell'identificatore nel secondo livello.  
  
 Se l'host completo del nome di scriptlet dispone di un livello, `psz` è l'indirizzo del buffer dell'identificatore al primo livello.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)