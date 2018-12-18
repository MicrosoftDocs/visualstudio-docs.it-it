---
title: CONTEXT_INFO_FIELDS | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f0316e8822706b26103f02eda1849568cf79994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Specifica le informazioni da recuperare su un contesto di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Membri  
 CIF_MODULEURL  
 Inizializzazione/Usa il `bstrModuleUrl` campo il [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struttura.  
  
 CIF_FUNCTION  
 Inizializzazione/Usa il `bstrFunction` campo il `CONTEXT_INFO` struttura.  
  
 CIF_FUNCTIONOFFSET  
 Inizializzazione/Usa il `posFunctionOffset` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ADDRESS  
 Inizializzazione/Usa il `bstrAddress` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ADDRESSOFFSET  
 Inizializzazione/Usa il `bstrAddressOffset` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ALLFIELDS  
 Tutti i campi di inizializzazione/Usa il `CONTEXT_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati a un parametro per il [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metodo per indicare quali campi del [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struttura devono essere inizializzati.  
  
 Questi flag sono utilizzati anche per indicare quali campi del `CONTEXT_INFO` struttura sono validi e utilizzate quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un OR bit per bit.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)