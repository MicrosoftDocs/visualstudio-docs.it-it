---
title: IDiaEnumSymbols | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb30549dc50b9e585768cd8778b8cbb70fb0f0c0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
Enumera i vari simboli contenuti nell'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumSymbols`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Recupera il `IEnumVARIANT Interface` versione di questo enumeratore.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Recupera il numero di simboli.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Recupera un simbolo mediante un indice.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Recupera un numero specificato di simboli nella sequenza di enumerazione.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignora un numero specificato di simboli in una sequenza di enumerazione.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia fornisce i simboli raggruppati in base a un tipo specifico del simbolo, ad esempio, `SymTagUDT` (tipi definiti dall'utente) o `SymTagBaseClass`. Per utilizzare i simboli raggruppati per indirizzo, utilizzare il [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Per ottenere questa interfaccia, la chiamata dei metodi seguenti:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaEnumSymbols` l'interfaccia e quindi utilizzare tale enumerazione di tipi di elenco definito dall'utente (UDT).  
  
> [!NOTE]
>  `CDiaBSTR` è una classe che esegue il wrapping di un `BSTR` e gestisce automaticamente liberando la stringa quando la creazione dell'istanza diventa esterno all'ambito.  
  
```C++  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
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
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)