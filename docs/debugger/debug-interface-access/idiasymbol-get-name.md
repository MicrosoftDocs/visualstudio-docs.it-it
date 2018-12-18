---
title: IDiaSymbol::get_name | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_name method
ms.assetid: 050ec02f-b7b3-48fc-8e35-58bdf7d938b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9ed63dce04967d9a312c57b5507da828814c6f6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetname"></a>IDiaSymbol::get_name
Recupera il nome del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il nome del simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaSymbol* pType;  
BSTR        name;  
pType->get_name( &name );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)