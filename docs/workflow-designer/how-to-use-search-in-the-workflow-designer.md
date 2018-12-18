---
title: 'Procedura: utilizzare la ricerca nella finestra di progettazione del flusso di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 20e4cca7723a47b5735301c54a67029f0f956c49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro
Per facilitare la creazione di flussi di lavoro più ampi e complessi, è possibile usare la ricerca in Progettazione flussi di lavoro per trovare gli elementi per parola chiave. Notare che la finestra di progettazione non supporta la sostituzione. La ricerca nella finestra di progettazione verrà trovato quanto segue:  
  
## <a name="quick-find"></a>Ricerca veloce  
 La ricerca rapida troverà nella finestra di progettazione quanto segue:  
  
-   Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.  
  
-   Variabili  
  
-   Argomenti  
  
-   Espressioni  
  
#### <a name="using-quick-find"></a>Uso di Ricerca veloce  
  
1.  Con Progettazione flussi di lavoro aperta, premere **Ctrl + F**, oppure selezionare **modifica**, **Trova e sostituisci**, **ricerca veloce**.  
  
2.  Immettere il termine di ricerca nel **trova** casella di testo e fare clic su **Trova successivo**.  
  
3.  Il termine di ricerca è posizionato nel flusso di lavoro corrente. Nella schermata seguente viene illustrato un nome visualizzato dell'attività che si trova nella finestra di progettazione.  
  
     ![Nei risultati della ricerca nella finestra di progettazione del flusso di lavoro](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Cercare nei file  
 Tramite l'uso di Cerca nei file è possibile trovare le stringhe nei file del flusso di lavoro, inclusi i file XAML.  
  
#### <a name="using-find-in-files"></a>Uso di Cerca nei file  
  
1.  In Visual Studio, premere **Ctrl + Maiusc + F**, oppure selezionare **modifica**, **Trova e sostituisci**, **Cerca nei file**  
  
2.  Immettere l'elemento di ricerca nel **trova** casella di testo e fare clic su **Trova tutti**  
  
3.  Verrà visualizzato il risultato di ricerca nel [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] **risultati ricerca** visualizzazione. Facendo doppio clic su un elemento del risultato verrà visualizzata l'attività contenente la corrispondenza nella finestra di progettazione del flusso di lavoro.