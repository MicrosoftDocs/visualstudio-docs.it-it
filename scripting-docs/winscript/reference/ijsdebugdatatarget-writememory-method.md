---
title: 'Metodo ijsdebugdatatarget:: WriteMemory | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Metodo IJsDebugDataTarget::WriteMemory
Legge la memoria del processo di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo di base da cui scrivere la memoria del processo di destinazione.  
  
 `pMemory`  
 [in] I dati da scrivere nello spazio degli indirizzi del processo specificato.  
  
 `size`  
 [in] Il numero di byte da scrivere nel processo.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Prima che si verifichi il trasferimento dei dati, il sistema verifica che tutti i dati in cui l'indirizzo di base e la memoria della dimensione specificata è accessibile in scrittura e, se non è accessibile, la funzione genera un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)