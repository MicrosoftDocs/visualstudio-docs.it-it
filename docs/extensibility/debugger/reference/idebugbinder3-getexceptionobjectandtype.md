---
title: IDebugBinder3::GetExceptionObjectAndType | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 519281487e85ec7dffc0e7bb470d044dc2bae885
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Questo metodo recupera l'eccezione associata a un oggetto, se presente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppException`  
 [out] Restituisce l'oggetto che rappresenta l'eccezione.  
  
 `ppField`  
 [out] Restituisce l'oggetto che rappresenta un campo specifico che potrebbe aver causato l'eccezione (potrebbe essere un valore null).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Per verificare se si verifica un'eccezione, controllare il valore restituito da `ppException`: se si tratta di un valore null, sarà associata a questo oggetto alcuna eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)