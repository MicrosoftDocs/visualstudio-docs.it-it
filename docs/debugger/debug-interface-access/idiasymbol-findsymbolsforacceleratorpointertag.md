---
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b96de709ae3ff8e4f8e37e882ca634fb158518a5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
Restituisce il numero di tag puntatore tasti di scelta rapida in una funzione di C++ AMP stub.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findSymbolsForAccleratorPointerTag (   
   DWORD             tagValue,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parametri  
 `tagValue`  
 [in] Il valore del tag puntatore per cui sono contenuti i record dei simboli pointee.  
  
 `ppResult`  
 [out] Un puntatore a un `IDiaEnumSymbols` puntatore a interfaccia che viene inizializzato con il risultato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)