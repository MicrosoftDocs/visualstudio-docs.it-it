---
title: FRAMEINFO | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO
helpviewer_keywords: FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b3fd52fb80cd2bd588951b6a921ca157935a3a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="frameinfo"></a>FRAMEINFO
Viene descritto uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>Membri  
 m_dwValidFields  
 Una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi vengono compilati.  
  
 m_bstrFuncName  
 Il nome della funzione associato a uno stack frame.  
  
 m_bstrReturnType  
 Il tipo restituito associato al frame dello stack.  
  
 m_bstrArgs  
 Gli argomenti della funzione associata a uno stack frame.  
  
 m_bstrLanguage  
 La lingua in cui la funzione è implementata.  
  
 m_bstrModule  
 Il nome del modulo associato a uno stack frame.  
  
 m_addrMin  
 L'indirizzo minima dello stack fisico.  
  
 m_addrMAX  
 L'indirizzo massima dello stack fisico.  
  
 m_pFrame  
 Il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) oggetto che rappresenta questo stack frame.  
  
 m_pFrame  
 Il [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) oggetto che rappresenta il modulo che contiene questo stack frame.  
  
 m_fHasDebugInfo  
 Diverso da zero (`TRUE`) se esistono informazioni di debug nel frame specificato.  
  
 m_fHasDebugInfo  
 Diverso da zero (`TRUE`) se il frame dello stack è associato a codice non è più valido.  
  
 m_fHasDebugInfo  
 Diverso da zero (`TRUE`) se il frame dello stack è annotato dal gestore di sessione di debug (SDM).  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metodo deve essere compilato. Questa struttura è contenuta anche in un elenco di contenuti nel [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata al [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)