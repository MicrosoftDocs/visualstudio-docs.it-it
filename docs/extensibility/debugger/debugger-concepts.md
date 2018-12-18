---
title: Concetti del debugger | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 920706adb86d79e635e4f5289ca010e03282853e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-concepts"></a>Concetti di debugger
Per compilare il pacchetto di debug di Visual Studio, è necessario avere familiarità con i concetti dell'architettura della progettazione del pacchetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Sessione di debug](../../extensibility/debugger/debug-session.md)  
 Viene illustrato il ruolo di una sessione nell'architettura di debug.  
  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Definisce un server è in termini di debug di architettura, in termini sia abstract che fisici.  
  
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)  
 Definisce le azioni è un fornitore di porta in termini di architettura di debug.  
  
 [Porte](../../extensibility/debugger/ports.md)  
 Definisce il tipo di porta è in termini di architettura di debug.  
  
 [Processi](../../extensibility/debugger/processes.md)  
 Definisce il tipo di processo è in termini di architettura di debug.  
  
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)  
 Definisce un nodo di programma in termini di architettura, incluso come in grado di identificare se stesso e il processo che è in esecuzione nel debug.  
  
 [Programmi](../../extensibility/debugger/programs.md)  
 Definisce un programma in termini di architettura di debug.  
  
 [Thread](../../extensibility/debugger/threads.md)  
 Definisce le caratteristiche di thread in termini di architettura di debug.  
  
 [Stack frame](../../extensibility/debugger/stack-frames.md)  
 Definisce uno stack frame in termini di architettura di debug. Uno stack frame è un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread.  
  
 [Moduli](../../extensibility/debugger/modules.md)  
 Definisce un modulo, in termini di debug di architettura, come un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.  
  
 [Punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Definisce i tre tipi di punti di interruzione, in sospeso, associazione e di errore, in termini di architettura di debug.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione rilevante a esso.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (Java EE) e il gestore di simboli (SH).  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a numerose attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.