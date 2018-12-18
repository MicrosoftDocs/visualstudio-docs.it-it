---
title: IDebugProgramProvider2::GetProviderProcessData | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77a6da58083feb8699c6db24207c265bf50c0f0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera un elenco dei programmi in esecuzione da un processo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Flags`  
 [in] Una combinazione di flag dal [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumerazione. I flag seguenti sono più comuni per questa chiamata:  
  
|Flag|Descrizione|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Chiamante è in esecuzione sul computer remoto.|  
|`PFLAG_DEBUGGEE`|Chiamante è in corso il debug (ulteriori informazioni di marshalling restituite per ogni nodo).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chiamante è stato collegato ma non è stato avviato dal debugger.|  
|`PFLAG_GET_PROGRAM_NODES`|Per un elenco di nodi programma chiamante richiede da restituire.|  
  
 `pPort`  
 [in] La porta del processo chiamante è in esecuzione.  
  
 `processId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che contiene l'ID del processo che contiene il programma in questione.  
  
 `EngineFilter`  
 [in] Una matrice di GUID per i motori di debug assegnato per eseguire il debug di questo processo (saranno usati per filtrare i programmi che vengono effettivamente restituiti basati su ciò che supportano i motori forniti; se nessun motore vengono specificato, quindi verranno restituiti tutti i programmi).  
  
 `pProcess`  
 [out] Oggetto [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struttura che viene compilato con le informazioni richieste.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, questo metodo viene chiamato da un processo per ottenere un elenco di programmi in esecuzione in tale processo. Le informazioni restituite sono un elenco di [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetti.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)