---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9250467aeec5a032c8e88054d868aa45ae7dda0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Costruisce un'istanza del campo Data una matrice di argomenti di tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cArgs`  
 [in] Numero di argomenti in di `ppArgs` matrice.  
  
 `ppArgs`  
 [in] Matrice che contiene gli argomenti di tipo. Gli argomenti di tipo devono essere tipi chiusi (generics non generico o istanziato completa).  
  
 `ppConstructedField`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia che rappresenta il nuovo campo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Vincoli non vengono controllati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)