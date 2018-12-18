---
title: IDebugExpressionContext2::GetName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84ac767c8e2cd53045dec9921f6d90300f1a87e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Recupera il nome del contesto di valutazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrName`  
 [out] Restituisce il nome del contesto di valutazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome è la descrizione di questo contesto di valutazione. È in genere un elemento che può essere analizzata tramite un analizzatore di espressioni che fa riferimento a questo contesto di valutazione esatta. Ad esempio, in C++ il nome è come segue:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)