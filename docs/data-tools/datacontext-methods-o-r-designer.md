---
title: Metodi DataContext (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b7c689ca374fe767c3db4ce8546b5bdcd560a19
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="datacontext-methods-or-designer"></a>Metodi DataContext (O/R Designer)

<xref:System.Data.Linq.DataContext> metodi (nel contesto del [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sono metodi del <xref:System.Data.Linq.DataContext> (classe) che eseguono stored procedure e funzioni in un database.

La classe <xref:System.Data.Linq.DataContext> rappresenta una classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] che funge da canale tra un database SQL Server e le classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tale database. La classe <xref:System.Data.Linq.DataContext> contiene le informazioni sulla stringa di connessione e i metodi per la connessione a un database e la modifica dei dati presenti in esso. Per impostazione predefinita, la classe <xref:System.Data.Linq.DataContext> contiene diversi metodi che è possibile chiamare, ad esempio il metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A> che invia dati aggiornati dalle classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] al database. È anche possibile creare ulteriori <xref:System.Data.Linq.DataContext> metodi con mapping a stored procedure e funzioni. In altre parole, la chiamata a questi metodi personalizzati determinerà l'esecuzione della stored procedure o funzione nel database a cui è stato eseguito il mapping del metodo <xref:System.Data.Linq.DataContext>. È possibile aggiungere nuovi metodi alla classe <xref:System.Data.Linq.DataContext> nello stesso modo in cui si aggiungono per estendere qualsiasi classe. Tuttavia, nelle discussioni sui <xref:System.Data.Linq.DataContext> metodi nel contesto del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], è il <xref:System.Data.Linq.DataContext> metodi che eseguono il mapping a stored procedure e funzioni che intendono fondamentalmente.

## <a name="methods-pane"></a>Riquadro Metodi

I metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni vengono visualizzati nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Il riquadro dei metodi è il riquadro lungo il lato del **entità** riquadro (area di progettazione principale). Il riquadro dei metodi sono elencati tutti <xref:System.Data.Linq.DataContext> metodi che è stato creato tramite il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Per impostazione predefinita, il riquadro dei metodi è vuoto. Trascinare stored procedure o funzioni da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] creare <xref:System.Data.Linq.DataContext> metodi e popolare il riquadro dei metodi. Per ulteriori informazioni, vedere [procedura: creare DataContext metodi con mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Aprire e chiudere il riquadro dei metodi facendo clic con il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e quindi fare clic su **Nascondi riquadro metodi** o **Mostra riquadro metodi**, oppure utilizzare il tasto di scelta rapida CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Due tipi di metodi DataContext

I metodi DataContext sono metodi con mapping a stored procedure e funzioni nel database. È possibile creare e aggiungere metodi DataContext nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Esistono due tipi distinti di <xref:System.Data.Linq.DataContext> metodi; quelli che restituiscono uno o più set di risultati e quelli che non:

-   Metodi <xref:System.Data.Linq.DataContext> che restituiscono uno o più set di risultati:

     Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure e funzioni nel database e restituire i risultati. Per ulteriori informazioni, vedere [procedura: creare DataContext metodi con mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, e <xref:System.Data.Linq.IMultipleResults>.

-   Metodi <xref:System.Data.Linq.DataContext> che non restituiscono set di risultati, ad esempio inserimenti, aggiornamenti ed eliminazioni per una classe di entità specifica.

     Creare questo tipo di <xref:System.Data.Linq.DataContext> metodo quando l'applicazione deve eseguire stored procedure anziché il valore predefinito [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento per il salvataggio dati modificati tra una classe di entità e il database. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Tipi restituiti dei metodi DataContext

Quando si trascinano stored procedure e funzioni da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> è diverso (metodo) a seconda della posizione in cui si rilascia l'elemento. Eliminazione degli elementi direttamente in una classe di entità esistente crea un <xref:System.Data.Linq.DataContext> (metodo) con il tipo restituito della classe di entità; rilascio degli elementi in un'area vuota del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (in dei riquadri) crea un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente. Questo tipo creato è dotato di un nome corrispondente a quello della stored procedure o funzione e di proprietà con mapping ai campi restituiti dalla stored procedure o funzione.

> [!NOTE]
> È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un <xref:System.Data.Linq.DataContext> (metodo), selezionarlo e controllare il **Return Type** proprietà il **proprietà** finestra. Per ulteriori informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Gli oggetti trascinati dal database nell'area Progettazione relazionale oggetti vengono denominati automaticamente, in base al nome degli oggetti nel database. Se si trascina più volte lo stesso oggetto, i vari nomi vengono distinti grazie all'aggiunta di un numero alla fine del nuovo nome. Se i nomi degli oggetti di database contengono spazi o caratteri non supportati in Visual Basic o C#, lo spazio o il carattere non valido viene sostituito con un carattere di sottolineatura.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [stored procedure](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)