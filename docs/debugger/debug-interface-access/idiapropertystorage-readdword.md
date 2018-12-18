---
title: IDiaPropertyStorage::ReadDWORD | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7353ef9f1aca7348adf681bfe627441e409906e6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Legge `DWORD` valori in un set di proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 [in] Identificatore della proprietà da leggere (`PROPID` è definito in Wtypes. H come un `ULONG`).  
  
 `pValue`  
 [out] Restituisce il valore della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `DWORD`.  
  
## <a name="remarks"></a>Note  
 Oggetto `DWORD` è definito da Windows come un intero senza segno a 32 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)