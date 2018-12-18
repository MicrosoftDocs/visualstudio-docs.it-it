---
title: IDebugEngine2::SetMetric | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12e323fe248bc022bcbbd8b9bdd0e628c27a97e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Questo metodo imposta un valore del Registro di sistema denominato una metrica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszMetric`  
 [in] Il nome della metrica.  
  
 `varValue`  
 [in] Specifica il valore della metrica.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una metrica è un valore del Registro di sistema utilizzato per modificare il comportamento del motore di debug o per annunciare le funzionalità supportate. Questo metodo può inoltrare la chiamata al modulo appropriato del [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funzione `SetMetric`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)