---
title: IDebugDynamicFieldCOMPlus | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15773a1133721996f95f29c8ab035f18f401cbeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Rappresenta un campo dinamico per una [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo dato il relativo tipo primitivo.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo di dato il relativo token.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll