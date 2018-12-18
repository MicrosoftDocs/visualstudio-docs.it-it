---
title: IDebugDocumentHelper::GetDebugApplicationNode | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetDebugApplicationNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetDebugApplicationNode
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27d1fb09698cffa4826ab35b36e3ae315a12ba74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpergetdebugapplicationnode"></a>IDebugDocumentHelper::GetDebugApplicationNode
Restituisce il nodo debug dell'applicazione corrispondente a questo documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppdan`  
 [out] Il nodo debug dell'applicazione corrispondente a questo documento.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Restituisce il nodo debug dell'applicazione corrispondente a questo documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)