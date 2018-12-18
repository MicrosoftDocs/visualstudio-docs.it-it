---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Questo metodo aggiunge un nodo di programma per ogni motore di debug (DE) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidLaunchingEngine`  
 [in] Il `GUID` di un DE che deve essere utilizzato per avviare i programmi (e viene utilizzato per aggiungere nodi di programma).  
  
 `rgguidSpecificEngines`  
 [in] Matrice di `GUID`s di DEs per il programma che verranno aggiunti i nodi.  
  
 `celtSpecificEngines`  
 [in] Il numero di `GUID`s nel `rgguidSpecificEngines` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md) verranno aggiunti per ogni Germania elencati nella `rgguidSpecificEngines`, escludendo il motore di avvio (come specificato in `guidLaunchingEngine`), che vengono utilizzati per aggiungere il proprio nodo programma quando si avvia un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md)