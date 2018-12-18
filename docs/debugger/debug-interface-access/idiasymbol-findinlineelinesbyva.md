---
title: IDiaSymbol::findInlineeLinesByVA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fd0167eaea86b13c8d197d39c6042f5ad183fcd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, in questo simbolo all'interno dell'indirizzo virtuale specificato (VA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findInlineeLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `va`  
 [in] Specifica l'indirizzo come un Virginia.  
  
 `length`  
 [in] Specifica l'intervallo di indirizzi, in numero di byte, per coprire la query.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumLineNumbers` oggetto che contiene l'elenco di numeri di riga recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)