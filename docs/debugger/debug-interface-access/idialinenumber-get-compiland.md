---
title: IDiaLineNumber::get_compiland | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee004d5cd97157963973f6dd650bd0ce1aa37b52
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
Recupera un riferimento al simbolo per il modulo che hanno contribuito i byte di testo di immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto per il modulo che hanno contribuito i byte di testo di immagine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)