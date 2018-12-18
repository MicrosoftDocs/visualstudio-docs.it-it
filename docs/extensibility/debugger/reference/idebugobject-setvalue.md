---
title: IDebugObject::SetValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::SetValue
helpviewer_keywords: IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: adb5987e8537938c5d6f6c6241cd466654bf4793
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Imposta il valore dell'oggetto da una serie di byte consecutiva.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pValue`  
 [in] Matrice di byte che rappresenta il nuovo valore.  
  
 `nSize`  
 [in] Le dimensioni del valore in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I valori nella matrice vengono copiati in questa [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto, sostituendo i valori esistenti. Le dimensioni del nuovo valore possono essere maggiore o minore del valore esistente. Questo `IDebugObject` non può essere un riferimento null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)