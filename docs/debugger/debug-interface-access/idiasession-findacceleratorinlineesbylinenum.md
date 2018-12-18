---
title: IDiaSession::findAcceleratorInlineesByLinenum | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 625c4368b1a05ae805a3df8cfe76574dfd332bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Restituisce un'enumerazione dei simboli per il frame inline che corrispondono al percorso di origine specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` che corrisponde alla funzione stub tasti di scelta rapida che deve essere eseguita la ricerca.  
  
 `file`  
 [in] Il `IDiaSourceFile` della posizione di origine.  
  
 `linenum`  
 [in] Il numero di riga della posizione di origine.  
  
 `colnum`  
 [in] Il numero di colonna della posizione di origine.  
  
 `ppResult`  
 [out] Un puntatore a un `IDiaEnumLineNumbers` puntatore a interfaccia che viene inizializzato con il risultato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)