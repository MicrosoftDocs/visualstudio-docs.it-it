---
title: IDebugProperty2::SetValueAsString | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5fb55fb6f9a90cf39120be408428524f64463d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Imposta il valore di una proprietà da una stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Stringa contenente il valore da impostare.  
  
 `nRadix`  
 [in] Radice da utilizzare per interpretare le informazioni numeriche. Può essere 0 per tentare di determinare automaticamente la radice.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, in millisecondi di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. La tabella seguente illustra gli altri valori possibili.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La stringa non può essere convertita in un valore di proprietà oppure non è stato possibile impostare il valore della proprietà.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La proprietà è in sola lettura.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)