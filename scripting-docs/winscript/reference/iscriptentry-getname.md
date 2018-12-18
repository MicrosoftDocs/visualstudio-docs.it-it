---
title: IScriptEntry::GetName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc518e87414d051e9b1393b60b5874a0204b78b2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Per le voci che rappresentano un singolo oggetto (ad esempio una funzione), restituisce il nome dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] Il nome dell'oggetto rappresentato dal `IScriptEntry` blocco di script. Se una voce non rappresenta un singolo oggetto, viene restituito NULL.  
  
 Le voci figlio rappresentano un oggetto funzione singola.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)