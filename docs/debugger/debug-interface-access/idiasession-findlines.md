---
title: 'Idiasession:: Findlines | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb256778f2bf92827ff98c5cafbb77bfdcba6c12
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Recupera i numeri di riga nel modulo specificato e gli identificatori di file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `compiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il modulo. Utilizzare questa interfaccia come un contesto in cui cercare i numeri di riga.  
  
 `file`  
 [in] Un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) oggetto che rappresenta il file di origine in cui cercare i numeri di riga.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) recuperare l'oggetto che contiene un elenco di numeri di riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)