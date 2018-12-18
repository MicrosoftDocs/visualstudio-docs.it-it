---
title: IActiveScript::GetScriptDispatch | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera il `IDispatch` interfaccia per i metodi e proprietà associate allo script attualmente in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrItemName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento per cui il chiamante necessita l'oggetto di distribuzione associati. Se questo parametro è `NULL`, contiene l'oggetto distribuzione come membri di tutte le proprietà e metodi globali definite dallo script. Tramite il `IDispatch` interfaccia e tale `ITypeInfo` interfaccia, l'host è possibile richiamare i metodi di script o una vista e modificare le variabili dello script.  
  
 `ppdisp`  
 [out] Indirizzo di una variabile che riceve un puntatore all'oggetto associato a metodi globali e le proprietà dello script. Se il motore di script non supporta tale tipo di oggetto, `NULL` viene restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
|`S_FALSE`|Il motore di script non supporta un oggetto di distribuzione. il `ppdisp` parametro è impostato su NULL.|  
  
## <a name="remarks"></a>Note  
 Poiché è possibile aggiungere proprietà e metodi chiamando il [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfaccia, il `IDispatch` restituito da questo metodo di interfaccia in modo dinamico può supportare nuovi metodi e proprietà. Analogamente, il `IDispatch::GetTypeInfo` metodo deve restituire un nuovo, univoco `ITypeInfo` quando vengono aggiunti i metodi e proprietà di interfaccia. Si noti tuttavia che i motori di lingua non è necessario modificare il `IDispatch` interfaccia in modo che è incompatibile con i precedenti `ITypeInfo` interfaccia restituita. Questa situazione implica, ad esempio, che non verranno riutilizzati mai DISPID.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)