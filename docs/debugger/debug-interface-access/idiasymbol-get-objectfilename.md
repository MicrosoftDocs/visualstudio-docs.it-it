---
title: IDiaSymbol::get_objectFileName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 683e789e1edbe9f256847ad1e7d5fb7d13616608
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetobjectfilename"></a>IDiaSymbol::get_objectFileName
Recupera il nome del file oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_objectFilename(   
   BSTR *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore a un `BSTR` che contiene il nome del file oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)