---
title: IDiaSectionContrib::get_informational | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b8d991a5444c719696db62ab6f9c3374015ea7e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
Recupera un flag che indica se una sezione con commenti o informazioni simili.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se la sezione contiene commenti o altre informazioni; in caso contrario restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 La sezione .directive contiene in genere informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)