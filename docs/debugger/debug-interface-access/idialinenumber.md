---
title: IDiaLineNumber | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 735b15f76d9cb679e6fda2327e4af0dc3d84c8a0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialinenumber"></a>IDiaLineNumber
Si accede alle informazioni che descrive il processo di mapping da un blocco di byte di testo da un'immagine a un numero di riga di file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaLineNumber`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Recupera un riferimento al simbolo per il modulo che hanno contribuito i byte di testo di immagine.|  
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Recupera un riferimento all'oggetto di file di origine.|  
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Recupera il numero di riga nel file di origine.|  
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Recupera il numero di riga di origine basato su uno in cui termina l'istruzione o espressione.|  
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Recupera il numero di colonna in cui inizia l'istruzione o espressione.|  
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Recupera il numero di colonna in cui termina l'espressione o istruzione.|  
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Recupera la parte della sezione dell'indirizzo di memoria in cui inizia un blocco.|  
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Recupera la parte relativa all'offset dell'indirizzo di memoria in cui inizia un blocco.|  
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Recupera l'immagine indirizzo virtuale relativo (RVA) di un blocco.|  
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Recupera l'indirizzo virtuale (VA) di un blocco.|  
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Recupera il numero di byte in un blocco.|  
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Recupera un identificatore di file di origine univoco per il file di origine che hanno contribuito a questa riga.|  
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Recupera un flag che indica che le informazioni di riga vengono descritti l'inizio di un'istruzione all'origine del programma.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Recupera l'identificatore univoco per il modulo che hanno contribuito a questa riga.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il [idiaenumlinenumbers:: Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) o [idiaenumlinenumbers:: Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) metodi.  
  
## <a name="example"></a>Esempio  
 La funzione seguente consente di visualizzare i numeri di riga utilizzati in una funzione (rappresentato da `pSymbol`).  
  
```C++  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
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
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
                }  
            }  
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [Idiaenumlinenumbers](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)