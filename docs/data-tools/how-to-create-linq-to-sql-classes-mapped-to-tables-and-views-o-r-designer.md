---
title: Eseguire il mapping di classi LINQ to SQL a tabelle/viste (O-R Designer)
description: Informazioni su come creare classi di entità LINQ to SQL (classi mappate a tabelle e viste) in Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b440e8c47afdec6e0b04b5f48a35e15fe48e1875
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866801"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: Creare classi LINQ to SQL con mapping a tabelle e viste (Object Relational Designer)

Le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tabelle e viste di database sono dette *classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità basate su viste o tabelle di database trascinando le tabelle o le viste da **Esplora server** o **Esplora database** sugli [strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). La **finestra di progettazione di O/R** genera le classi e applica gli [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] attributi specifici per abilitare la [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funzionalità (le funzionalità di comunicazione e modifica dei dati di <xref:System.Data.Linq.DataContext> ). Per informazioni dettagliate sulle [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classi, vedere [il modello a oggetti LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **O/R Designer** è un semplice mapper relazionale a oggetti perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

Il trascinamento di tabelle o viste da **Esplora server** o **Esplora database** a **Progettazione relazionale** classi crea classi di entità oltre ai <xref:System.Data.Linq.DataContext> metodi utilizzati per l'esecuzione degli aggiornamenti.

Per impostazione predefinita, il runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se non si desidera questo comportamento, è possibile configurare una classe di entità per l'utilizzo di stored procedure per l'esecuzione di inserimenti, aggiornamenti ed eliminazioni anziché utilizzare il comportamento predefinito della [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] fase di esecuzione. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

1. In **Esplora server**/**Esplora database** espandere **Tabelle** o **Viste** e individuare la tabella o la vista di database da usare nell'applicazione.

2. Trascinare la tabella o la vista in **o/R Designer**.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creare l'origine dati di un oggetto e visualizzare i dati in un form

Dopo aver creato le classi di entità usando **Progettazione relazionale** oggetti, è possibile creare un'origine dati oggetto e popolare la [finestra Origini dati](add-new-data-sources.md#data-sources-window) con le classi di entità.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare il progetto.

2. Per aprire la finestra **origini dati** , scegliere **Mostra origini dati** dal menu **dati** .

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

5. Espandere i nodi, quindi individuare e selezionare la classe.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.

6. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

7. Trascinare gli elementi dalla finestra **Origini dati** in un form.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Il modello a oggetti di LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
