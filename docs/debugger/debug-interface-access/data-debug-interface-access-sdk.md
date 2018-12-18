---
title: Dati (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cc11de394ab53b1f223b008535efc1d83936de2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="data-debug-interface-access-sdk"></a>Dati (Debug Interface Access SDK)
Tutte le variabili, ad esempio parametri, variabili locali, le variabili globali e i membri di classe, vengono identificate da `SymTagData` simboli. Valori costanti (`LocIsConstant`) vengono anche identificati con questo tipo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Se un campo, quindi uno dei valori del [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte relativa all'offset di posizione. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte di sezione di percorso. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` Se l'indirizzo dei dati fa riferimento un altro simbolo.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Posizione del bit di percorso. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md) (non supportato nella versione 8.0 DIA SDK).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Simbolo per la classe, se si tratta di una struttura, unione o campo della classe.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo classe padre.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` Se i dati è stati generati dal compilatore.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se i dati vengono contrassegnati come costante.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Uno del [DataKind (enumerazione)](../../debugger/debug-interface-access/datakind.md) valori.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` Se i dati sono parte di un tipo di dati aggregati (solo in DIA SDK versione 8.0 e versioni successive).|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` Se i dati è stata suddivisa in un'aggregazione di più simboli (solo in DIA SDK versione 8.0 e versioni successive).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Lunghezza del campo di bit; Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando, funzione o di blocco di inclusione.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|I tipi di percorso consentiti; Per informazioni dettagliate, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della variabile.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset dal contenuto del Registro; Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Registrare l'indicatore di posizione. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa dei dati nel relativo blocco.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Ottiene il numero di slot di dati.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagData` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Il token di metadati che rappresenta i dati.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Simbolo per il tipo di variabile.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID di simbolo del tipo di variabile.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se i dati non allineati.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Il valore di dati costanti.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione dei dati all'interno dell'eseguibile.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se i dati vengono contrassegnati come volatile.|  
  
## <a name="see-also"></a>Vedere anche  
 [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md)   
 [DataKind (enumerazione)](../../debugger/debug-interface-access/datakind.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)