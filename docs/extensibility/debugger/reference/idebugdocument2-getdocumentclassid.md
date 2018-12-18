---
title: IDebugDocument2::GetDocumentClassID | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79a80d5a37c341a46d32e9bedac8f7ff416158da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Ottiene l'identificatore di classe del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pclsid`  
 [out] Restituisce un GUID che rappresenta l'ID di classe del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il GUID della classe può essere utilizzato per creare le singole classi ognuno dei quali rappresenta un documento.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)