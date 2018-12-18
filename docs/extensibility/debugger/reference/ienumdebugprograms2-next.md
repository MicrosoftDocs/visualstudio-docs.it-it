---
title: IEnumDebugPrograms2::Next | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPrograms2::Next
helpviewer_keywords: IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c90fa359d37d59171e59e7853e2c1c38cdd46dd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
Restituisce il set successivo di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Next(  
   ULONG            celt,  
   IDebugProgram2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint             celt,  
   IDebugProgram2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) elementi da compilare.  
  
 `pceltFetched`  
 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se può essere inferiore al numero di elementi richiesto sia restituiti; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)