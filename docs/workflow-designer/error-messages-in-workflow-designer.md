---
title: I messaggi di errore nella finestra di progettazione del flusso di lavoro | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: a167848362c8979046ba4dc02c6396616ccb71ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-messages-in-workflow-designer"></a>Messaggi di errore in Progettazione flussi di lavoro
In questo argomento vengono descritti i tipi dei messaggi di errore che possono verificarsi durante l'uso di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situazioni nelle quali si verificano gli errori in Progettazione flussi di lavoro  
 Gli errori in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] si verificano nelle situazioni seguenti:  
  
1.  È presente un errore in un'espressione.  
  
2.  Non sono stati soddisfatti i vincoli di convalida di un'attività.  
  
3.  Sono presenti errori nel file XAML che impediscono il caricamento di un'attività.  
  
4.  Sono presenti errori nel file XAML che impediscono il caricamento del flusso di lavoro.  
  
 Espressioni non valide e vincoli di convalida non possono impedire la compilazione del flusso di lavoro. La compilazione del flusso di lavoro infatti riesce, ma viene generato un oggetto <xref:System.Activities.InvalidWorkflowException> in fase di esecuzione. In presenza di errori nel file XAML, la compilazione non riesce.  
  
 All'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quando un flusso di lavoro viene caricato, relativi errori vengono visualizzati nel **elenco errori**. Per passare all'attività che rappresenta l'origine dell'errore, fare doppio clic su errore nel **elenco errori**.  
  
### <a name="expression-errors"></a>Errori nelle espressioni  
 Un'espressione non valida viene segnalata da un cerchio rosso con un punto esclamativo bianco accanto a essa. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fare clic sull'espressione per visualizzare la riga che sottolinea l'origine dell'errore. Se si posiziona il mouse sul testo sottolineato, viene visualizzata una descrizione comandi relativa all'origine dell'errore.  
  
### <a name="activity-validation-errors"></a>Errori di convalida delle attività  
 Una volta soddisfatti i vincoli di convalida di un'attività, viene visualizzato un cerchio rosso con un punto esclamativo bianco nell'angolo superiore destro dell'attività. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore.  
  
### <a name="xaml-load-errors"></a>Errori di caricamento di XAML  
 Quando un'attività non viene caricata, viene visualizzata una casella rossa con il testo "attività potrebbe non essere caricato a causa di errori nel codice XAML". Ciò si verifica in genere quando il tipo dell'attività non può essere risolto. L'attività non valida può essere eliminata nella finestra di progettazione selezionando ed eliminando la casella rossa.  
  
### <a name="workflow-load-errors"></a>Errori di caricamento del flusso di lavoro  
 Quando un flusso di lavoro non viene caricato, il testo "Problemi di progettazione del flusso di lavoro con il documento" viene visualizzato nell'area di progettazione, con le informazioni di eccezione che ha causato l'errore del flusso di lavoro da caricare. Ciò si verifica in genere quando non è possibile analizzare il file XAML.