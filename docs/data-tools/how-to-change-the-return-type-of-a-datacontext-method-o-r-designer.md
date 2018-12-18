---
title: 'Procedura: modificare il tipo restituito di un metodo DataContext (O-R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bba6a516cb0b94f91afd21b4a9f26821aec0c922
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)
Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> (creato in base a una stored procedure o funzione) varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un <xref:System.Data.Linq.DataContext> (metodo), selezionarlo e fare clic su di **Return Type** proprietà il **proprietà** finestra.

> [!NOTE]
>  Non è possibile ripristinare <xref:System.Data.Linq.DataContext> metodi che presentano un tipo restituito impostato su una classe di entità per restituire il tipo generato automaticamente tramite il **proprietà** finestra. Per ripristinare la restituzione di un tipo generato automaticamente da parte di un metodo <xref:System.Data.Linq.DataContext>, è necessario trascinare nuovamente l'oggetto di database originale in Progettazione relazionale oggetti.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità

1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.

2.  Selezionare **Return Type** nel **proprietà** alla classe finestra e quindi selezionare un'entità disponibile nel **Return Type** elenco. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] per aggiungerlo all'elenco.

3.  Salvare il file .dbml.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente

1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi ed eliminarlo.

2.  Trascinare l'oggetto di database da **Esplora Server**/**Esplora Database** in un'area vuota della finestra di Progettazione relazionale.

3.  Salvare il file .dbml.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)