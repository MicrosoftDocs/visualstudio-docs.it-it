---
title: 'Metodo ijsdebugdatatarget:: ReadMemory | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Metodo IJsDebugDataTarget::ReadMemory
Legge la memoria del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo di base da cui leggere la memoria del processo di destinazione.  
  
 `flags`  
 [in] Flag che controllano il comportamento di ReadMemory.  
  
 `pBuffer`  
 [out] Un buffer che riceve il contenuto dallo spazio degli indirizzi del processo di destinazione. In caso di errore, il contenuto del buffer non è specificato.  
  
 `size`  
 [in] Il numero di byte da leggere dal processo.  
  
 `pBytesRead`  
 [out] Indica il numero di byte letti dal processo di destinazione. Se JsDebugAllowPartialRead è deselezionata, in caso di esito positivo questo valore sarà sempre esattamente uguale alla dimensione di input. Se viene specificato JsDebugAllowPartialRead, in caso di esito positivo, questo valore sarà maggiore di zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_OK con successo e codici di errore vengono utilizzati per eventuali errori. Restituisce E_JsDEBUG_INVALID_MEMORY_ADDRESS se l'indirizzo non è valido. Per ulteriori informazioni, vedere JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)