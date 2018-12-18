---
title: IDebugObject::GetValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetValue
helpviewer_keywords: IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c96a9224d77f8693226b4474bfed2893b39e27f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ottiene il valore dell'oggetto come una serie di byte consecutiva.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pValue`  
 [in, out] Matrice che viene compilata con una serie di byte che rappresenta il valore dell'oggetto consecutiva.  
  
 `nSize`  
 [in] Numero massimo di byte da recuperare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ottenere il numero totale di byte di valore che possono essere recuperati chiamando il [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)