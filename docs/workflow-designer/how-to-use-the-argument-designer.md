---
title: 'Procedura: utilizzare la finestra di progettazione argomenti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aa1cdd0dd563a5f87d4e32f779985afd63319032
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-argument-designer"></a>Procedura: utilizzare la finestra di progettazione argomenti
Se confrontata con le versioni precedenti di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la finestra di progettazione argomenti semplifica il flusso di dati da e verso un'attività. Viene visualizzata la finestra di progettazione facendo il **argomenti** pulsante nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di argomenti che vengono visualizzati in formato tabulare e possono essere ordinati da ciascuna delle intestazioni di colonna, ad eccezione di **il valore predefinito** colonna. Ogni argomento include un nome, una direzione per la proprietà in/out/in-out, un tipo e un valore di espressione predefinito (se presente). Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa. [! INCLUDERE[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
### <a name="to-create-a-new-argument"></a>Per creare un nuovo argomento  
  
1.  Aprire una soluzione per flusso di lavoro o attività in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Aprire la finestra di progettazione facendo clic di **argomenti** pulsante nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione argomenti.  
  
3.  Fare clic sulla riga vuota denominata **Crea argomento**. Verrà aggiunta una nuova riga con un nuovo argomento utilizzando i valori predefiniti seguenti: argumentx per il **nome** dove x è un intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di argomenti univoci, **In**  per il **direzione**, e **stringa** per il **tipo di argomento**. Viene aggiunto alcun valore per **il valore predefinito**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.  
  
    > [!NOTE]
    >  Per eliminare un argomento, selezionare l'argomento facendovi clic sopra e quindi premere il **eliminare** chiave.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando la finestra di progettazione del flusso di lavoro](../workflow-designer/using-the-workflow-designer.md)   
 [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)