---
title: Debug di flussi di lavoro Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d15236de90af6a8749482f2b159d66c28a1b8c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-legacy-workflows"></a>Debug dei flussi di lavoro legacy
Se si sta usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] in [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per compilare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] destinate a .NET Framework 3.0 o 3.5, è possibile eseguire il debug dei flussi di lavoro come con qualsiasi altro programma impostando punti di interruzione, creando connessioni ai processi ed esaminando i thread e lo stack di chiamate. È inoltre possibile eseguire il debug in modalità remota.  
  
> [!NOTE]
>  Se più versioni di Visual Studio vengono installate e disinstallate sul computer, il debug WF3 potrebbe non riuscire per una delle due seguenti cause:  
>   
>  -   I punti di interruzione non vengono rilevati.  
> -   Viene visualizzato il seguente messaggio:  
>   
>  **Impossibile avviare il debug sul server web. Il debugger non è installato correttamente.  Impossibile eseguire il debug del tipo di codice richiesto.  Eseguire il programma di installazione per installare o ripristinare il debugger.**  
>   
>  Se uno di questi scenari si verifica durante il debug dei flussi di lavoro .NET Framework 3.0 o 3.5, eseguire un ripristino dell'installazione di Visual Studio.  
  
 La [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] si integra con le seguenti finestre di debug standard di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   **Punto di interruzione**: funziona come previsto, ma si specifica un'attività per il nome della funzione.  
  
-   **Stack di chiamate**: modificato per fornire una struttura delle attività eseguite in un'istanza del flusso di lavoro. Le voci di **Stack di chiamate** finestra sono una ricerca approfondita di attività in esecuzione. È possibile fare doppio clic su una voce per selezionare l’attività desiderata.  
  
-   **Thread**: fornisce l'ID istanza dell'istanza del flusso di lavoro che viene eseguito il debug.  
  
 Visual Studio per Windows Workflow Foundation non supporta le funzionalità di debug seguenti:  
  
-   Punti di interruzione condizionali nell'area di progettazione.  
  
-   Controllo immediato.  
  
-   Imposta istruzione successiva.  
  
-   Esegui fino al cursore.  
  
-   Modifica e continuazione.  
  
-   Debug JIT.  
  
-   Debug in modalità mista.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Procedura: Eseguire il debug di flussi di lavoro basati su ASP.NET (legacy)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Procedura: Impostare punti di interruzione nei flussi di lavoro (legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Esecuzione del debug dei flussi di lavoro da computer remoto (legacy)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Opzioni di avanzamento nell’esecuzione del debug (legacy)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Procedura: Modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)