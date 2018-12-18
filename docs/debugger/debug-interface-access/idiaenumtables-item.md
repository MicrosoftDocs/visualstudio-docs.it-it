---
title: 'Idiaenumtables:: Item | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fd0049e15f17d5dff58d35d4279bb0ab0673091e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera una tabella tramite un indice o al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Indice o nome di [IDiaTable](../../debugger/debug-interface-access/idiatable.md) da recuperare. Se si utilizza una variante dell'intero, deve essere compreso tra 0 e `count`-1, dove `count` è restituito dal [idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) metodo.  
  
 `table`  
 [out] Restituisce un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) oggetto che rappresenta la tabella desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se viene specificata una variante di stringa, la stringa di nomi di una determinata tabella. Il nome deve essere uno dei nomi di tabella come definito in [costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Esempio  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)