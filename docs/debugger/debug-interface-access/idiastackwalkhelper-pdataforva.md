---
title: IDiaStackWalkHelper::pdataForVA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9eb500539184d6ac5e7e3cb00e753a00f3585057
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Restituisce il blocco di dati PDATA associato all'indirizzo virtuale.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `va`  
 [in] Specifica l'indirizzo virtuale dei dati da ottenere.  
  
 `cbData`  
 [in] Le dimensioni dei dati in byte da ottenere.  
  
 `pcbData`  
 [out] Restituisce le dimensioni effettive dei dati in byte che è stato ottenuto.  
  
 `pbData`  
 [in, out] Un buffer che viene riempito con i dati richiesti. Non può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è presente alcun PDATA per l'indirizzo specificato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 PDATA (sezione denominata "pdata") di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.  
  
 Il chiamante conosce la quantità di dati è necessario restituire quindi il chiamante non ha alcuna necessità di richiederle per la quantità di dati è disponibile. Pertanto, è accettabile per l'implementazione di questo metodo per restituire un errore se il `pbData` parametro `NULL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)