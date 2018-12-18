---
title: Strategia di implementazione dell'analizzatore di espressioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia di implementazione dell'analizzatore di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Uno degli approcci disponibili per creare rapidamente un analizzatore di espressioni (Java EE) consiste nell'implementare prima di tutto il codice minimo necessario per visualizzare le variabili locali nel **variabili locali** finestra. È utile tenere presente che ogni riga di **variabili locali** finestra vengono visualizzati nome, tipo e il valore di una variabile locale e che tutti e tre sono rappresentati da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto. Nome, tipo e il valore di una variabile locale può essere ottenuti da un `IDebugProperty2` oggetto chiamando il relativo [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo. Per ulteriori informazioni su come visualizzare le variabili locali nel **variabili locali** finestra, vedere [visualizzazione variabili locali](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussione  
 Una possibile implementazione che inizia con implementazione [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Il [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodi devono essere implementati per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` restituisce un `IDebugProperty2` oggetto che rappresenta un metodo:, ovvero un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) oggetto. Metodi non vengono visualizzati di **variabili locali** finestra.  
  
 Il [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo deve essere implementato successivamente. Il motore di debug (DE) chiama questo metodo per ottenere un elenco di argomenti e variabili locali passando `IDebugProperty2::EnumChildren` un `guidFilter` argomento di `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` le chiamate [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando i risultati in un'unica enumerazione. Vedere [visualizzazione variabili locali](../../extensibility/debugger/displaying-locals.md) per altri dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)