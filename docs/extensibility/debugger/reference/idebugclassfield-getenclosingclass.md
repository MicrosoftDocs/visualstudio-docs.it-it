---
title: IDebugClassField::GetEnclosingClass | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetEnclosingClass
helpviewer_keywords: IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 440b9845ae7f3dd57b34b4ce25f48bea3aaa7e80
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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