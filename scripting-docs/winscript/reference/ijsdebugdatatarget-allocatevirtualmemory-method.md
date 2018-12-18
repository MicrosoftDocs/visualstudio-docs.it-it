---
title: 'Metodo ijsdebugdatatarget:: Allocatevirtualmemory | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Metodo IJsDebugDataTarget::AllocateVirtualMemory
Riserva e/o viene eseguito il commit di un'area di memoria all'interno di spazio degli indirizzi virtuali del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo all'interno del processo di destinazione in cui la memoria deve essere eseguito il commit oppure sono riservata. In genere, questo valore è zero, in cui il sistema sceglie un indirizzo.  
  
 `size`  
 [in] Le dimensioni dell'area di memoria da allocare, in byte. Il sistema verrà automaticamente arrotondare per eccesso ai limiti della pagina successiva.  
  
 `allocationType`  
 [in] Indica il tipo di allocazione da eseguire. Si tratta in genere MEM_COMMIT &#124; MEM_RESERVE (0x3000) che si riserva ed esegue il commit di un'allocazione in un unico passaggio.  
  
 `pageProtection`  
 [in] La protezione della memoria per l'area delle pagine da allocare. Se il commit di pagine, è possibile specificare una delle costanti di protezione della memoria (ad esempio, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Indirizzo di base della regione allocata di pagine.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 La funzione inizializza la memoria che allocata a zero, a meno che non viene utilizzato MEM_RESET. Per ulteriori informazioni, vedere l'API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)