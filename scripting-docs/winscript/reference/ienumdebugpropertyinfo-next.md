---
title: IEnumDebugPropertyInfo::Next | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc1e25a865ab1e21ab011e3a5bd0cc3b74f4abf2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Recupera un numero specificato di `DebugPropertyInfo` strutture in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di `DebugPropertyInfo`strutture da recuperare.  
  
 `rgelt`  
 [out] Matrice di `DebugPropertyInfo` strutture recuperate.  
  
 `pceltFetched`  
 [out] Restituisce il numero di `DebugPropertyInfo` strutture effettivamente recuperate.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)