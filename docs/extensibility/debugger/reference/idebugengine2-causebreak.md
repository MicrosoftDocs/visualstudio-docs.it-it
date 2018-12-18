---
title: IDebugEngine2::CauseBreak | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ba10e167246ce2467f2faebf157e46306749bdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Le richieste di tutti i programmi in corso il debug da questo motore di debug (DE) per arrestare l'esecuzione, la volta successiva che uno dei relativi thread tenta di eseguire.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è asincrono: un [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento viene inviato quando il programma successivo tentativo di eseguire dopo la chiamata di questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)