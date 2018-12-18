---
title: IDiaSession::symsAreEquiv | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc92a38305e7cc8c74b4ada0d560b314ed92da8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Controlla se due simboli sono equivalenti.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `symbolA`  
 [in] Il primo [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto utilizzato nel confronto.  
  
 `symbolB`  
 [in] Il secondo `IDiaSymbol` oggetto utilizzato nel confronto.  
  
## <a name="return-value"></a>Valore restituito  
 Se i simboli sono equivalenti, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, i simboli non sono equivalenti. In caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)