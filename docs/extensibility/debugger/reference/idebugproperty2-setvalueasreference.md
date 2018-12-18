---
title: IDebugProperty2::SetValueAsReference | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsReference
helpviewer_keywords: IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7bd9e42ae6be1cbd5afe1cbe2ae1b06da7f9937f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Imposta il valore di questa proprietà sul valore del riferimento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rgpArgs`  
 [in] Matrice di argomenti da passare al metodo di impostazione di proprietà di codice gestito. Se il setter di proprietà non accetta argomenti o se questo [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto non fa riferimento a tale impostazione di una proprietà, `rgpArgs` deve essere un valore null. In genere, questo parametro è un valore null.  
  
 `dwArgCount`  
 [in] Il numero di argomenti in di `rgpArgs` matrice.  
  
 `pValue`  
 [in] Un riferimento, sotto forma di un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto, il valore da utilizzare per impostare questa proprietà.  
  
 `dwTimeout`  
 [in] Il tempo da eseguire per impostare il valore, espresso in millisecondi. Un valore tipico è `INFINITE`. Questo problema riguarda il periodo di tempo che può accettare qualsiasi valutazione possibili.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario restituisce un errore del codice, in genere uno dei seguenti:  
  
|Error|Descrizione|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|L'impostazione del valore da un riferimento non è supportata.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Impossibile impostare il valore di questa proprietà fa riferimento a un metodo.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)