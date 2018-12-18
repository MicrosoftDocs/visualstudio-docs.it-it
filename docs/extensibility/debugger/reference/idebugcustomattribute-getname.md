---
title: IDebugCustomAttribute::GetName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a33b4507cb54095a38671eaf310d87dae180be6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ottiene il nome dell'attributo personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bstrName`  
 [out] Restituisce una stringa contenente il nome dell'attributo personalizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'oggetto denominato restituito da questo metodo corrisponde al nome della classe utilizzata per dichiarare l'attributo. Questo potrebbe corrispondono esattamente al nome della classe dell'attributo personalizzato, come il suffisso "Attribute" da eliminare da un nome di attributo personalizzato quando viene utilizzata in una dichiarazione di c#.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)