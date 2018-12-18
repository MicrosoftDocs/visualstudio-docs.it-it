---
title: IDiaStackWalkFrame::readMemory | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d23b46f0f487bddc678814e41b5cb96331ff46c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Legge dall'immagine della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 [in] Uno del [MemoryTypeEnum (enumerazione)](../../debugger/debug-interface-access/memorytypeenum.md) valori di enumerazione che specifica il tipo di memoria per l'accesso.  
  
 `va`  
 [in] Percorso di indirizzo virtuale nell'immagine per iniziare la lettura.  
  
 `cbData`  
 [in] Dimensione del buffer di dati, in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte restituiti. Se `data` è `NULL`, quindi `pcbData` contiene il numero totale di byte di dati disponibili.  
  
 `data`  
 [out] Un buffer che deve essere compilato con i dati dal percorso specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)