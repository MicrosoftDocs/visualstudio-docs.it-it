---
title: IDebugProgram2::Execute | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Execute
helpviewer_keywords: IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2e53f13aea93de8f39c5802dd2a12598ad938f64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua l'esecuzione di questo programma da uno stato di arresto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) è deselezionata, e il programma viene avviato l'esecuzione di nuovo.  
  
> [!NOTE]
>  Questo metodo è deprecato. Utilizzare il [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metodo invece.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando l'utente avvia l'esecuzione da uno stato di interruzione di thread di alcuni degli altri programmi, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il **avviare** comando il **Debug** menu nell'IDE. L'implementazione di questo metodo può essere semplice come chiamare il [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente nel programma.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)