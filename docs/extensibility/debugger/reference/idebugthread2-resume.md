---
title: IDebugThread2::Resume | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::Resume
helpviewer_keywords: IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5de844c3b07a509f266e2f9d278d1f78bea2b089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Riprende l'esecuzione di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSuspendCount`  
 [out] Restituisce il conteggio di sospensione dopo l'operazione di ripresa.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Con ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a raggiungere 0 a quel punto, l'esecuzione viene ripresa effettivamente. Questo conteggio di sospensione viene visualizzato nel **thread** finestra di debug.  
  
 Per ogni chiamata a questo metodo, deve essere una chiamata precedente al [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metodo. Il conteggio di sospensione determina quante volte il `IDebugThread2::Suspend` metodo è stato chiamato finora.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)