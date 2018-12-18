---
title: Creare visualizzazioni personalizzate dei dati nel debugger | Documenti Microsoft
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8f008ba3cde911ed5c21f281d30fda2a77bf824
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Creare visualizzazioni personalizzate dei dati nel debugger di Visual Studio
Nel debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è disponibile una serie di strumenti che consentono di analizzare e modificare lo stato del programma. La maggior parte di questi strumenti è utilizzabile solo in modalità di interruzione.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creare visualizzazioni personalizzate dei dati nelle finestre delle variabili e i suggerimenti dati
 Molte del [finestre del debugger](../debugger/debugger-windows.md), ad esempio il **Auto** e **espressioni di controllo** windows, consentono di controllare le variabili durante il debug. È possibile personalizzare la visualizzazione di tipi nativi e gestiti gli oggetti nelle finestre delle variabili del debugger e in [i suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Può essere utile per visualizzare i tipi creati in applicazioni personalizzate. Per ulteriori informazioni, vedere [creare viste personalizzate di oggetti nativi di](../debugger/create-custom-views-of-native-objects.md) e [creare viste personalizzate di oggetti gestiti](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Creazione di visualizzatori personalizzati  
 I visualizzatori consentono di visualizzare il contenuto di un oggetto o variabile in modo significativo. Nel debugger di Visual Studio, un visualizzatore fa riferimento a varie finestre che è possibile aprire l'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore"). È ad esempio possibile usare il visualizzatore HTML per visualizzare una stringa HTML come verrebbe interpretata e visualizzata in un browser. I visualizzatori sono accessibili dai suggerimenti dati, dalla finestra di dialogo **Controllo immediato** e dalle finestre **Espressioni di controllo** , **Auto** e **Variabili locali** . Per ulteriori informazioni, vedere [creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Command Window](../ide/reference/command-window.md)  (Finestra di comando)  
 [Sicurezza del debugger](../debugger/debugger-security.md)