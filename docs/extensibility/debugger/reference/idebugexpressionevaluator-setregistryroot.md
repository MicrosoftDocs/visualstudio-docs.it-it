---
title: IDebugExpressionEvaluator::SetRegistryRoot | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70b1730fc44deeb7e32433480f02f750c9bec193
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Questo metodo imposta la radice del Registro di sistema. Usato per il debug side-by-side.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ustrRegistryRoot`  
 [in] Il nuovo oggetto radice del Registro di sistema.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La radice del Registro di sistema viene in genere impostata quando l'analizzatore di espressioni viene innanzitutto creata un'istanza e fa riferimento alla chiave del Registro di sistema per una specifica versione di Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y* , dove *x. y* è un numero di versione).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)