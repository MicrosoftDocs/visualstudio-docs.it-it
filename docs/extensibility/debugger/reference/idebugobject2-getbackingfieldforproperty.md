---
title: IDebugObject2::GetBackingFieldForProperty | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords: IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f8833e3d2b686e1c350e1094aaa9bdfe925586a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o una variabile (se presente) che può essere supporto della proprietà rappresentata dall'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto che descrive il campo sottostante.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto rappresenta una proprietà di classe di codice gestito, vale a dire un metodo con una richiesta get e/o funzione di accesso set. Tali proprietà in genere richiedono una variabile per contenere il valore modificato dalla proprietà. Questa variabile è noto come il campo sottostante. Se è presente alcun campo sottostante per l'oggetto, quindi verificare che restituisca un valore null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma invece risulterà per vedere se è stato restituito un valore null in `ppObject`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)