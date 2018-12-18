---
title: IDebugGenericParamField | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4072908a8f6690e3d3b00d8c43690be62083242d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Rappresenta un parametro per un tipo generico di codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Usato per il supporto dei generics.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Restituisce il numero di vincoli che sono associati a questo parametro generico.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera i vincoli che sono associati a questo parametro generico.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera i flag per il parametro generico.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera l'indice del parametro generico.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera il nome del parametro generico.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera il proprietario del tipo o metodo di questo parametro generico.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll