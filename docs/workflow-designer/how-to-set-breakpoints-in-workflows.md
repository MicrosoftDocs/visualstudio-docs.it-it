---
title: 'Procedura: impostare punti di interruzione nei flussi di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 4c9a3124ddefc892207ccc821b80056baab14166
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procedura: impostazione di punti di interruzione nei Flussi di lavoro
Quando si usa [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], è possibile impostare punti di interruzione nei flussi di lavoro grafici come si farebbe nel codice Visual Basic o C#. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.  
  
 Un punto di interruzione ha tre stati: *in sospeso*, *associato*, e *errore*. Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa. Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato. Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.  
  
> [!NOTE]
>  L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.  
  
> [!WARNING]
>  Assicurarsi di selezionare l'opzione **Abilita Just My Code (solo gestito)** dal **strumenti**, **opzioni**, **debug** menu prima eseguire il debug. Se si dispone di due sequenze annidate in un'altra sequenza e si imposta un punto di interruzione nella prima sequenza interna, premendo **F11** non eseguire il debug nella seconda sequenza interna se il **Abilita Just My Code (solo gestito)**opzione non è selezionata.  
  
> [!WARNING]
>  I punti di interruzione in un flusso di lavoro non vengono raggiunti se il percorso completo per la proprietà del file XAML non è corretto. Il percorso completo del file XAML non è preciso dopo avere spostato il progetto o la soluzione in un'altra cartella o a un altro computer. Selezionare CTRL+S per salvare e aggiornare la proprietà percorso completo.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione  
  
1.  Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.  
  
2.  Nel **Debug** dal menu **Attiva/Disattiva punto di interruzione**. Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.  
  
     In alternativa, è anche possibile premere il collegamento **F9** chiave dopo avere selezionato l'attività o si può fare doppio clic su attività e selezionare **punto di interruzione** quindi **Inserisci punto di interruzione**dal menu di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: richiamare il Debugger del flusso di lavoro](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Debug di flussi di lavoro con Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Procedura: Debug di XML mediante Progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)