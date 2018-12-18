---
title: La visualizzazione delle variabili locali | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8566baec58e2dd95b42be8916b7d48131370e65e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-locals"></a>La visualizzazione delle variabili locali
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Sempre l'esecuzione avviene all'interno del contesto di un metodo, noto anche come metodo contenitore o il metodo corrente. Quando viene sospesa l'esecuzione, Visual Studio chiama il motore di debug (DE) per ottenere un elenco delle variabili locali e gli argomenti, collettivamente denominati variabili locali del metodo. Visual Studio visualizza le variabili locali e i relativi valori nel **variabili locali** finestra.  
  
 Per visualizzare variabili locali, chiama il DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodo appartenente all'analizzatore di Espressioni e fornisce un contesto di valutazione, ovvero, un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto di associazione. Per ulteriori informazioni, vedere [contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.  
  
 Le chiamate DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto, che viene filtrato in modo da restituire soli variabili locali ed enumerata per produrre un elenco di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)strutture. Ogni struttura contiene nome, tipo e il valore di una variabile locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, tipo e valore sono in genere visualizzati insieme in una riga del **variabili locali** finestra.  
  
> [!NOTE]
>  Il **controllo immediato** e **espressioni di controllo** finestre visualizzate anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anziché `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Alcuni esempi di utilizzo di eseguire il processo di implementazione delle variabili locali.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Viene illustrato che quando il motore di debug (DE) chiama l'analizzatore di espressioni (Java EE), passa di tre argomenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)