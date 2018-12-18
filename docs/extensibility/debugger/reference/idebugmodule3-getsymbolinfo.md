---
title: IDebugModule3::GetSymbolInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53d84b9ef6cdabc12c88e30fc65d506cad673a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera un elenco di percorsi in cui vengono ricercati i simboli, nonché i risultati di ogni percorso di ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumerazione che specifica quali campi della `pInfo` deve essere compilata.  
  
 `pInfo`  
 [out] Oggetto [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) struttura i cui membri devono essere compilato con le informazioni specificate. Se questo è un valore null, questo metodo restituisce `E_INVALIDARG`.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`; in caso contrario, viene restituito un codice di errore.  
  
> [!NOTE]
>  La stringa restituita (nel `MODULE_SYMBOL_SEARCH_INFO` struttura) può essere vuoto se `S_OK` viene restituito. In questo caso, si è verificato alcuna informazione di ricerca da restituire.  
  
## <a name="remarks"></a>Note  
 Se il `bstrVerboseSearchInfo` campo il `MODULE_SYMBOL_SEARCH_INFO` struttura non è vuota, quindi contiene un elenco di percorsi di ricerca e i risultati della ricerca. L'elenco viene formattato con un percorso, seguito dai puntini di sospensione ("..."), seguita dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separato da una coppia di "\r\n" (ritorno a capo ritorno/avanzamento riga). Il modello è simile al seguente:  
  
 \<percorso >... \<risultato > \r\n\<percorso >... \<risultato > \r\n\<percorso >... \<risultato >  
  
 Si noti che l'ultima voce non dispone di una sequenza \r\n.  
  
## <a name="example"></a>Esempio  
 In questo esempio, questo metodo restituisce tre percorsi con tre risultati di ricerca diverso. Ogni riga viene terminata con una coppia di ritorno a capo ritorno avanzamento riga. Esempio di output solo stampa i risultati della ricerca come un'unica stringa.  
  
> [!NOTE]
>  Un risultato di stato è tutto quello che segue immediatamente "…" fino alla fine della riga.  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.pdb... File non trovato.**  
**c:\winnt\symbols\user32.pdb... Versione non corrisponde.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... I simboli caricati.**   
## <a name="see-also"></a>Vedere anche  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)