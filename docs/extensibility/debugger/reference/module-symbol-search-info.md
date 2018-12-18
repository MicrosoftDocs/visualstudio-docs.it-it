---
title: MODULE_SYMBOL_SEARCH_INFO | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb62fb0a830c8c3bf6bb9b7ca186e001573b7b37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Contiene informazioni sui percorsi di ricerca di simboli che alcuno.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwValidFields`  
 Una combinazione di flag dal [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumerazione che specifica il tipo di informazioni di ricerca descritte in questa struttura.  
  
 `bstrVerboseSearchInfo`  
 Percorso di ricerca e risultati concatenati in una singola stringa.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita da una chiamata al [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) metodo.  
  
 Se il `bstrVerboseSearchInfo` campo non è vuoto, quindi contiene un elenco di percorsi di ricerca e i risultati della ricerca. L'elenco viene formattato con un percorso, seguito dai puntini di sospensione ("..."), seguita dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separato da una coppia di "\r\n" (ritorno a capo ritorno/avanzamento riga). Il modello è simile al seguente:  
  
 \<percorso >... \<risultato > \r\n\<percorso >... \<risultato > \r\n\<percorso >... \<risultato >  
  
 Si noti che l'ultima voce non dispone di una sequenza \r\n.  
  
 Ecco un possibile `bstrVerboseSearchInfo` stringa che è stato inviato a un output standard.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)