---
title: IDebugIDECallback | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 739c419e7f71b325a74c0a7c6dbbc31b1fd0e37f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Consente un analizzatore di espressioni (Java EE) visualizzare un messaggio nella finestra di output del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questo callback viene implementato dal motore di debug gestito.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Che può essere utilizzata da un analizzatore di espressioni per inviare l'output alla finestra di output del debugger.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Invia la stringa di messaggio specificato alla finestra di output del debugger.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll