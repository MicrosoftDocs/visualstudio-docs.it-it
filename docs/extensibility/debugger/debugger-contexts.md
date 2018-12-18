---
title: Contesti del debugger | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a9310512417ac0e24046a1b7bcc1fd92099fe98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-contexts"></a>Contesti di debugger
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, il motore di debug (DE) opera contemporaneamente in contesti diversi, come indicato di seguito:  
  
-   Il contesto del codice, che descrive la posizione corrente nel flusso di esecuzione del programma.  
  
-   Il contesto di documentazione o la posizione, che descrive la posizione corrente all'interno di un documento di origine.  
  
-   Il contesto di valutazione espressione, che descrive il contesto nel quale espressione valutazione verrà eseguita.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto del codice](../../extensibility/debugger/code-context.md)  
 Descrive il contesto del codice come un indirizzo nel flusso di istruzioni del programma odierna in fase di esecuzione le architetture e lingue utilizzate, in codice non può essere rappresentato da istruzioni, ma alcuni altri mezzi.  
  
 [Posizione nel documento](../../extensibility/debugger/document-position.md)  
 Definisce la posizione documento eseguire il debug tramite un'astrazione di una posizione in un file di origine come noto all'IDE di Visual Studio.  
  
 [Contesto del documento](../../extensibility/debugger/document-context.md)  
 Viene descritto il contesto del documento rappresenta in relazione a un file di origine eseguire il debug di Visual Studio. Illustra anche come il gestore di simboli esegue il mapping di un contesto di codice per il contesto di documentazione.  
  
 [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
 Fornisce informazioni su un contesto di valutazione di espressioni in Visual Studio. Ad esempio, un contesto di valutazione di espressione associato a uno stack frame fornisce il contesto per la valutazione di variabili locali, i parametri del metodo e i membri della classe.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti di debug](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Componenti di debug](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (Java EE) e il gestore di simboli (SH).  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a numerose attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.