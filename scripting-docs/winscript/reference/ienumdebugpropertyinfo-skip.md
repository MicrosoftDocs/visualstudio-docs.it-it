---
title: IEnumDebugPropertyInfo::Skip | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d0f8ff65340edfac1c02e5b7e80b7be3fd257c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Ignora un numero specificato di `DebugPropertyInfo` strutture in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di `DebugPropertyInfo` strutture nella sequenza di enumerazione da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`. Restituisce `S_FALSE` e imposta la fine dell'enumerazione puntatore dell'elemento corrente se `celt` è maggiore del numero di elementi a sinistra nell'enumeratore.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)