---
title: IEnumDebugReferenceInfo2::GetCount | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugReferenceInfo2::GetCount
helpviewer_keywords:
- IEnumDebugReferenceInfo2::GetCount
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bdbbc5bf50f395ab988fd0c2d5b97786333afca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugreferenceinfo2getcount"></a>IEnumDebugReferenceInfo2::GetCount
Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è solitamente si interfaccia COM di enumerazione che specifica che solo il `Next`, `Clone`, `Skip`, e `Reset` metodi devono essere implementate.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)