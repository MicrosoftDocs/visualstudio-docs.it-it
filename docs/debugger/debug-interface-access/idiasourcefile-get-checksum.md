---
title: 'Idiasourcefile:: Get_checksum | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 002ad16d94467c135e08ef0040fd7ffd51462719
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Recupera i byte di checksum.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Dimensione del buffer di dati, in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte di checksum. Questo parametro non può essere `NULL`.  
  
 `data`  
 [in, out] Un buffer che viene riempito con i byte di checksum. Se questo parametro è `NULL`, quindi `pcbData` restituisce il numero di byte necessari.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per determinare il tipo di algoritmo di checksum utilizzata per generare i byte di checksum, chiamare il [idiasourcefile:: Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) metodo.  
  
 Il valore di checksum viene in genere generato dall'immagine del file di origine in modo che le modifiche nel file di origine vengono applicate le modifiche apportate in byte di checksum. Se i byte di checksum non corrispondono a un checksum generato dall'immagine di caricamento del file, quindi è necessario considerare il file danneggiato o manomesso.  
  
 Tipico checksum non sono mai più di 32 byte di dimensioni ma non presupporre che è la dimensione massima di un checksum. Impostare il `data` parametro `NULL` per ottenere il numero di byte necessari per recuperare il valore di checksum. Quindi allocare un buffer di dimensioni appropriate e chiamare questo metodo ancora una volta con il nuovo buffer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)