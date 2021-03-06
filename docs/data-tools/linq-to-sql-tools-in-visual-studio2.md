---
title: Panoramica di LINQ to SQL O/R Designer
description: Ottenere una panoramica degli strumenti di LINQ to SQL in Visual Studio. Informazioni sul Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 20473125814b1ee0569579c7248b7b940cd31500
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858644"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Strumenti di LINQ to SQL in Visual Studio

LINQ to SQL è stata la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene negli scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo attivo. Usare LINQ to SQL quando si gestisce un'applicazione legacy che lo sta già usando o in applicazioni semplici che usano SQL Server e non richiedono il mapping a più tabelle. In generale, le nuove applicazioni devono usare il Entity Framework quando è necessario un livello di mapper relazionale a oggetti.

## <a name="install-the-linq-to-sql-tools"></a>Installare gli strumenti di LINQ to SQL

In Visual Studio è possibile creare classi di LINQ to SQL che rappresentano le tabelle SQL tramite **Object Relational Designer** (**O/R Designer**). La finestra di progettazione di O/R è l'interfaccia utente per la modifica di file con estensione dbml. Per modificare i file con estensione dbml con un'area di progettazione sono necessari gli strumenti LINQ to SQL che non sono installati per impostazione predefinita come parte di tutti i carichi di lavoro di Visual Studio.

Per installare gli strumenti di LINQ to SQL, avviare il programma di installazione di Visual Studio, scegliere **modifica**, quindi selezionare la scheda **singoli componenti** e quindi selezionare **LINQ to SQL strumenti** nella categoria **strumenti codice** .

## <a name="what-is-the-or-designer"></a>Che cos'è l'oggetto O/R Designer

Nella finestra di progettazione di **O/R** sono presenti due aree distinte: il riquadro entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi rappresenta invece l'area di progettazione in cui vengono visualizzati i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.

**Progettazione relazionale** oggetti fornisce un'area di progettazione visiva per la creazione di [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) le classi di entità e le associazioni (relazioni) basate sugli oggetti in un database. In altre parole, in **Progettazione relazionale** oggetti viene creato un modello a oggetti in un'applicazione che esegue il mapping a oggetti in un database. Genera inoltre un oggetto fortemente tipizzato <xref:System.Data.Linq.DataContext> che invia e riceve dati tra le classi di entità e il database. **O/R Designer** fornisce anche la funzionalità per eseguire il mapping di stored procedure e funzioni ai <xref:System.Data.Linq.DataContext> metodi per la restituzione di dati e il popolamento delle classi di entità. Infine, la **finestra di progettazione di O/R** fornisce la possibilità di progettare relazioni di ereditarietà tra le classi di entità.

## <a name="open-the-or-designer"></a>Aprire la finestra di progettazione O/R

Per aggiungere un modello di entità LINQ to SQL al progetto, scegliere **progetto**  >  **Aggiungi nuovo elemento** e quindi selezionare **LINQ to SQL classi** dall'elenco di elementi del progetto:

![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un file con *estensione dbml* e lo aggiunge alla soluzione. Si tratta del file di mapping XML e dei file di codice correlati.

![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Quando si seleziona il file con *estensione dbml* , Visual Studio Mostra l'area della **finestra di progettazione O/R** che consente di creare visivamente il modello. Nella figura seguente viene illustrata la finestra di progettazione dopo il `Customers` `Orders` trascinamento di Northwind e tabelle da **Esplora server**. Si noti la relazione tra le tabelle.

![Finestra di progettazione di LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Designer** è un semplice mapper relazionale a oggetti perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, ad esempio il mapping di una classe di entità a una tabella unita in join, non è supportato. usare il Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali apportate al file di codice non vengono riflesse in **O/R Designer**. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate per il **O/R Designer**, vedere [come: Estendere il codice generato da Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Creare e configurare DataContext

Dopo l'aggiunta di un elemento **classi LINQ to SQL** a un progetto e l'apertura di **Progettazione relazionale** oggetti, l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per la configurazione. L'oggetto <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Pertanto, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato usando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per ulteriori informazioni sulla <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Creare classi di entità con mapping a tabelle e viste di database

È possibile creare classi di entità di cui è stato eseguito il mapping a tabelle e viste trascinando le tabelle e le viste di database da **Esplora server** o **Esplora database** su **Progettazione relazionale di o/R**. Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se un elemento successivo che usa una connessione diversa viene aggiunto a **Progettazione relazionale** oggetti, è possibile modificare la connessione per <xref:System.Data.Linq.DataContext> . Per altre informazioni, vedere [procedura: creare LINQ to SQL classi mappate a tabelle e viste (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creazione di metodi DataContext che chiamano stored procedure e funzioni

È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano le stored procedure e le funzioni (a cui è stato eseguito il mapping) trascinandoli da **Esplora server** o **Esplora database** su **Progettazione relazionale** elementi. Le stored procedure e le funzioni vengono aggiunte alla **finestra di progettazione di O/R** come metodi dell'oggetto <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Quando si trascinano stored procedure e funzioni da **Esplora server** o **Esplora database** su **Progettazione relazionale** oggetti, il tipo restituito del <xref:System.Data.Linq.DataContext> metodo generato varia a seconda della posizione in cui si rilascia l'elemento. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurare un oggetto DataContext per l'utilizzo di stored procedure per salvare i dati tra le classi di entità e un database

Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è possibile assegnare le stored procedure utilizzate per il comportamento predefinito LINQ to SQL Runtime, che esegue inserimenti, aggiornamenti ed eliminazioni. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Object Relational Designer

Analogamente ad altri oggetti, le classi LINQ to SQL possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. **Progettazione** relazionale oggetti supporta il concetto di ereditarietà a tabella singola poiché viene spesso implementato nei sistemi relazionali. Per altre informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Query LINQ to SQL

Le classi di entità create da **O/R Designer** sono progettate per l'uso con [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/). Per ulteriori informazioni, vedere [procedura: eseguire una query per ottenere informazioni](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separare il codice DataContext e la classe di entità generati in spazi dei nomi diversi

In **O/R Designer** sono disponibili lo **spazio dei nomi del contesto** e le proprietà **dello spazio dei nomi dell'entità** in <xref:System.Data.Linq.DataContext> . Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diverso da quello dell'applicazione, immettere un valore nelle proprietà **Context Namespace** e/o **Entity Namespace**.

## <a name="reference-content"></a>Contenuto di riferimento

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Domande frequenti (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
