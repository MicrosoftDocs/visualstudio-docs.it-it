---
title: IDiaStackWalkHelper::readMemory | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f528d377dc75f940a10f1a38ae04cc3eb71cdd22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Legge un blocco di dati dall'immagine del file eseguibile in memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 [in] Un valore di [MemoryTypeEnum (enumerazione)](../../debugger/debug-interface-access/memorytypeenum.md) enumerazione che specifica il tipo di memoria per la lettura.  
  
 va  
 [in] Indirizzo virtuale dell'immagine da cui iniziare la lettura.  
  
 `cbData`  
 [in] Le dimensioni del buffer di dati in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte effettivamente letti. Se `pbData` è `NULL`, quindi il numero totale di byte di dati disponibili.  
  
 `pbData`  
 [in, out] Un buffer che viene compilato con la memoria di lettura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum (enumerazione)](../../debugger/debug-interface-access/memorytypeenum.md)