---
title: Estendibilità del Debugger di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5bb01c093fda068dfbc7dfa705914a8bdef4d2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del Debugger di Visual Studio
Visual Studio include un debugger di codice sorgente completamente interattivo, che fornisce uno strumento potente e facile da usare per rilevare i bug nel programma. Il debugger ha supporto completo per Visual Basic, c#, C/C++ e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], che è disponibile il [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), altri linguaggi di programmazione possono essere supportati nel debugger con la stessa funzionalità avanzate.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è comune front-end (ovvero, l'interfaccia utente) per i componenti di debug sono, a sua volta, a seconda della lingua in fase di debug. Per nuove lingue, è sufficiente per supportare dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger consiste nel creare i componenti necessari di back-end, ad esempio un motore di debug (DE). Dove è il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è disponibile in.  
  
 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento completo a tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi necessari per creare un nuovo DE. Inoltre, esistono esempi ed esercitazioni che consentono di iniziare.  
  
 Per un esempio end-to-end di un sistema di progetto di linguaggio con supporto per il debug, vedere il [esempio IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Nelle sezioni seguenti viene descritto come estendere il debugger usando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Viene descritto cosa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug offerte e su come installare il SDK.  
  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta il processo DE personalizzato, dalla preparazione del programma per un DE per scollegare la Germania.  
  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Descrive se è necessario scrivere un analizzatore di espressioni.  
  
 [Scelta di una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Viene illustrato come implementare la Germania.  
  
 [Riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'API di debug.  
  
 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene collegamenti per un esempio dell'analizzatore di espressioni espressione di common language runtime e un esempio di motore di debug.
