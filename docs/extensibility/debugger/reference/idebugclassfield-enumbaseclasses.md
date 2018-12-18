---
title: IDebugClassField::EnumBaseClasses | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumBaseClasses
helpviewer_keywords: IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3f62f570b489427b59aefe8153692ab8f9fc2181
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crea un enumeratore per le classi di base di questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco delle classi base. Restituisce un valore null se esistono classi base.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK, restituisce S_SH_NO_BASE_CLASSES se esistono classi base (e `ppEnum` parametro è impostato su un valore null); in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le classi di base dell'oggetto enumeratore vengono specificate nell'ordine della classe base in questione (o più derivata) alla classe di base più remota. Ad esempio, poiché le classi C++:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 Enumerazione restituisce le classi di base nell'ordine `Level2`, `Level1`, `Root`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)