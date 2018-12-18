---
title: IDiaPropertyStorage::Enum | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0fe51224a4b4a5abc73a3edb7a2caf239d32efb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Ottiene un enumeratore per le proprietà all'interno di questo set.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppenum`  
 [out] Restituisce un `IEnumSTATPROPSTG` oggetto (nello spazio dei nomi Interop) che rappresenta un'enumerazione di proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)