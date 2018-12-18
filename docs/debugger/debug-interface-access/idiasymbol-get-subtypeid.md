---
title: IDiaSymbol::get_subTypeId | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0f899920-4fc5-4de8-84a3-cd98c57bf124
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8fc4036ac0c5f148ca067a00b635ae7023232ed
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetsubtypeid"></a>IDiaSymbol::get_subTypeId
Recupera l'ID di tipo sub.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_subTypeId(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore a un `DWORD` che contiene l'ID di tipo sub.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)