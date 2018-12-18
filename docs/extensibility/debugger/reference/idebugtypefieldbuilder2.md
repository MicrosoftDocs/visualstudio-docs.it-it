---
title: IDebugTypeFieldBuilder2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4500f8e44a3008655d9a4068b96ce2cfcdbc2ac5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Estende il **IDebugTypeFieldBuilder** per essere in grado di creare tipi di matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia può essere ottenuta dal provider di simboli.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matrice del tipo specificato e dimensioni.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll