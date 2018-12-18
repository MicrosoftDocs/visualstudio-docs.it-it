---
title: Il contesto di valutazione di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab4e57f500c2dfbfe673713c784cbc93ff52a73d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-context"></a>Contesto di valutazione dell'espressione
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **il contesto di valutazione di espressioni**:  
  
-   Rappresenta un contesto per la valutazione dell'espressione. In genere, un contesto di valutazione corrisponde per l'ambito lessicale in cui valutare variabili, parametri, funzioni e metodi. Ad esempio, un contesto di valutazione di espressione associato a uno stack frame fornirà il contesto per la valutazione di variabili locali, parametri del metodo e i membri di classe (se applicabile).  
  
-   Si verifica quando un programma è stata interrotta in un punto di interruzione. L'espressione stessa è una struttura di dati che rappresenta un'espressione analizzata è pronta per l'associazione e la valutazione all'interno del contesto specificato.  
  
     In modo più dettagliato, le espressioni vengono create utilizzando il [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo. Quando viene valutata un'espressione, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra Espressioni di controllo o nella finestra variabili locali dell'IDE.  
  
     Dato un `BSTR` e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia, è possibile creare un motore di debug (DE) un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia mediante l'analisi di un'espressione. Dato un `IDebugExpression2` interfaccia, la Germania può ottenere un valore tramite la valutazione dell'espressione di tipo sincrono o asincrono. Questo valore, insieme a nome e il tipo della variabile o argomento, viene inviato all'IDE per la visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)