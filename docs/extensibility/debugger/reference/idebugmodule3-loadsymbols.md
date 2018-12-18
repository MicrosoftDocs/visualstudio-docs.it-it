---
title: IDebugModule3::LoadSymbols | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7f7a08e827b22f7011fe97babf1a57882245649
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carica i simboli per il modulo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo carica i simboli dal percorso di ricerca corrente (che può essere modificato chiamando il [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) (metodo)).  
  
 Questo metodo è preferibile il [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)