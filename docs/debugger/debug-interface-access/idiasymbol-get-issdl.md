---
title: IDiaSymbol::get_isSdl | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0a38c77383a7793b3116187703b256b54164528
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
Specifica se il modulo compilato con l'opzione /SDL.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore a un `BOOL` che specifica se il modulo compilato con l'opzione /SDL.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)