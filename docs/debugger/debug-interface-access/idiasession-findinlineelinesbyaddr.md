---
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a26692a7c8715150cad071b9c0871e0b8ad9e239
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896672"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni numeriche della riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo del padre specificato e è contenuta all'interno dell'intervallo di indirizzi specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` oggetto che rappresenta l'elemento padre.  
  
 `isect`  
 [in] Specifica il componente di sezione dell'indirizzo.  
  
 `offset`  
 [in] Specifica il componente offset dell'indirizzo.  
  
 `length`  
 [in] Specifica l'intervallo di indirizzi, in numero di byte, per coprire la query viene usata.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumLineNumbers` oggetto che contiene l'elenco dei numeri di riga recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)