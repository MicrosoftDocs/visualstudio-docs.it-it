---
title: Implementazione di un analizzatore di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f18e2e131b6baa325bd7e0b65babee4c3679ed8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-an-expression-evaluator"></a>Implementazione di un analizzatore di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Valutazione di un'espressione è un'interazione complessa tra il motore di debug (DE), il provider di simboli (SP), l'oggetto di gestore di associazione e l'analizzatore di espressioni (Java EE) se stesso. I quattro componenti sono connessi tramite le interfacce che vengono implementate da un componente e utilizzate da un altro.  
  
 L'analizzatore di Espressioni accetta un'espressione da DE sotto forma di stringa e analizza o valuta. L'analizzatore di Espressioni implementa le interfacce seguenti, che vengono usate per la Germania:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 L'analizzatore di Espressioni chiama l'oggetto di gestore di associazione, fornito per la Germania, per ottenere il valore di simboli e oggetti. L'analizzatore di Espressioni utilizza le interfacce seguenti, che vengono implementate per la Germania:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementa l'analizzatore di Espressioni [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fornisce il meccanismo per la descrizione del risultato della valutazione di un'espressione, ad esempio una variabile locale, una primitiva o un oggetto, a Visual Studio, che consente di visualizzare le informazioni appropriate nella **variabili locali**,  **Espressioni di controllo**, o **immediato** finestra.  
  
 Stored procedure viene fornito l'analizzatore di Espressioni per la Germania quando vengono richieste informazioni. SP implementa interfacce che descrivono gli indirizzi e campi, ad esempio le seguenti interfacce e i relativi derivati:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 L'analizzatore di Espressioni utilizza tutte queste interfacce.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Strategia di implementazione di un analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definisce un processo a tre passaggi per la strategia di implementazione di espressione dell'analizzatore di espressioni (Java EE).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)