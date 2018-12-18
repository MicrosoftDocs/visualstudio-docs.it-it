---
title: IDebugProcess2::Terminate | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3bb6c47a95ff77d19ea8f6cb8803e416c35148c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Termina il processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando un processo viene terminato, vengono terminati tutti i programmi all'interno del processo; non sono consentiti per l'esecuzione di qualsiasi altro codice.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)