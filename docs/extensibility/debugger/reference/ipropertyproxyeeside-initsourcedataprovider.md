---
title: IPropertyProxyEESide::InitSourceDataProvider | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6ae2716fc76d77d1c670bb206168826c66c48ed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inizializza i dati di origine per questo oggetto e restituisce un oggetto contenente i dati iniziali.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataOut`  
 [out] Restituisce un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo esegue tutte le operazioni necessarie per inizializzare un oggetto in modo che può restituire un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfaccia sui dati dell'oggetto. In questo modo i dati dell'oggetto essere visualizzate e, se consentito, modificato da un visualizzatore di tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)