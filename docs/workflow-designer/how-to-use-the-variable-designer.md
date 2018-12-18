---
title: 'Procedura: utilizzare la finestra di progettazione variabile | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c9bf63222f16e29044a9a07078096b765421fbb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-variable-designer"></a>Procedura: utilizzare la finestra di progettazione variabili
La finestra di progettazione variabili consente di creare variabili da usare in scenari di data binding e istruzioni condizionali. Viene visualizzata la finestra di progettazione facendo il **variabili** pulsante nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di variabili che vengono visualizzati in formato tabulare e possono essere ordinati da ciascuna delle intestazioni di colonna, ad eccezione di **predefinito** colonna. Ogni variabile contiene un nome, un tipo di variabile, un ambito e un valore predefinito (se presente). Il nome e il valore predefinito sono campi di testo modificabili mentre il tipo e l'ambito sono elenchi a discesa. L'ambito è l'attività selezionata al momento del richiamo della finestra di progettazione variabili. Se non è possibile creare una variabile nell'ambito della selezione, l'ambito verrà impostato in modo predefinito sull'attività predecessore più vicina della selezione in modo da consentire la creazione di variabili nel relativo ambito. [! INCLUDERE[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
 L'ordinamento non viene applicato fino a quando l'utente non usa in modo esplicito uno dei controlli di ordinamento, chiude e riapre la finestra di progettazione variabili o crea un'altra variabile.  
  
### <a name="to-create-a-new-variable"></a>Per creare una nuova variabile  
  
1.  Aprire una soluzione per flusso di lavoro o attività in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Nell'area di progettazione selezionare un'attività nel flusso di lavoro.  
  
3.  Aprire la finestra di progettazione variabile facendo clic di **variabili** pulsante nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione variabili.  
  
4.  Fare clic sulla riga vuota denominata **Crea variabile**. Verrà aggiunta una nuova riga con una nuova variabile con i valori predefiniti seguenti: variablex per il **nome** dove x è un intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di variabile univoci,  **Stringa** per il **tipo di variabile**, e **sequenza** per il **ambito**. Viene aggiunto alcun valore per **predefinito**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.  
  
    > [!NOTE]
    >  Per eliminare una variabile, selezionare la variabile facendovi clic sopra e quindi premere il **eliminare** chiave.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando la finestra di progettazione del flusso di lavoro](../workflow-designer/using-the-workflow-designer.md)   
 [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)   
 [Procedura: Usare la finestra di progettazione argomenti](../workflow-designer/how-to-use-the-argument-designer.md)