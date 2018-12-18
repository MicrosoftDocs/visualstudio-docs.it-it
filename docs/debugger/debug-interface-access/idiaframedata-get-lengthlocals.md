---
title: IDiaFrameData::get_lengthLocals | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31dd2eb35ccf8a9adb4392c55bbfb3feb8b010e5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedatagetlengthlocals"></a>IDiaFrameData::get_lengthLocals
Recupera il numero di byte di variabili locali inserite nello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di byte di variabili locali.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito da questo metodo viene utilizzato in genere l'interpretazione di una stringa di programma (vedere il [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) metodo per la definizione di una stringa di programma).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)