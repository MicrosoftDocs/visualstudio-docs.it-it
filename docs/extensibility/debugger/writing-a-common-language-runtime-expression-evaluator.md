---
title: Scrittura di un analizzatore di espressioni di Common Language Runtime | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ff2189bd80d2c5bbbc5253763e2ba07ef917d19
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Scrittura di un analizzatore di espressioni di Common Language Runtime
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni (Java EE) è la parte di un motore di debug (DE) che gestisce la sintassi e semantica del linguaggio di programmazione che ha generato il codice sottoposto a debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcune lingue, ad esempio, l'espressione "A + B", "la somma di A e b." In altri linguaggi, la stessa espressione potrebbe indicare "A o B." Di conseguenza, un oggetto separato EE deve essere scritto per ogni linguaggio di programmazione che genera il codice oggetto per il debug nell'IDE di Visual Studio.  
  
 Alcuni aspetti del debug pacchetto Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando si interrompe esecuzione in un punto di interruzione, tutte le espressioni che l'utente ha digitato in un **espressioni di controllo** finestra deve essere valutata e deve essere visualizzata. Inoltre, l'utente può modificare il valore di una variabile locale, digitare un'espressione in un **espressioni di controllo** finestra o nel **immediato** finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Common Language Runtime e valutazione delle espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Viene illustrato che quando si integra il linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un EE in grado di valutazione di espressioni all'interno del contesto del linguaggio proprietaria consente di compilare in Microsoft intermediate language (MSIL) senza scrivere un motore di debug.  
  
 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Viene illustrato come implementare le interfacce EE necessarie e chiamare il provider di simbolo di common language runtime (SP) e interfacce dello strumento di associazione.  
  
 [Registrazione di un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Indica che l'analizzatore di Espressioni deve registrarsi come una class factory con il common language runtime e di ambienti di runtime di Visual Studio.  
  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Viene descritto come il processo di valutazione di un'espressione include il motore di debug (DE), il provider di simboli (SP), l'oggetto di gestore di associazione e l'analizzatore di espressioni (Java EE).  
  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)  
 Viene descritto come, quando viene sospesa l'esecuzione, il pacchetto di debug chiama la Germania per ottenere un elenco di argomenti e variabili locali.  
  
 [Valutazione di un'espressione della finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Illustra come il pacchetto di debug di Visual Studio chiama la Germania per determinare il valore corrente di ogni espressione nell'elenco di espressioni di controllo.  
  
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Viene illustrato come modificare il valore di una variabile locale, ogni riga della finestra variabili locali è associato un oggetto che fornisce il nome, tipo e il valore corrente di una variabile locale.  
  
 [Implementazione di visualizzatori di tipi e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Illustra l'interfaccia che deve essere implementata da un componente che per supportare i visualizzatori di tipo e i visualizzatori personalizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)