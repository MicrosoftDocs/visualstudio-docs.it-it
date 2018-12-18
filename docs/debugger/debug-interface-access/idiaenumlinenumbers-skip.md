---
title: IDiaEnumLineNumbers::Skip | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebaa7366128a02b9ac0af253c418650a747b657e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
Ignora un numero specificato di numeri di riga in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di numeri di riga nella sequenza di enumerazione da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se sono non presenti ignorare più numeri di riga.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)