---
title: IDiaSymbol::get_unmodifiedTypeId | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03013ad84ff6a74d967c7b4dc5784565df909730
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetunmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
Recupera l'ID del tipo originale (non modificato).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_unmodifiedTypeId(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore a un `DWORD` che contiene l'ID.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)