---
title: 'Metodo ijsdebugdatatarget:: FreeVirtualMemory | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Metodo IJsDebugDataTarget::FreeVirtualMemory
Rilascia e/o libera un'area di memoria all'interno di spazio degli indirizzi virtuali del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] Indirizzo all'interno del processo di destinazione in cui deve essere liberata la memoria.  
  
 `size`  
 [in] Numero di byte da liberare. Per rilasciare un'area di memoria, questo valore deve essere zero.  
  
 `freeType`  
 [in] Indica il tipo di operazione libero da eseguire. Si tratta in genere MEM_RELEASE (0x8000), che quale rilascia l'area delle pagine specificato. Al termine dell'operazione, le pagine sono in stato libero. MEM_DECOMMIT (0x4000) è invece consente di liberare le pagine senza rilasciarlo.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere l'API Win32 VirtualFree.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)