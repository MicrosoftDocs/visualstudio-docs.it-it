---
title: IDiaPropertyStorage::ReadMultiple | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1747d55de37777a9919f4709a62fbaff4b6d8a2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Letture specificate proprietà dal set di proprietà corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpspec`  
 [in] Numero di proprietà specificate nel `rgpspec` matrice. Se è zero, il metodo non restituisce nessuna proprietà ma restituire `S_OK` come un codice di riuscita.  
  
 `rgpspec`  
 [in] Una matrice di proprietà da leggere. Le proprietà possono essere specificate da un ID di proprietà o da un nome di stringa facoltativa. Non è necessario specificare le proprietà in un ordine specifico nella matrice. La matrice può contenere proprietà duplicate, valori di proprietà duplicati in fase di restituzione per le proprietà semplici. Devono restituire le proprietà non semplice accesso negato al tentativo di aprire una seconda volta. La matrice può contenere una combinazione di ID di proprietà e ID di stringa. Questa matrice deve avere almeno `cpspec` numero dei valori delle proprietà.  
  
 `rgvar`  
 [in, out] Matrice di `PROPVARIANT` strutture (nello spazio dei nomi Interop) per l'inserimento di valori per ogni proprietà. La matrice deve essere almeno `cpspec` le dimensioni degli elementi. Il chiamante non è necessario inizializzare i valori nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se uno o più delle proprietà non è stato trovato. In caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se una proprietà non viene trovato, la voce corrispondente nel `rgvar` matrice contiene un `VARIANT` con il tipo di `VT_EMPTY`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)