---
title: Modifica del valore di una variabile locale | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-value-of-a-local"></a>Modifica del valore di una variabile locale
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando un nuovo valore sia stato digitato nel campo del valore di **variabili locali** finestra, il pacchetto di debug passa la stringa, durante la digitazione, per l'analizzatore di espressioni (Java EE). L'analizzatore di Espressioni valuta questa stringa, che può contenere un semplice valore o un'espressione e archivia il valore risultante in locale associato.  
  
 Questa è una panoramica del processo di modifica del valore di una variabile locale:  
  
1.  Dopo aver inserito il nuovo valore, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sul [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto associato all'oggetto locale.  
  
2.  `IDebugProperty2::SetValueAsString` esegue le attività seguenti:  
  
    1.  Restituisce la stringa per produrre un valore.  
  
    2.  Associa l'oggetto associato [IDebugField](../../extensibility/debugger/reference/idebugfield.md) per ottenere un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
    3.  Converte il valore in una serie di byte.  
  
    4.  Chiamate [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) per inserire i byte del valore in memoria in modo che il programma in fase di debug può accedervi.  
  
3.  Visual Studio aggiorna il **variabili locali** visualizzare (vedere [visualizzazione variabili locali](../../extensibility/debugger/displaying-locals.md) per informazioni dettagliate).  
  
 Questa procedura viene utilizzata anche per modificare il valore di una variabile nel **espressioni di controllo** finestra ma il `IDebugProperty2` oggetto associato al valore della variabile locale che viene usata invece del `IDebugProperty2` oggetto associato a locale se stesso.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Utilizza l'esempio MyCEE per scorrere il processo di modifica dei valori.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)