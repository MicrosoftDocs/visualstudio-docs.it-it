---
title: 'Metodo ijsdebugframe:: GetStackRange | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetstackrange-method"></a>Metodo IJsDebugFrame::GetStackRange
Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStart`  
 [out] Basso la maggior parte dei puntatori agli stack del frame.  
  
 `pEnd`  
 [out] Primi puntatore Fascicolatore la maggior parte del frame.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Questo metodo è utile per riunire le tracce dello stack con interfoliazione raccolte da più runtime. Inizio, fine puntatori di stack possono includere più stack frame di computer fisico (per i frame al runtime JavaScript interpretati). Start > terminare man mano che aumenta lo stack dall'alto all'indirizzo bassa.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)