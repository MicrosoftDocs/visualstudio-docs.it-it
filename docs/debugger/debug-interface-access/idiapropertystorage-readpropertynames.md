---
title: IDiaPropertyStorage::ReadPropertyNames | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13ac0e3a1af8dc20fe63f832e7a19d7bf40c271
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera corrispondente per i nomi di stringa fornito gli identificatori di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpropid`  
 [in] Numero di ID di proprietà in `rgpropid`.  
  
 `rgpropid`  
 [in] Matrice di ID di proprietà per cui ottenere i nomi (`PROPID` è definito in Wtypes. H come un `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Matrice di nomi di proprietà per l'ID di proprietà specificato. La matrice deve essere pre-allocata per contenere il numero richiesto di nomi di proprietà e deve essere in grado di contenere almeno `cpropid``BSTR` stringhe.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I nomi di proprietà restituito devono essere liberati (chiamando il `SysFreeString` funzione) quando non sono più necessari.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)