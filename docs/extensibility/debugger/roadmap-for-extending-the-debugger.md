---
title: Guida di orientamento per l'estensione del Debugger | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 612017888c78f0994a83a10e3628fc10b667f8d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del Debugger
Questa documentazione fornisce guide e informazioni di riferimento per l'estensione di [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] del debugger con la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debug documentazione include esempi, un riferimento completo e rappresentativi scenari che illustrano le modalità per personalizzare il debugger.  
  
 Il compilatore e il relativo output determinare cosa è necessario eseguire per implementare il debug del prodotto. Se il compilatore:  
  
-   Destinazione di Windows nativo del sistema operativo e scrive un. Il file PDB, eseguire il debug di programmi con il motore di debug di codice nativo (DE), integrata in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Non è necessario implementare un analizzatore DE o un'espressione. L'analizzatore di espressioni viene scritta per la sintassi del linguaggio di programmazione C++.  
  
-   Produce Microsoft intermediate language (MSIL) di output, è possibile eseguire il debug di programmi con il motore di debug di codice gestito, DE, inoltre è integrato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Di conseguenza, è necessario implementare solo un analizzatore di espressioni. Un analizzatore di espressioni di esempio viene fornito automaticamente. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Valutazione delle espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Scrittura di un analizzatore di espressioni di Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   È destinato a un proprietario di un ambiente di runtime o del sistema operativo, è necessario scrivere la propria DE. Viene fornita un'esercitazione che consente di creare un semplice DE uso di ATL COM. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Esercitazione: Creazione di un motore di Debug tramite COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)