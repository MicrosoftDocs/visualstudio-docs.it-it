---
title: Stack frame | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 110a68d737ac2f194c7a318c41d05801d69511c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="stack-frames"></a>Stack frame
In termini di architettura del debugger, un **frame dello stack**:  
  
-   È un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Uno stack frame contiene le variabili locali della funzione e gli argomenti a esso. Per eseguire il debug con Visual Studio, la lingua o l'ambiente in fase di debug deve supportare frame dello stack.  
  
-   Può identificare e descrivere se stesso sia può restituire il thread associato. Il contesto del codice che rappresenta il puntatore all'istruzione corrente, nonché la relativa documentazione e contesti di valutazione di espressione, può restituire anche uno stack frame.  
  
-   Proprietà che descrivono il nome, tipo e valore delle variabili locali e gli argomenti e che vengono visualizzati nelle varie finestre di debug IDE.  
  
-   È rappresentato da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, in genere creata da un motore di debug (DE) o di una macchina virtuale come conseguenza un thread in esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)