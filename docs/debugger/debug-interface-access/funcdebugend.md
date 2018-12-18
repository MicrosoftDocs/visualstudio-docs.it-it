---
title: FuncDebugEnd | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc51ca70fcd5d68812465b05febf63e84a2a0502
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="funcdebugend"></a>FuncDebugEnd
Se una funzione dispone di un determinato punto in cui debug è alla fine, il debug di punto di partenza è identificato da un simbolo con un `SymTagFuncDebugEnd` tag.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte relativa all'offset di posizione. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte di sezione di percorso. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Se la funzione utilizza una convenzione di chiamata personalizzata (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Se funzione esegue una distanza restituito (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Se la funzione contiene un ritorno da interrupt (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Se la funzione è statica (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per la funzione contenitrice.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punti di fine sono statici location; Per informazioni dettagliate, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Se la funzione è stata specificata con il [noinline](/cpp/cpp/noinline) attributo (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Se la funzione è stata specificata con il [noreturn](/cpp/cpp/noreturn) attributo (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Se la funzione non viene chiamata mai (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del simbolo in memoria. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Se la funzione utilizza le informazioni di debug per il codice ottimizzato (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa della fine di questa funzione all'interno al modulo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagFuncDebugEnd` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione di questa funzione all'interno dell'immagine eseguibile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)