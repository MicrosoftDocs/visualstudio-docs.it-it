---
title: Implementazione di variabili locali di esempio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d4a500f2d66fdab239f5d10fb5d8b4ff4212a36
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446279"
---
# <a name="sample-implementation-of-locals"></a>Implementazione di esempio di variabili locali
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito viene fornita una panoramica del modo in cui Visual Studio Ottiene le variabili locali per un metodo dall'analizzatore di espressioni (EE):  
  
1. Visual Studio chiama il motore di debug (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta tutte le proprietà del frame dello stack, incluse le variabili locali.  
  
2. `IDebugStackFrame2::GetDebugProperty` le chiamate [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere un oggetto che descrive il metodo all'interno del quale si è verificato il punto di interruzione. La Germania fornisce un provider di simboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), un indirizzo ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e uno strumento di associazione ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` le chiamate [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con il parametro fornito `IDebugAddress` oggetto per cui ottenere un' [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo che contiene l'indirizzo specificato.  
  
4. Il `IDebugContainerField` viene eseguita una query di interfaccia per il [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaccia. È questa interfaccia che consente di accedere a variabili locali del metodo.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` Crea un'istanza di una classe (chiamati `CFieldProperty` nell'esempio) che implementa il `IDebugProperty2` interfaccia per rappresentare variabili locali del metodo. Il `IDebugMethodField` oggetto viene inserito in questa `CFieldProperty` dell'oggetto con il `IDebugSymbolProvider`, `IDebugAddress` e `IDebugBinder` oggetti.  
  
6. Quando la `CFieldProperty` viene inizializzato, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) viene chiamato sul `IDebugMethodField` oggetto da cui ottenere un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) struttura che contiene tutte le informazioni visualizzabile sul metodo di stesso .  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Restituisce il `CFieldProperty` dell'oggetto come un `IDebugProperty2` oggetto.  
  
8. Le chiamate di Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sull'oggetto restituito `IDebugProperty2` oggetto con il filtro `guidFilterLocalsPlusArgs`. Restituisce un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente variabili locali del metodo. Questa enumerazione viene compilata tramite chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Le chiamate di Visual Studio [successivo](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura per ogni locale. Questa struttura contiene un puntatore a un `IDebugProperty2` interfaccia per una variabile locale.  
  
10. Le chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni locale ottenere nome, valore e tipo di oggetto locale. Si tratta delle informazioni che viene visualizzate nei **variabili locali** finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Viene descritta un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerazione di variabili locali](../../extensibility/debugger/enumerating-locals.md)  
 Viene descritto come il motore di debug (DE) effettua una chiamata per enumerare le variabili locali o argomenti.  
  
 [Recupero delle proprietà locali](../../extensibility/debugger/getting-local-properties.md)  
 Viene descritto come la Germania effettua una chiamata per ottenere il nome, tipo e valore di uno o più variabili locali.  
  
 [Recupero dei valori locali](../../extensibility/debugger/getting-local-values.md)  
 Viene illustrato come ottenere il valore della variabile locale, che richiede i servizi di un oggetto strumento di associazione fornito dal contesto di valutazione.  
  
 [Valutazione di variabili locali](../../extensibility/debugger/evaluating-locals.md)  
 Illustra le modalità di valutazione delle variabili locali.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati durante la Germania chiama l'analizzatore di espressioni (EE).  
  
 [Esempio MyCEE](http://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Viene illustrato un approccio di implementazione per la creazione di un analizzatore di espressioni per il linguaggio MyC.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
