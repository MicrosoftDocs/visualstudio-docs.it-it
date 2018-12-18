---
title: IDebugSymbolProviderDirect::GetMetaDataImport | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9abccf11d514a998cd19aef8e9f5e8417b544c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
Recupera le informazioni di importazione dei metadati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```csharp  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guid`  
 [in] Identificatore univoco per il modulo.  
  
 `appID`  
 [in] Identificatore per il dominio applicazione.  
  
 `ppImport`  
 [out] Restituisce un oggetto che contiene i metadati di importare le informazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)