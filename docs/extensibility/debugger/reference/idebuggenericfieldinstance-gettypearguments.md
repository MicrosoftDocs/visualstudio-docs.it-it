---
title: IDebugGenericFieldInstance::GetTypeArguments | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0521405cfd9991ca0de72690e7b50ca22baaa67e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
Recupera gli argomenti di parametro di tipo per questa istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cArgs`  
 [in] Numero di parametri di tipo.  
  
 `ppArgs`  
 [out] Restituisce una matrice di parametri di tipo.  
  
 `pcArgs`  
 [in, out] Numero di membri di `ppArgs` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)