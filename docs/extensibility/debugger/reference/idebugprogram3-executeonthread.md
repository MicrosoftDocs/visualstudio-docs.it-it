---
title: IDebugProgram3::ExecuteOnThread | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8aff643014da16ed9644573a77cb8444836d713d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Esegue il programma del debugger. Il thread viene restituito per fornire le informazioni del debugger thread in cui l'utente visualizza quando l'esecuzione del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Esistono tre modi diversi che un debugger può riprendere l'esecuzione dopo l'arresto:  
  
-   Eseguire: Annullare qualsiasi passaggio precedente ed eseguita fino al punto di interruzione successivo e così via.  
  
-   Passaggio: Annullare un passaggio precedente ed eseguire fino a quando non viene completato il passaggio della nuova.  
  
-   Continuare: Eseguire di nuovo e lasciare attiva qualsiasi passaggio precedente.  
  
 Il thread è passato a `ExecuteOnThread` è utile quando si decide il passaggio da annullare. Se non si conosce il thread in esecuzione eseguire Annulla tutti i passaggi. Con le informazioni del thread, è necessario annullare il passaggio sul thread attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)