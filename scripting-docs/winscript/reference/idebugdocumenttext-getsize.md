---
title: IDebugDocumentText::GetSize | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3152150c46793a71ec7a46b6ab2097efa06f6fc8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Restituisce il numero di righe e numero di caratteri nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcNumLines`  
 [out] Numero di righe del documento. Se questo parametro è NULL, il metodo non restituisce un valore.  
  
 `pcNumChars`  
 [out] Numero di caratteri nel documento. Se questo parametro è NULL, il metodo non restituisce un valore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il numero di righe e numero di caratteri nel documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)