---
title: IDebugModule2::ReloadSymbols_Deprecated | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcd383130c1af1765014adfa438482543c336ede
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszUrlToSymbols`  
 [in] Il percorso dell'archivio simboli.  
  
 `pbstrDebugMessage`  
 [out] Restituisce un messaggio informativo, ad esempio un messaggio di stato o di errore, che viene visualizzato a destra del nome del modulo nella finestra moduli.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un motore di debug deve sempre restituire `E_FAIL`.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è più supportato. Implementare il [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) metodo invece.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)