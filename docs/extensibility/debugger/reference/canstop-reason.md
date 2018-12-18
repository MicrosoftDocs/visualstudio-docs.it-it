---
title: CANSTOP_REASON | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CANSTOP_REASON
helpviewer_keywords: CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98b1e4a9db18490079dd443cb296481aed64376a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="canstopreason"></a>CANSTOP_REASON
Utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un determinato punto dell'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membri  
 CANSTOP_ENTRYPOINT  
 Specifica il punto di ingresso del programma specificato.  
  
 CANSTOP_STEPIN  
 Specifica l'esecuzione di istruzioni in una funzione.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per verificare con sessione di Debug Manager (SDM) se è possibile arrestare dopo aver raggiunto il punto di ingresso del programma o dopo l'esecuzione di una funzione o metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)