---
title: CODE_PATH | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CODE_PATH
helpviewer_keywords: CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dd2cd5de0d415e133beb6b72b63b9d42eb61c947
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="codepath"></a>CODE_PATH
Descrive una chiamata di funzione o metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Membri  
 bstrName  
 Il nome del percorso del codice.  
  
 pCode  
 Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che identifica in cui il codice per eseguire una funzione.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene utilizzata per implementare l'esecuzione di una funzione. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) restituisce tutte le chiamate dalla posizione corrente nel programma sottoposto a debug. Questa struttura rappresenta una chiamata di questo tipo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)