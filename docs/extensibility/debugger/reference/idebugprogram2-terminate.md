---
title: IDebugProgram2::Terminate | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5eb14280947ff93a4a0c2ab6d2cf025037fc06aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termina il programma.  
  
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
 Se possibile, verrà terminato e scaricato dal processo; il programma in caso contrario, il motore di debug (DE) eseguirà le operazioni di pulitura necessarie.  
  
 Questo metodo o [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metodo viene chiamato dall'IDE, in genere in risposta all'utente di interrompere il debug tutti. L'implementazione di questo metodo deve, in teoria, terminare il programma all'interno del processo. In caso contrario, la Germania deve impedire che il programma in esecuzione altri in questo processo ed eseguire operazioni di pulitura necessarie. Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato un po' dopo il `IDebugProgram2::Terminate` metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminare](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)