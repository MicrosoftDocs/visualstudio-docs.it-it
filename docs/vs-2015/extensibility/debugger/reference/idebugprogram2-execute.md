---
title: IDebugProgram2::Execute | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfc486b307483f2f9a68ee43562e5449f3900ca6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286351"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continua l'esecuzione di questo programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio, un passaggio) sia deselezionata, e il programma inizia l'esecuzione anche in questo caso.  
  
> [!NOTE]
>  Questo metodo è deprecato. Usare la [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metodo invece.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 Quando l'utente avvia l'esecuzione da uno stato di interruzione nel thread di alcuni degli altri programmi, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il **avviare** dalle **Debug** menu nell'IDE. L'implementazione di questo metodo potrebbe essere semplice come chiamare le [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente nel programma.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)

