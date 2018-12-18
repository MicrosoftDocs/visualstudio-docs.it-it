---
title: IDebugProgram3::ExecuteOnThread | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 649b16c1b57b2f66772c2117b776e6b79ad862be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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