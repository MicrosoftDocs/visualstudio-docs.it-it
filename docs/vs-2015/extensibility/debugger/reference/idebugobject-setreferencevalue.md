---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51770bf8b57877450917933af2f5382205aa60fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540913"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugObject::SetReferenceValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-setreferencevalue).  
  
Imposta il valore di riferimento di questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pObject`  
 [in] Un' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta il nuovo valore di riferimento.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo rende questa [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) sul valore dell'oggetto specificato in un riferimento a un oggetto di `pObject` parametro, generando un'eccezione qualsiasi riferimento precedente. Si noti che questo `IDebugObject` oggetto deve essere già un tipo di riferimento.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

