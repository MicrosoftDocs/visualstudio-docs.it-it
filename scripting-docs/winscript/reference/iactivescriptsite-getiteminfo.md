---
title: IActiveScriptSite::GetItemInfo | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Consente al motore di scripting ottenere informazioni su un elemento aggiunto con il [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrName`  
 [in] Il nome associato all'elemento, come specificato nella [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metodo.  
  
 `dwReturnMask`  
 [in] Maschera di bit che specifica le informazioni sull'elemento devono essere restituite. Il motore di script deve richiedere la quantità minima possibile di informazioni perché alcuni dei parametri restituiti (ad esempio, `ITypeInfo`) può richiedere molto tempo per caricare o generare. Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Restituisce il `IUnknown` interfaccia per questo elemento.|  
|SCRIPTINFO_ITYPEINFO|Restituisce il `ITypeInfo` interfaccia per questo elemento.|  
  
 `ppunkItem`  
 [out] Indirizzo di una variabile che riceve un puntatore di `IUnknown` interfaccia associata con l'elemento specificato. Il motore di script è possibile utilizzare il `IUnknown::QueryInterface` per ottenere il `IDispatch` interfaccia per l'elemento. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_IUNKNOWN. Inoltre, riceve NULL se nessun oggetto associato al nome di elemento; Questo meccanismo viene utilizzato per creare una classe semplice di quando è stato aggiunto l'elemento denominato con il flag SCRIPTITEM_CODEONLY impostato nella [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metodo.  
  
 `ppTypeInfo`  
 [out] Indirizzo di una variabile che riceve un puntatore di `ITypeInfo` associato all'elemento di interfaccia. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_ITYPEINFO, o se le informazioni sul tipo non è disponibile per questo elemento. Se le informazioni sul tipo non è disponibile, l'oggetto non è l'origine degli eventi e associazione del nome deve essere realizzato con il `IDispatch::GetIDsOfNames` metodo. Si noti che il `ITypeInfo` interfaccia recuperata descrive coclasse dell'elemento (TKIND_COCLASS) perché l'oggetto può supportare più interfacce e le interfacce di eventi. Se l'elemento supporta la `IProvideMultipleTypeInfo` interfaccia, il `ITypeInfo` interfaccia recuperata corrisponde all'indice zero `ITypeInfo` che sarebbe ottenuto utilizzando il `IProvideMultipleTypeInfo::GetInfoOfIndex` metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un elemento con il nome specificato non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera solo le informazioni indicate dal `dwReturnMask` parametro; Ciò migliora le prestazioni. Ad esempio, se un `ITypeInfo` interfaccia non è necessaria per un elemento, non è semplicemente specificato `dwReturnMask`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)