---
title: IEnumCodePaths2::Next | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2::Next
helpviewer_keywords: IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a018e033d9e342697cd1e06d1ef9ad8a53e4036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
Restituisce il set successivo di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) elementi da compilare.  
  
 `pceltFetched`  
 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se può essere inferiore al numero di elementi richiesto sia restituiti; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)