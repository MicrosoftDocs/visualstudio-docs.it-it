---
title: La chiamata di eventi del Debugger | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="calling-debugger-events"></a>Eventi del Debugger chiamata
Si verificano eventi nelle sessioni di debug in un ordine specifico.  
  
## <a name="discussion"></a>Discussione  
 Per comprendere il criterio di chiamate tra il motore di debug (DE) e il gestore di sessione di debug (SDM), di seguito rappresenta l'ordine degli eventi che si verificano in una sessione di debug tipica chiamante:  
  
1.  [Collegamento e scollegamento di un programma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Avvio del debugger](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Terminare un programma](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Creazione di un punto di interruzione](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Quando si associa un punto di interruzione o diventare non associato](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Errori di punto di interruzione](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Raggiungere un punto di interruzione](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [L'eliminazione di un punto di interruzione](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Modalità di interruzione](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Esecuzione in modalità di interruzione](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestione delle eccezioni](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)