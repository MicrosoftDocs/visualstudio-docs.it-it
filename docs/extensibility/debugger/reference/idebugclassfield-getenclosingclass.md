---
title: IDebugClassField::GetEnclosingClass | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd73955835f8aff0047995a690da03e5ab0305d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ottiene la classe che include questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppClassField`  
 [out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) classe di oggetto che rappresenta il tipo di inclusione. Restituisce un valore null se nessuna classe del contenitore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se la classe è rappresentato da questo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto è una classe annidata, la `ppClassField` parametro restituisce un `IDebugClassField` classe di oggetto che rappresenta il tipo di inclusione. Ad esempio, poiché la definizione di classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 La chiamata di `GetEnclosingClass` metodo il `IDebugClassField` oggetto che rappresenta il `NestedClass` classe restituisce un `IDebugClassField` oggetto che rappresenta la classe `RootClass`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)