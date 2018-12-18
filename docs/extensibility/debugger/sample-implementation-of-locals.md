---
title: Implementazione di variabili locali di esempio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3e8157d6ecede516ca1dcb2900cf081c11a2b790
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sample-implementation-of-locals"></a>Esempio di implementazione di variabili locali
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito viene fornita una panoramica di come Visual Studio Ottiene le variabili locali per un metodo dall'analizzatore di espressioni (Java EE):  
  
1.  Visual Studio chiama il motore di debug (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta tutte le proprietà del frame dello stack, incluse le variabili locali.  
  
2.  `IDebugStackFrame2::GetDebugProperty`chiamate [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere un oggetto che descrive il metodo all'interno del quale si è verificato il punto di interruzione. La Germania fornisce un provider di simboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), un indirizzo ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e uno strumento di associazione ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`chiamate [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con fornito `IDebugAddress` oggetto da ottenere un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo che contiene l'indirizzo specificato.  
  
4.  Il `IDebugContainerField` interfaccia viene eseguita una query per il [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaccia. È questa interfaccia che fornisce accesso a variabili locali del metodo.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`Crea un'istanza di una classe (chiamato `CFieldProperty` nell'esempio) che implementa il `IDebugProperty2` rappresentano variabili locali del metodo di interfaccia. Il `IDebugMethodField` oggetto viene posizionato in questo `CFieldProperty` dell'oggetto con il `IDebugSymbolProvider`, `IDebugAddress` e `IDebugBinder` oggetti.  
  
6.  Quando il `CFieldProperty` oggetto viene inizializzato, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) viene chiamato sul `IDebugMethodField` per ottenere un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) struttura che contiene tutte le informazioni sul metodo stesso visualizzabile .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`Restituisce il `CFieldProperty` oggetto come un `IDebugProperty2` oggetto.  
  
8.  Chiamate di Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sull'oggetto restituito `IDebugProperty2` oggetto con il filtro `guidFilterLocalsPlusArgs`. Restituisce un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente variabili locali del metodo. Questa enumerazione viene compilata tramite chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Chiamate di Visual Studio [Avanti](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura per ogni locale. Questa struttura contiene un puntatore a un `IDebugProperty2` interfaccia per una variabile locale.  
  
10. Chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni locale ottenere nome, valore e tipo di oggetto locale. Si tratta delle informazioni visualizzate nel **variabili locali** finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Viene descritta un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerazione di variabili locali](../../extensibility/debugger/enumerating-locals.md)  
 Viene descritto come il motore di debug (DE) effettua una chiamata per enumerare le variabili locali o argomenti.  
  
 [Recupero delle proprietà locali](../../extensibility/debugger/getting-local-properties.md)  
 Viene descritto come la Germania effettua una chiamata per ottenere il nome, tipo e valore di uno o più variabili locali.  
  
 [Recupero dei valori locali](../../extensibility/debugger/getting-local-values.md)  
 Viene illustrato come ottenere il valore della variabile locale, che richiede i servizi di un oggetto gestore di associazione fornito dal contesto di valutazione.  
  
 [Valutazione di variabili locali](../../extensibility/debugger/evaluating-locals.md)  
 Illustra le modalità di valutazione delle variabili locali.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati quando la Germania chiama l'analizzatore di espressioni (Java EE).  
  
 [Esempio MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Viene illustrato un approccio di implementazione per la creazione di un analizzatore di espressioni per la lingua MyC.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)