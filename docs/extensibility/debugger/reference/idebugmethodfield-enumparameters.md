---
title: IDebugMethodField::EnumParameters | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112b91c2155c28b37b2222a99a45893fcb56e98c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crea un enumeratore per i parametri del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParams`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) l'oggetto che rappresenta l'elenco di parametri al metodo; in caso contrario, restituisce un valore null se non sono presenti parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti parametri. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta diversi tipi di parametri. Chiamare il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) su ogni oggetto per determinare esattamente quale tipo di parametro l'oggetto rappresenta.  
  
 Un parametro include sia il nome della variabile e il relativo tipo. Il primo parametro a un metodo di classe è in genere il puntatore "this".  
  
 Se solo i tipi dei parametri è necessaria, chiamare il [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)