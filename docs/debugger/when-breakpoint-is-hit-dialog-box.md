---
title: Quando i punti di interruzione è la finestra di dialogo Hit | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d2d0940764e64f9179eb8346c271afa6136b72f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Finestra di dialogo Quando il punto di interruzione viene raggiunto
Con questa finestra di dialogo, è possibile personalizzare l'azione che si verifica quando viene raggiunto un punto di interruzione.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Stampa un messaggio**  
 Stampa un messaggio, utilizzando la sintassi DebuggerDisplay. Per ulteriori informazioni, vedere [utilizzando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Questa casella di testo supporta anche parole chiave speciali (ad esempio $ADDRESS) che possono essere utilizzate da soli o tra le parentesi graffe di un'espressione DebuggerDisplay. Le parole chiave disponibili sono elencate nella finestra di dialogo.  
  
 **Continuare l'esecuzione**  
 Questo controllo è abilitato solo quando **stampa un messaggio** è selezionata. A questo controllo è selezionato, è possibile utilizzare un punto di interruzione come un punto di analisi per tracciare l'esecuzione del programma, anziché l'interruzione quando viene raggiunto il percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando i punti di interruzione](../debugger/using-breakpoints.md)   
 [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)