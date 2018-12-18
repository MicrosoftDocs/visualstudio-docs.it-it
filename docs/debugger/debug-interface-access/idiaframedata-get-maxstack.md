---
title: IDiaFrameData::get_maxStack | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 533e2db9d755ee5927d35dfad3414f83c99893bb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedatagetmaxstack"></a>IDiaFrameData::get_maxStack
Recupera il numero massimo di byte inviati allo stack nel frame.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero massimo di byte inseriti nello stack.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito da questo metodo viene utilizzato in genere l'interpretazione di una stringa di programma (vedere il [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) metodo per la definizione di una stringa di programma).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)