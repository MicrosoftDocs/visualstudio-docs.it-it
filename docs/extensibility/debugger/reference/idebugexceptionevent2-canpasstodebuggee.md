---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3a443b3f88ec64d24ea7a5bf4db682e5aa10b2eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se il motore di debug (DE) supporta l'opzione del passaggio di questa eccezione a un programma sottoposto a debug durante l'esecuzione riprende.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `S_OK` (l'eccezione può essere passato al programma) o `S_FALSE` (l'eccezione non può essere passato).  
  
## <a name="remarks"></a>Note  
 La Germania deve avere un'azione predefinita per il passaggio per l'oggetto del debug. L'IDE è possibile che venga visualizzato il [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventi e chiamate di [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo senza chiamare il `CanPassToDebuggee` (metodo). Di conseguenza, la Germania dovrebbe avere un case predefinito per trasmettere l'eccezione o non.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)