---
title: IDebugPointerObject3 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fe58df189ebfbc8519d45fab1011b691f50d2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta un puntatore in un albero di analisi ed estende il **IDebugPointerObject** interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata un analizzatore di espressioni (Java EE).  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Recupera l'indirizzo del puntatore.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll