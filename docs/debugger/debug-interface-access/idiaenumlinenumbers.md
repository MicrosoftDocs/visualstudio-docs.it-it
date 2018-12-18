---
title: IDiaEnumLineNumbers | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fb0b457a0efef1c860be7174f012575aec64f99
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
Enumera i numeri di riga diversi contenuti nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumLineNumbers : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumLineNumbers`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|Recupera il [interfaccia IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versione di questo enumeratore.|  
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|Recupera il numero di numeri di riga.|  
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|Recupera un numero di riga tramite un indice.|  
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|Recupera un numero specificato di numeri di riga nella sequenza di enumerazione.|  
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|Ignora un numero specificato di numeri di riga in una sequenza di enumerazione.|  
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta chiamando uno dei seguenti metodi di [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia:  
  
-   [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)  
  
-   [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)  
  
-   [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)  
  
-   [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)  
  
-   [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaEnumLineNumbers` interfaccia da una sessione. In questo caso, nell'esempio viene illustrato come ottenere l'enumerazione di numeri di riga per una funzione (rappresentato da `pSymbol`). Per un esempio più completo dell'utilizzo di numeri di riga, vedere il [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) interfaccia.  
  
```C++  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD isect = 0;  
    DWORD offset = 0;  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines )  
                      )  
           )  
        {  
            // Do something with the enumeration  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [Findlinesbyrva](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)   
 [Findlinesbyva](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)   
 [Findlines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)