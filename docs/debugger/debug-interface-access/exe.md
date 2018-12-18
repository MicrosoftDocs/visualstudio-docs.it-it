---
title: Exe | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 899b168428428e0e4df3330691358571d7da9ed1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="exe"></a>Exe
Exe è l'unico simbolo senza un lessicale o classe padre, in quanto rappresenta l'ambito globale del file .exe o DLL. È presente un solo simbolo con la `SymTagExe` tag per ogni file. Il [idiasession:: Get_globalscope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) il metodo restituisce il simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente vengono illustrate le proprietà sono valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Tempo di memorizzazione del file eseguibile.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` del file eseguibile.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` Se il file di simboli associato a questo eseguibile contiene i tipi di C (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` Se i simboli privati sono state rimosse dal file di simboli associato a questo eseguibile (solo in DIA SDK versione 8.0 o versione successiva).|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valore che indica la CPU di destinazione (uno del [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md) valori).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome del file .exe.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Firma del file eseguibile.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Percorso completo per il file con estensione PDB o DBG di .exe del file.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagExe` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
  
## <a name="see-also"></a>Vedere anche  
 [Get_globalscope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)