---
title: IDiaSymbol::get_isMultipleInheritance | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab7f0d789527f874f3d3b80b44c58347d1cd84f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Specifica se il `this` puntatore punta a un membro dati con ereditarietà multipla.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isMultipleInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore a un `BOOL` che specifica se il `this` puntatore punta a un membro dati con ereditarietà multipla.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)