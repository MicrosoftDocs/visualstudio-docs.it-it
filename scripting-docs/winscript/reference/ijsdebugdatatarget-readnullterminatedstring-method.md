---
title: 'Metodo ijsdebugdatatarget:: Readnullterminatedstring | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Metodo IJsDebugDataTarget::ReadNullTerminatedString
Legge il numero specificato di caratteri dalla destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [in] L'indirizzo da cui leggere.  
  
 `characterSize`  
 [in] dimensione di ogni carattere nella stringa  
  
 `maxCharacters`  
 [in] Numero massimo di caratteri da leggere. maxCharacters dovrebbe essere ragionevole. Qualsiasi richiesta per più di 128MB di memoria avrà esito negativo.  Se la stringa è maggiore di maxCharacters, la stringa di risultato verrà troncata dopo maxCharacters.  
  
 `pString`  
 [out] La stringa BSTR leggere dalla destinazione.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_FALSE se non viene troncato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)