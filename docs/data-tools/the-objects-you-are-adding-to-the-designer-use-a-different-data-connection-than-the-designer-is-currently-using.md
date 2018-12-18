---
title: Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: dc08b045ebd02496d0ae87055b205285ee5ab57f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Gli oggetti a cui che si sta aggiungendo alla finestra di progettazione utilizzano una connessione dati diversa da quella finestra di progettazione

Gli oggetti in corso di aggiunta alla finestra di progettazione usano una connessione dati diversa da quella usata per la finestra di progettazione. Sostituire la connessione usata per la finestra di progettazione?

Quando si aggiungono elementi al [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), tutti gli elementi usano un'unica connessione dati condivisa. (l'area di progettazione rappresenta l'oggetto <xref:System.Data.Linq.DataContext>, che usa una sola connessione per tutti gli oggetti nell'area). Questo messaggio viene visualizzato se si aggiunge alla finestra di progettazione un oggetto che usa una connessione dati differente da quella attualmente usata per la finestra di progettazione. Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente. In questo caso, l'oggetto selezionato non verrà aggiunto. In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare il <xref:System.Data.Linq.DataContext> connessione alla nuova connessione.

> [!NOTE]
> Se si fa clic **Sì**, le classi di tutte le entità nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene eseguito il mapping alla nuova connessione.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Per sostituire la connessione esistente con quella usata per l'oggetto selezionato

- Scegliere **Sì**.

    L'oggetto selezionato viene aggiunto a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]e l'oggetto DataContext.Connection viene impostato sulla nuova connessione.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Per continuare a usare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato

- Fare clic su **No**.

    L'azione viene annullata e l'oggetto DataContext.Connection resta impostato sulla connessione esistente.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
