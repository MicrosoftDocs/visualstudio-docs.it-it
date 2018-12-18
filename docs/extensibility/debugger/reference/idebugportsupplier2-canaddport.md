---
title: IDebugPortSupplier2::CanAddPort | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00b1c1303be8ccc326a58a20d132ad38db3b426d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifica che un fornitore di porta è possibile aggiungere nuove porte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se è possibile aggiungere la porta, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` per indicare le porte non possono essere aggiunto al fornitore porta.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo prima di chiamare il [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metodo poiché quest'ultimo metodo crea la porta come aggiungerlo, che può essere un'operazione richiede molto tempo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)