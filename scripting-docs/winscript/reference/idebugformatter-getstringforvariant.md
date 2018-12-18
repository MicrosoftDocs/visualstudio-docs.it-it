---
title: IDebugFormatter::GetStringForVariant | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfc31b0fdbf6d1f4a29b1322dc3a3c4015f9c8ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Restituisce una stringa che rappresenta il valore di variante specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvar`  
 [in] VARIANTE per essere rappresentato come una stringa.  
  
 `nRadix`  
 [in] Radice da utilizzare per i valori numerici.  
  
 `pbstrValue`  
 [out] Stringa che rappresenta `pvar`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una stringa che rappresenta il valore di tipo variant specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)