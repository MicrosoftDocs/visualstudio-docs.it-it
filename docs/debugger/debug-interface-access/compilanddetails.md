---
title: CompilandDetails | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16f9239028cada1108092af3bc5a511964f89c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="compilanddetails"></a>CompilandDetails
Informazioni di modulo viene suddiviso tra i simboli con un `SymTagCompiland` tag (dettagli bassa) e un `SymTagCompilandDetails` tag (alta dettagli). `SymTagCompilandDetails` richiede il caricamento dei simboli aggiuntivi. Tuttavia, fornisce una serie di informazioni sul modulo che non è disponibile con un `SymTagCompiland` simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numero di build di back-end del compilatore.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numero di versione principale di back-end del compilatore.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numero di versione secondaria di back-end del compilatore.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome del compilatore che ha generato questo modulo (solo nella versione 8.0 di DIA SDK o versione successiva).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Se la compilazione fosse abilitata la funzionalità Modifica e continuazione.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numero di build front-end del compilatore.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numero di versione principale front-end del compilatore.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numero di versione secondaria front-end del compilatore.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Se questo modulo include le informazioni di debug (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Se questo modulo contiene il codice gestito (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/GS (controllo sicurezza Buffer)](/cpp/build/reference/gs-buffer-security-check) opzione del compilatore (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Se il modulo è stato convertito dal codice Common Intermediate Language (CIL) al codice nativo.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Se i tipi definiti dall'utente (UDT) sono stati allineati a alcune specificate limite di memoria (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/hotpatch (Crea immagine hot patch)](/cpp/build/reference/hotpatch-create-hotpatchable-image) opzione del compilatore (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Se il modulo è stato compilato con il [/LTCG (generazione codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation) opzione del compilatore (solo nella versione 8.0 SDK DIA o versione successiva).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE se il modulo è un modulo di Microsoft Intermediate Language (MSIL) (solo nella versione 8.0 DIA SDK o versione successiva).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Linguaggio del codice sorgente.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il modulo.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Piattaforma in cui è stato compilato il modulo (uno del [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md) valori).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandDetails` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
  
## <a name="remarks"></a>Note  
 I compilatori sono spesso in un formato noto come un compilatore due passaggi. in alcune versioni del compilatore, ogni passaggio è gestita da un programma separato. Questi sono conosciuti come front-end e back-end di compilatori, rispettivamente, di conseguenza le proprietà dei simboli per i numeri di versione di back-end e front-end.  
  
## <a name="see-also"></a>Vedere anche  
 [Modulo](../../debugger/debug-interface-access/compiland.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)