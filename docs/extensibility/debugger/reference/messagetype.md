---
title: MESSAGETYPE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MESSAGETYPE
helpviewer_keywords: MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4c507575442d188e7a273559689cc782f00d51c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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