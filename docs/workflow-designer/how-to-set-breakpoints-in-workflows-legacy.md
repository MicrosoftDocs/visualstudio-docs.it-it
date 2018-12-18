---
title: 'Procedura: impostare punti di interruzione nei flussi di lavoro (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d634f9648ed87f448e1b984392c827badc42930c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Procedura: impostare punti di interruzione nei flussi di lavoro (legacy)
In questo argomento viene descritto come impostare punti di interruzione nelle applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando l'applicazione [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] deve fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si usa la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] per compilare un'applicazione [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)], è possibile impostare punti di interruzione nei codici C# e Visual Basic come in Visual Studio. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.  
  
 Un punto di interruzione ha tre stati: *in sospeso*, *associato*, e *errore*. Quando si imposta un punto di interruzione, sarà In sospeso e verrà rappresentato da un icona di colore rosso vuota. Quando il tipo del flusso di lavoro viene caricato dal runtime, diventa Associato e viene rappresentato da un’icona  rossa a tinta unita. Se si specifica un formato non corretto per il punto di interruzione, come avviene quando un nome di attività non è valido, verrà visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.  
  
 È possibile impostare punti di interruzione su un'attività sull'area di progettazione del flusso di lavoro nelle modalità seguenti:  
  
-   L'attività di mouse e scegliere **punto di interruzione \ inserire punto di interruzione**.  
  
-   Selezionare l’attività e premere F9.  
  
-   Selezionare **nuovo punto di interruzione** dal **Debug** menu.  
  
     È inoltre possibile usare questa opzione per impostare un nuovo punto di interruzione durante l'esecuzione del debug, quando il debugger si arresta in corrispondenza di un punto di interruzione.  
  
    > [!NOTE]
    >  L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Per impostare un punto di interruzione usando l'opzione Nuovo punto di interruzione nel menu Debug  
  
1.  Nel **Debug** dal menu **nuovo punto di interruzione**.  
  
2.  Fare clic su **Interrompi alla funzione**.  
  
     Il **nuovo punto di interruzione** verrà visualizzata la finestra di dialogo.  
  
3.  Specificare il nome di un'attività nel **funzione** casella di testo utilizzando questa sintassi: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Facoltativamente, anziché usare il nome dell'attività nel **funzione** casella di testo, è possibile impostare un punto di interruzione specificando il percorso assoluto dell'attività flusso di lavoro. Ad esempio, si supponga che si dispone di una soluzione del flusso di lavoro denominata **WorkflowConsoleApplication1** e un flusso di lavoro nella soluzione denominato **Workflow1** che utilizza un'attività denominata **Delay1**. È possibile utilizzare il nome dell'attività **Delay1** o specificare il percorso come **Delay1:WorkflowConsoleApplication1.Workflow1** o **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4.  Selezionare il **Usa IntelliSense** casella di controllo per verificare il nome della funzione.  
  
     Se questa casella di controllo non è selezionata, non viene eseguita nessuna verifica del nome del punto di interruzione.  
  
5.  Selezionare **flusso di lavoro** dal **Language** elenco.  
  
6.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)