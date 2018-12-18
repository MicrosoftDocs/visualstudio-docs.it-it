---
title: IDiaInjectedSource::get_sourceCompression | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a56d1eac34c5076be8dbcd7b4e38363a12fe392f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera l'indicatore di compressione di origine utilizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce l'indicatore di compressione di origine utilizzato. Un valore pari a zero indica che è stata usata alcuna compressione di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito da questo metodo è specifico per usata dal compilatore. Ad esempio, un compilatore può utilizzare la compressione di codifica di Run-Length o lo stile di Huffman.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)