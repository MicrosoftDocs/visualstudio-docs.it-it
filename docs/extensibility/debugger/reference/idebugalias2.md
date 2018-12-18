---
title: IDebugAlias2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15fbf639c15e62b19e112ad140517f096d49f9d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni (Java EE) per ottenere il dominio applicazione per l'alias.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dal motore di debug gestito (DE).  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera l'identificatore per il dominio applicazione.|  
  
## <a name="remarks"></a>Note  
 Un alias è un numero decimale in formato stringa seguita dal carattere #, ad esempio, 1001#.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll