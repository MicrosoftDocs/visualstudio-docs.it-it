---
title: IDebugField::GetTypeInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetTypeInfo
helpviewer_keywords: IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f1ec3adf1f71d5d7f7e916b261555ca8aeb9d31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Questo metodo ottiene il simbolo o un tipo indipendente dal tipo di informazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pTypeInfo`  
 [out] Restituisce informazioni sul tipo nella classe fornita [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struttura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Indipendente dal tipo di informazioni dovrebbe includere, ad esempio, il dominio applicazione, il modulo e la classe che contiene il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)