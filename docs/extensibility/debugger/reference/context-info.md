---
title: CONTEXT_INFO | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO
helpviewer_keywords: CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 46168fefd491aeeae05c6406bd2b985fc5649bd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfo"></a>CONTEXT_INFO
Questa struttura viene descritto un contesto di memoria o il contesto di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag da egli [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumerazione che specifica quali campi vengono compilati**.**  
  
 bstrModuleUrl  
 Il nome del modulo in cui si trova il contesto.  
  
 bstrFunction  
 Il nome della funzione in cui si trova il contesto.  
  
 posFunctionOffset  
 Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che identifica l'offset di riga e colonna della funzione associata al contesto di codice.  
  
 bstrAddress  
 L'indirizzo nel codice in cui si trova il contesto specificato.  
  
 bstrAddressOffset  
 L'offset dell'indirizzo nel codice in cui si trova il contesto specificato.  
  
 bstrAddressAbsolute  
 L'indirizzo assoluto in memoria in cui si trova il contesto specificato.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita da una chiamata al [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metodo.  
  
 Un tipico utilizzo di questa struttura è supportano un **memoria** finestra di debug.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)