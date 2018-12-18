---
title: MODULE_INFO | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO
helpviewer_keywords: MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd49230165282dd656252c4edaabfbaa31d43340
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfo"></a>MODULE_INFO
Descrive un particolare modulo (DLL, EXE o assembly).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```csharp  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## <a name="members"></a>Membri  
 dwValidFields  
 Una combinazione di flag dal [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumerazione che specifica quali campi vengono compilati.  
  
 m_bstrName  
 Nome del modulo.  
  
 m_bstrUrl  
 L'URL del modulo.  
  
 m_bstrVersion  
 La versione del modulo.  
  
 m_bstrDebugMessage  
 Un messaggio facoltativo sul modulo, ad esempio, "non è possibile caricare i simboli."  
  
 m_addrLoadAddress  
 L'indirizzo di caricamento del modulo.  
  
 m_addrPreferredLoadAddress  
 L'indirizzo di caricamento preferito del modulo.  
  
 m_dwSize  
 Le dimensioni del modulo.  
  
 m_dwLoadOrder  
 L'ordine di caricamento del modulo.  
  
 m_TimeStamp  
 L'ora che dell'ultima modifica il file di simboli.  
  
 m_bstrUrlSymbolLocation  
 Il percorso del file di simboli (ad esempio, ".\\") specificato nel modulo. Utilizzato come percorso inizio per trovare i simboli per un modulo.  
  
 m_dwModuleFlags  
 Una combinazione di flag dal [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) enumerazione che descrive il modulo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) (metodo) in cui viene compilato.  
  
 Questa struttura corrisponde a ogni modulo nel **moduli** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)