---
title: MESSAGETYPE | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa09d938e0e7c3853431369c7e0634242df2ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="messagetype"></a>MESSAGETYPE
Specifica il tipo di messaggio e il motivo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Membri  
 MT_OUTPUTSTRING  
 Indica che deve essere inviato il messaggio nella finestra di output. Questo si escludono a vicenda da `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Questo si escludono a vicenda da `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Un valore di maschera per isolare la destinazione per il messaggio.  
  
 MT_REASON_EXCEPTION  
 Indica che una finestra di messaggio viene visualizzata come risultato di un'eccezione. Questo si escludono a vicenda da `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indica che una finestra di messaggio viene visualizzata in seguito a raggiungere un punto di analisi. Questo si escludono a vicenda per `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Un valore di maschera per isolare il motivo per il messaggio venga visualizzato.  
  
## <a name="remarks"></a>Note  
 Questi valori sono restituiti dal [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metodi.  
  
 Uno dei valori di motivo può essere combinato con uno dei valori di destinazione di output utilizzando un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)