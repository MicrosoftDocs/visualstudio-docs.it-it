---
title: Costanti (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c77febb7ad9f41880fef604849af75aa065ff593
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="constants-debug-interface-access-sdk"></a>Costanti (Debug Interface Access SDK)
Per identificare diverse sezioni di un file di database di (programma PDB) programma debug tramite il DIA SDK, è possono utilizzare queste costanti di stringa.  
  
## <a name="constants"></a>Costanti  
 Di seguito viene dichiarati come macro C/C++.  
  
|Macro|Valore|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Simboli"|  
|`DiaTable_Sections`|L "Sezioni"|  
|`DiaTable_SrcFiles`|L "SourceFiles"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L "SegmentMap"|  
|`DiaTable_Dbg`|L "Dbg"|  
|`DiaTable_InjSrc`|L "InjectedSource"|  
|`DiaTable_FrameData`|L "FrameData"|  
  
## <a name="example"></a>Esempio  
 Di seguito è riportato un esempio di utilizzo di uno di questi simboli:  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)