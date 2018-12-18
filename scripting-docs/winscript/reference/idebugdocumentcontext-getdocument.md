---
title: IDebugDocumentContext::GetDocument | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentContext.GetDocument
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776a65ca9adbcf9304e57e0b93f4ebcb4a33bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
Restituisce il documento che contiene questo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppsd`  
 [out] Il documento che contiene questo contesto.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `GetDocument` metodo restituisce il documento che contiene questo contesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)