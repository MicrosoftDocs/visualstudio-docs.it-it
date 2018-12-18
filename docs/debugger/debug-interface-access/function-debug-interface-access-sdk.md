---
title: Funzione (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f18ff7e00a1e48063d64ced832cc6a57e05853df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="function-debug-interface-access-sdk"></a>Funzione (Debug Interface Access SDK)
Ogni funzione è identificata da un `SymTagFunction` simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|`Data type`|Descrizione|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Uno dei valori del [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md), se la funzione è una funzione membro.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte relativa all'offset di posizione. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte di sezione di percorso. Per informazioni dettagliate, vedere il [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Simbolo per la classe, se la funzione è una funzione membro.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo classe padre.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se la funzione è contrassegnata come costante.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Se la funzione utilizza una convenzione di chiamata personalizzata (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Se la funzione esegue una distanza restituito (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` Se la funzione utilizza memoria allocata funzione (solo uinnder versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` Se la funzione contiene stile C++ delle eccezioni (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` Se la funzione contiene eccezioni asincrone (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` Se la funzione contiene assembly inline (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` Se la funzione contiene un [longjmp](/cpp/c-runtime-library/reference/longjmp) chiamare (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Se la funzione contiene controlli di sicurezza (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` Se la funzione contiene stile Win32 strutturata delle eccezioni (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` Se la funzione contiene un [setjmp](/cpp/c-runtime-library/reference/setjmp) chiamare (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Se la funzione ha restituito da interrupt (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` Se una funzione è intro virtuale.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` Se la funzione è stata contrassegnata con uno del [inline, inline, \__forceinline](/cpp/cpp/inline-functions-cpp) attributi.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` Se la funzione è contrassegnata con il [naked](/cpp/cpp/naked-cpp) attributo (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Se la funzione è statica (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Numero di byte di codice della funzione, a partire dalla posizione.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando il contenitore.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Le funzioni possono avere siti statico o metadati. Per informazioni dettagliate, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome della funzione.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Se la funzione non è una funzione inline (solo n DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Se la funzione non è raggiungibile (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Se la funzione non restituisce un valore (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` Se è stata compilata la funzione con i controlli di sicurezza buffer ma nessun ordinamento stack poteva essere eseguito.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Se il codice presenta le informazioni di debug per il codice ottimizzato (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` Se è pura funzione virtuale.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa di questa funzione all'interno al modulo.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagFunction` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token di metadati per la funzione.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Simbolo per la firma della funzione.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID di simbolo del tipo.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se la funzione non è allineata.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Il formato non decorato del nome della funzione (solo nella versione 8.0 DIA SDK o versioni successive)|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Parte o tutto il formato non decorato del nome della funzione (solo nella versione 8.0 DIA SDK o versione successiva).|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` Se una funzione virtuale.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione di questa funzione all'interno dell'immagine eseguibile.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Se una funzione virtuale, quindi l'offset nella tabella di funzioni virtuali.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se la funzione è contrassegnata come volatile.|  
  
## <a name="see-also"></a>Vedere anche  
 [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)