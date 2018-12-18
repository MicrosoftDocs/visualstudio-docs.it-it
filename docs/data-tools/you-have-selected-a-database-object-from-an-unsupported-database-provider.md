---
title: È stato selezionato un oggetto di database da un provider di database non supportato
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0646f153149d887ce87f2688d9c28b3da502ba1c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato

O/R Designer supporta solo il Provider di dati .NET Framework per SQL Server (<xref:System.Data.SqlClient>). Anche se è possibile fare clic su **OK** e continuare a lavorare con gli oggetti di provider del database non supportato, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.

> [!NOTE]
> Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Fare clic su **OK**.

   È possibile continuare a progettare le classi di entità con mapping alla connessione che utilizza il provider di database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.

    oppure

- Fare clic su **Annulla**.

   L'azione viene interrotta. Creare o usare una connessione dati che si avvale del provider .NET Framework per SQL Server.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)