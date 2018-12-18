---
title: IActiveScript::AddTypeLib | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Aggiunge una libreria dei tipi per lo spazio dei nomi per lo script. È simile al `#include` direttiva in C/C++. Consente a un set di elementi predefiniti, ad esempio le definizioni di classe, `typedefs`, denominato costanti da aggiungere all'ambiente di runtime disponibile per lo script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidTypeLib`  
 [in] CLSID della libreria dei tipi da aggiungere.  
  
 `dwMaj`  
 [in] Numero di versione principale.  
  
 `dwMin`  
 [in] Numero di versione secondario.  
  
 `dwFlags`  
 [in] Flag di opzione. Può essere il seguente:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La libreria dei tipi viene descritto un controllo ActiveX utilizzato dall'host.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
|`TYPE_E_CANTLOADLIBRARY`|Impossibile caricare la libreria dei tipi specificata.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)