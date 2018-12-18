---
title: IDiaLineNumber::get_addressOffset | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_addressOffset method
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1e8911e1c1a1cce764775850520593efe4be9f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumbergetaddressoffset"></a>IDiaLineNumber::get_addressOffset
Recupera la parte relativa all'offset dell'indirizzo di memoria in cui inizia un blocco.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la parte offset di indirizzo di memoria in cui inizia un blocco.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="example"></a>Esempio  
  
```C++  
CComPtr< IDiaLineNumber > pLine;  
DWORD offset;  
pLine->get_addressOffset( &offset);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)