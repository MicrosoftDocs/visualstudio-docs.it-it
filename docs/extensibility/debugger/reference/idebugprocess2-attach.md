---
title: IDebugProcess2::Attach | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56f14b399a904c2584e81c2b6c8f344654b69a18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Collega il gestore di sessione di debug (SDM) al processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto utilizzato per la notifica degli eventi di debug.  
  
 `rgguidSpecificEngines`  
 [in] Matrice di GUID di motori di debug da utilizzare per eseguire il debug di programmi in esecuzione nel processo. Questo parametro può essere un valore null. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 `celtSpecificEngines`  
 [in] Il numero di debug motori del `rgguidSpecificEngines` matrice e la dimensione del `rghrEngineAttach` matrice.  
  
 `rghrEngineAttach`  
 [in, out] Matrice di codici HRESULT restituito dai motori di debug. Le dimensioni di questa matrice sono incluso il `celtSpecificEngines` parametro. Ogni codice è in genere `S_OK` o `S_ATTACH_DEFERRED`. Quest'ultimo indica che la Germania è attualmente collegato a nessun programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. La tabella seguente illustra gli altri valori possibili.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il processo specificato è già collegato al debugger.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione di sicurezza durante la procedura di collegamento.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processo desktop non è possibile collegare il debugger.|  
  
## <a name="remarks"></a>Note  
 Connessione a un processo Allega il SDM tutti i programmi in esecuzione in tale processo di debug può essere eseguito dai motori di debug (DE) specificati nella `rgguidSpecificEngines` matrice. Impostare il `rgguidSpecificEngines` parametro a un valore null valore o includere `GUID_NULL` nella matrice da collegare tutti i programmi del processo.  
  
 Tutti gli eventi di debug che si verificano nel processo vengono inviati per il dato [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto. Questo `IDebugEventCallback2` oggetto viene fornito quando il SDM chiama questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)