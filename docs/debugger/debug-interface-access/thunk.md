---
title: Thunk | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 906f1daa1df528121c63b6740702fb098c9b779f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="thunk"></a>Thunk
Ogni `thunk` è identificato da un `SymTagThunk` tag.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Attributo di modificatore di accesso, uno del [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md) valori (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte relativa all'offset di posizione. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Parte di sezione di percorso. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Contenitore padre di classe, se presente (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del contenitore simbolo padre classe (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|TRUE se il thunk è contrassegnato come costante (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|TRUE se il thunk viene fornita un'introduzione a una funzione virtuale (solo nella versione 8.0 SDK DIA o versioni successive)|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|TRUE se il thunk viene considerato statico (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Numero di byte di codice il thunk.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando, blocco o funzione contenitore.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punti di fine sono statici location; Per informazioni dettagliate, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md) enumerazione.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome del thunk.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|TRUE se il thunk è puramente virtuale (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa di questo thunk entro il relativo modulo.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagThunk` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Parte relativa all'offset della posizione della destinazione thunk.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Indirizzo virtuale relativo della destinazione thunk nel relativo blocco di inclusione.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Parte nella sezione della destinazione thunk.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Posizione della destinazione thunk nell'immagine eseguibile.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Thunk tipo, come definito dal [THUNK_ORDINAL (enumerazione)](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Il tipo di questo thunk (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID di simbolo del tipo (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se il thunk non è allineato (solo nella versione 8.0 SDK DIA o versione successiva),|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` Se il thunk è virtuale (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione di questo thunk all'interno dell'immagine eseguibile.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Offset nella tabella virtuale per questo thunk (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se il thunk viene contrassegnato come volatile (solo nella versione 8.0 SDK DIA o versione successiva).|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK_ORDINAL (enumerazione)](../../debugger/debug-interface-access/thunk-ordinal.md)