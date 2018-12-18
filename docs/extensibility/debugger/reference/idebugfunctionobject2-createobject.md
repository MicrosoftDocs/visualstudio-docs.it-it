---
title: IDebugFunctionObject2::CreateObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5283d72972e1ba579cafa82648cbf0ec0fcf80c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crea un oggetto che usa un costruttore base impostazioni dei flag di valutazione e un valore di timeout.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pConstructor`  
 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto che rappresenta il costruttore dell'oggetto da creare.  
  
 `dwArgs`  
 [in] Il numero di parametri in di `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.  
  
 `pArgs`  
 [in] Matrice di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) gli oggetti che rappresenta i parametri passati al costruttore.  
  
 `dwEvalFlags`  
 [in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che specificano la modalità è necessario eseguire la valutazione.  
  
 `dwTimeout`  
 [in] Tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare **infinito** per un'attesa indefinita.  
  
 `ppObject`  
 [out] Restituisce un **IDebugObject** che rappresenta l'oggetto appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe o di altro tipo complesso che richiede un costruttore, che è un parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)