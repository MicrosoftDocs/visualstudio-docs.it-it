---
title: IDiaEnumTables | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26b4e6ae104bb0ba50c7be60944f6397fda6a637
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Enumera le varie tabelle contenute nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumTables`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Recupera il [interfaccia IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera il numero di tabelle.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera una tabella tramite un indice o un nome.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera un numero specificato di tabelle nella sequenza di enumerazione.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora un numero specificato di tabelle in una sequenza di enumerazione.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodo.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaEnumTables` interfaccia da una sessione. Per un esempio più completo di utilizzo di tabelle, vedere il [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)