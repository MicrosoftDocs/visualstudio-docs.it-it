---
title: 'Procedura: creare LINQ to SQL classi con mappate a tabelle e viste (O-R Designer) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 3d295cc9527aae2f566f5ec4d1ba92a2b129fbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: creare LINQ to SQL classi con mappate a tabelle e viste (O/R Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]le classi che vengono eseguito il mapping di tabelle e viste del database vengono denominate *classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità che sono basate su viste o tabelle di database trascinando le tabelle o viste dal **Esplora Server**/**Esplora Database** sul [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] genera le classi e applica la specifica [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] attributi per attivare [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funzionalità (la comunicazione di dati e le funzionalità di modifica il <xref:System.Data.Linq.DataContext>). Per informazioni dettagliate su [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classi, vedere [LINQ al modello a oggetti SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).  
  
> [!NOTE]
>  Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è un'utilità di mapping relazionale oggetti semplice, poiché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.  
  
## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creazione di classi LINQ to SQL con mapping a tabelle o visualizzazioni di database  
 Trascinamento di tabelle o viste dal **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crea classi di entità oltre al <xref:System.Data.Linq.DataContext> metodi utilizzati per esecuzione di aggiornamenti.  
  
 Per impostazione predefinita, il runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se non si desidera questo comportamento, è possibile configurare una classe di entità in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione anziché usare il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database  
  
1.  In **Server**/**Esplora Database**, espandere **tabelle** o **viste** e individuare la tabella di database o la visualizzazione che si desidera da utilizzare nell'applicazione.  
  
2.  Trascinare la tabella o la visualizzazione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.  
  
## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creazione dell'origine dati di un oggetto e visualizzazione dei dati in un form  
 Dopo aver creato le classi di entità tramite il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], è possibile creare un'origine dati oggetto e popolare il [finestra Origini dati](add-new-data-sources.md) con le classi di entità.  
  
#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL  
  
1.  Nel **compilare** menu, fare clic su **Compila soluzione** per compilare il progetto.  
  
2.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
4.  Fare clic su **oggetto** sul **scegliere un tipo di origine dati** pagina e quindi fare clic su **Avanti**.  
  
5.  Espandere i nodi, quindi individuare e selezionare la classe.  
  
    > [!NOTE]
    >  Se il **cliente** classe non è disponibile, annullare la procedura guidata, compilare il progetto e rieseguire la procedura guidata.  
  
6.  Fare clic su **fine** per creare l'origine dati e aggiungere il **cliente** la classe di entità per il **origini dati** finestra.  
  
7.  Trascinare gli elementi dal **origini dati** finestra in un form.  
  
## <a name="see-also"></a>Vedere anche  
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL modello a oggetti](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)   
 [Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione di comportamento delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
  [Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)