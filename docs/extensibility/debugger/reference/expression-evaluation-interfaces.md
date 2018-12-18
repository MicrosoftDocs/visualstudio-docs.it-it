---
title: Interfacce di valutazione di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5ce9f82e88c6275000c17d40e2b1e1494683715
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-interfaces"></a>Interfacce di valutazione di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito sono le interfacce di valutazione di espressioni per la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono utilizzate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per common language runtime gli analizzatori di espressioni (Java EE).  
  
 Ogni interfaccia nella tabella viene illustrato il componente che può implementare dall'elenco seguente:  
  
-   Eseguire il debug del motore (Germania)  
  
-   Analizzatore di espressioni (Java EE)  
  
-   Visual Studio (VS)  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias per una variabile numerico.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni (Java EE) per ottenere il dominio applicazione per l'alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta una matrice gestita e consente un analizzatore di espressioni (Java EE) per determinare l'indice di base (inferiore) per la matrice.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta uno strumento di associazione che associa i simboli per gli indirizzi effettivi in memoria di debug.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Stesso come il [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia ma fornisce l'accesso a tipi, gli alias e i visualizzatori personalizzati.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione avanzata di un analizzatore di espressioni (Java EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni (Java EE) con una struttura ad albero parser avanzata.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente un analizzatore di espressioni (Java EE) visualizzare un messaggio nella finestra di output del debugger.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stesso come il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia ma fornisce l'accesso a informazioni aggiuntive.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per essere valutata.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in un albero di analisi ed estende il **IDebugPointerObject** interfaccia.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilità di modificare il valore di un tipo tramite un visualizzatore di tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Consente di accedere ai visualizzatori personalizzati e i visualizzatori di tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilità di creare un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) oggetto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)