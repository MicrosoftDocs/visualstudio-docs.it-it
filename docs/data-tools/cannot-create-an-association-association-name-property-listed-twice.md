---
title: Impossibile creare un'associazione - proprietà elencata due volte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2d183241739df858b52700aef9ed8c065db6bd1a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà elencata due volte

Impossibile creare un'associazione \<nome associazione >. La stessa proprietà è elencata più volte: \<nome proprietà >.

Le associazioni vengono definite dall'oggetto selezionato **proprietà associazione** nel **Editor di associazione** la finestra di dialogo. Le proprietà possono essere elencate una sola volta per ogni classe nell'associazione.

La proprietà nel messaggio viene visualizzato più di una volta nell'elemento padre o figlio della classe **proprietà associazione**.

## <a name="to-resolve-this-condition"></a>Risoluzione del problema

- Esaminare il messaggio e prendere nota della proprietà specificata in esso.

- Fare clic su **OK** per chiudere la finestra di messaggio.

- Controllare il **proprietà associazione** e rimuovere le voci duplicate.

- Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura: creare un'associazione tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)