---
title: 'Idiasymbol:: Get_basetype | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 080c8872682f9c255eda77449cb24dd703cd9583
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
Recupera il tipo base per questo simbolo *.*  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un valore di [BasicType (enumerazione)](../../debugger/debug-interface-access/basictype.md) enumerazione che specifica il tipo di base del simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Ottenere innanzitutto il tipo del simbolo ed quindi l'interrogazione restituite per il tipo di base, è possibile determinare il tipo di base per un simbolo. Si noti che alcuni simboli non possono avere un tipo di base, ad esempio, un nome di struttura.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 7.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [BasicType (enumerazione)](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)