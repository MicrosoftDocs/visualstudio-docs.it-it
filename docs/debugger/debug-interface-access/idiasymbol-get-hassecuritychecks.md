---
title: IDiaSymbol::get_hasSecurityChecks | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b14858508d341d09616d8b4a6c44afe1a5f21594
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Recupera un flag che specifica se la funzione o un modulo è stato compilato con i controlli di sicurezza di sovraccarico del buffer (ad esempio, il [/GS (controllo sicurezza Buffer)](/cpp/build/reference/gs-buffer-security-check) opzione del compilatore).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Restituisce `TRUE` se la funzione dispone di alcun controllo della sicurezza; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 8.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check)