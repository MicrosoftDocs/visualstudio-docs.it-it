---
title: IDebugDocumentText::GetPositionOfLine | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfLine
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0098a78938c745931c529bbc02823d32b8180cde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
Restituisce la posizione di carattere corrispondente al primo carattere di una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cLineNumber`  
 [in] Numero di riga.  
  
 `pcCharacterPosition`  
 [out] Posizione del carattere all'interno del documento dell'inizio della riga `cLineNumber`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce la posizione del carattere corrispondente al primo carattere di una riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)