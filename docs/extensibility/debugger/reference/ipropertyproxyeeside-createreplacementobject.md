---
title: IPropertyProxyEESide::CreateReplacementObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56e5001d7abd498982361a51d0386db4b2624cf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia di un oggetto dati specifico per l'analizzatore di espressioni (Java EE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto che contiene i dati da copiare.  
  
 `dataOut`  
 [out] Restituisce un nuovo `IEEDataStorage` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo riceve un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto che rappresenta una matrice di byte. Questo oggetto dati in entrata non è in genere implementato dal motore di esecuzione. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal motore di esecuzione, che consente di implementare EE il `IEEDataStorage` interfaccia su qualsiasi classe desiderata.  
  
 Si noti che i dati forniti da in ingresso `IEEDataStorage` l'oggetto deve essere gli stessi dati in uscita `IEEDataStorage` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)