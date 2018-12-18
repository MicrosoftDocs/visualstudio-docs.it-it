---
title: IDebugDocumentText::GetDocumentAttributes | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetDocumentAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetDocumentAttributes
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3121538612be48628b24965e118130875c51a0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetdocumentattributes"></a>IDebugDocumentText::GetDocumentAttributes
Restituisce gli attributi del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ptextdocattr`  
 [out] Gli attributi di testo del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce gli attributi del documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Costanti TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)