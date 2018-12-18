---
title: "Introduzione al Debugger estendibilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 964b6bcc18e74174aa59e7a1bb4441e24d3918d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Guida introduttiva di estendibilità del Debugger
Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornisce le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi dall'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug è aggiunto miglioramenti derivati dall'usabilità completa test eseguiti nel precedente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger. È possibile utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug al passaggio tramite un'applicazione in più lingue, oppure è possibile implementare in tempo reale la modifica delle variabili durante il debug di applicazioni e soluzioni in più lingue.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug è eseguita out-of-process con il programma in fase di debug e pertanto è meno intrusivo nello spazio di elaborazione dell'applicazione. Di conseguenza, risulta più semplice scrivere i componenti che interagiscono con il debugger senza influire sull'applicazione di debug.  
  
 Per ottimizzare l'utilizzo di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], è necessario avere familiarità con le operazioni seguenti:  
  
-   Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE)  
  
-   Il linguaggio di programmazione C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>In questa sezione  
 [Guida di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descrive il processo di implementazione del prodotto, a seconda del compilatore e il relativo output di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug di componenti, che includono il motore di debug (DE), l'analizzatore di espressioni (Java EE) e il gestore di simboli (SH).  
  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, posizione, posizione o valutazione rilevante a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a numerose attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.