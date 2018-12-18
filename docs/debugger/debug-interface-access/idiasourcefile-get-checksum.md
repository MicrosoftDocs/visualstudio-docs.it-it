---
title: 'Idiasourcefile:: Get_checksum | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3cc815608c1871de7269a432e02f95acbb3e0d81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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