---
title: IDiaSymbol::findChildrenExByVA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbc050bf1923e13678e4938f04b40f8db30c12f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Recupera gli elementi figlio del simbolo valide in un indirizzo virtuale specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `symtag`  
 [in] Specifica il tag symbol degli elementi figlio da recuperare, come definito nel [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md). Impostare su `SymTagNull` per tutti gli elementi figlio da recuperare.  
  
 `name`  
 [in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.  
  
 `compareFlags`  
 [in] Specifica le opzioni di confronto da applicare al nome corrispondente. I valori di [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzato da solo o in combinazione.  
  
 `address`  
 [in] Specifica l'indirizzo virtuale.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperare l'oggetto che contiene un elenco dei simboli figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se almeno un figlio del simbolo è stato trovato oppure restituisce `S_FALSE` se sono stato trovato senza elementi figlio; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I simboli locali che vengono restituiti includono le informazioni di intervallo in tempo reale.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions (enumerazione)](../../debugger/debug-interface-access/namesearchoptions.md)