---
title: 'Metodo ijsdebugdatatarget:: GetTLSValue | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Metodo IJsDebugDataTarget::GetTlsValue
Per il thread è in corso il debug, recupera il valore nello slot (TLS) di archiviazione locale di thread per l'indice specificato di TLS.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 [in] Thread in esecuzione nel processo di destinazione da cui leggere.  
  
 `tlsIndex`  
 [in] L'indice TLS è stata allocata quando il processo di destinazione chiamata alla funzione TlsAlloc.  
  
 `pValue`  
 [out] Il valore della dimensione del puntatore che è stato archiviato in uno slot TLS del thread. Se il thread di destinazione è a 32 bit, 32-bit superiori di questo valore sarà zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Ogni thread di un processo ha un proprio slot per ogni indice TLS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)