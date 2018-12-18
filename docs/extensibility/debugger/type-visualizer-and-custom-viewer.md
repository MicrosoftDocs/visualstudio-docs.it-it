---
title: Digitare visualizzatore e il visualizzatore personalizzato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d419130cd93c6cc2f7dcff132fdafc8986bfd30a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizzatore di tipo e il visualizzatore personalizzato
Un visualizzatore di tipo è un componente che consente di visualizzare i dati in un formato molto specifico. Questo formato è interamente dipende dall'implementatore del visualizzatore, ovvero l'utente finale o un fornitore di terze parti di visualizzatori.  
  
 Un visualizzatore personalizzato è la parte di un analizzatore di espressioni personalizzato che consente di visualizzare i dati in un formato molto specifico. Questo formato è interamente dipende dall'implementatore del visualizzatore personalizzato, il che significa che il formato è dipende dall'implementatore dell'analizzatore di espressioni (Java EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Supporto per i visualizzatori di tipo in un analizzatore di espressioni  
 Un EE possibilità di supportare i visualizzatori di tipo che supporta un set di interfacce accessibile ai visualizzatori: interfacce, ad esempio [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Si noti tuttavia che l'analizzatore di Espressioni non è responsabile dell'implementazione del Visualizzatore di tipo stesso: l'analizzatore di Espressioni semplicemente consente i visualizzatori esterni di accedere a informazioni relative al tipo. Questi visualizzatori potrebbero essere forniti con l'analizzatore di Espressioni e installati nella posizione appropriata in Visual Studio, forniti da un altro fornitore di terze parti o anche dall'utente finale.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Supporto per i visualizzatori personalizzati disponibili in un analizzatore di espressioni  
 Un EE supporta anche i visualizzatori personalizzati in cui l'analizzatore di Espressioni fornisce il codice per la visualizzazione del tipo di dati. Un visualizzatore personalizzato implementa il [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) è richiesta l'interfaccia che gestisce tutti i compiti di mostrare i dati nel formato desiderato; il visualizzatore ha il pieno controllo sulla visualizzazione e può anche consentire il modifica dei dati. Qualsiasi visualizzatori personalizzati forniti dal motore di esecuzione forniti con l'analizzatore di Espressioni quando la distribuzione del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)