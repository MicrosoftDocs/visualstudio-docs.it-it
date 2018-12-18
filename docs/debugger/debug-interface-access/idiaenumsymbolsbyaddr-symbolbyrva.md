---
title: IDiaEnumSymbolsByAddr::symbolByRVA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4cdeaef2bc963eca894403bf90e1c9fb720efd4d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Posiziona l'enumeratore eseguendo una ricerca in base all'indirizzo virtuale relativo (RVA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT symbolByRVA (   
   DWORD**      relativeVirtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 relativeVirtualAddress  
 [in] Indirizzo relativa all'inizio dell'immagine.  
  
 ppsymbol  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il simbolo trovato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non è stato possibile trovare il simbolo. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [Symbolbyva](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)