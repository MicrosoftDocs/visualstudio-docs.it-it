---
title: IDebugTypeFieldBuilder | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3c14959e0b14b74b31732a7d8611c0ae2d2c699
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Rappresenta la possibilità di creare un campo che rappresenta un tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta dal provider di simboli.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crea un oggetto che rappresenta un tipo primitivo.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crea un puntatore al tipo specificato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll