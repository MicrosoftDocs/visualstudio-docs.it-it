---
title: 'Procedura: estendere il codice generato dalla finestra di progettazione O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0210037cdd554838c9fe08c424f02b081c6f2e1a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: estendere il codice generato da O/R Designer
Il codice generato da [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene rigenerato quando vengono apportate modifiche alle classi di entità e ad altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] offre la possibilità di generare file di classe parziale in cui è possibile aggiungere codice che non verrà sovrascritto. Un esempio di aggiunta di codice personalizzato al codice generato da [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] consiste nell'aggiungere la convalida di dati a classi (di entità) LINQ to SQL. Per informazioni, vedere [procedura: aggiungere la convalida alle classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-code-to-an-entity-class"></a>Aggiunta di codice a una classe di entità

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità

1.  Aprire o creare un nuovo file LINQ to SQL Classes (**dbml** file) nei [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Fare doppio clic su di **. dbml** file **Esplora**/**Esplora Database**.)

2.  Nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], la classe per cui si desidera aggiungere la convalida, quindi fare clic destro **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3.  Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.

## <a name="adding-code-to-a-datacontext"></a>Aggiunta di codice a un oggetto DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Per creare una classe parziale e aggiungere codice a un oggetto DataContext

1.  Aprire o creare un nuovo file LINQ to SQL Classes (**dbml** file) nei [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Fare doppio clic su di **. dbml** file **Esplora**/**Esplora Database**.)

2.  Nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], fare doppio clic su un'area vuota della finestra di progettazione e quindi fare clic su **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.

3.  Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)