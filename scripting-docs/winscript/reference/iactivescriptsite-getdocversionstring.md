---
title: IActiveScriptSite::GetDocVersionString | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una stringa definita dall'host che identifica in modo univoco la versione del documento corrente. Se il documento correlato è stato modificato all'esterno dell'ambito dello Script di Windows (come nel caso di una pagina HTML modificato con il blocco note), il motore di script può salvare questo oltre allo stato persistente, forzare una ricompilazione al successivo che caricamento dello script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrVersionString`  
 [out] Indirizzo della stringa di versione del documento definita dall'host.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_NOTIMPL` se questo metodo non è supportato.  
  
## <a name="remarks"></a>Note  
 Se `E_NOTIMPL` viene restituito, il motore di script deve presupporre che lo script è sincronizzato con il documento.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)