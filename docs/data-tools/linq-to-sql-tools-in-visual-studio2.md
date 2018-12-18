---
title: Cenni preliminari su Visual Studio O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1d065a31c8c15ac26b7ded368499846cb9f0645
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Gli strumenti di LINQ to SQL in Visual Studio

LINQ to SQL è la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene in scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo. Utilizzo di LINQ to SQL per la manutenzione di un'applicazione legacy che è già in uso in o in semplici applicazioni che utilizzano SQL Server e non necessitano del mapping di più tabelle. In generale, le nuove applicazioni devono utilizzare Entity Framework quando è necessario un livello di mapping relazionale a oggetti.

In Visual Studio creare classi LINQ to SQL che rappresentano le tabelle SQL utilizzando la Object Relational Designer (O/R Designer).

O/R Designer ha due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi è l'area di progettazione che consente di visualizzare il <xref:System.Data.Linq.DataContext> metodi che vengono eseguito il mapping a stored procedure e funzioni.

O/R Designer fornisce un'area di progettazione visiva per la creazione [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità e associazioni (relazioni) che si basano sugli oggetti in un database. In altre parole, O/R Designer consente di creare un modello a oggetti in un'applicazione con mapping agli oggetti in un database. e genera inoltre un oggetto <xref:System.Data.Linq.DataContext> fortemente tipizzato, usato per inviare e ricevere dati tra le classi di entità e il database. O/R Designer anche fornisce funzionalità per eseguire il mapping di stored procedure e funzioni ai <xref:System.Data.Linq.DataContext> metodi per la restituzione di dati e il popolamento delle classi di entità. Infine, O/R Designer fornisce la possibilità di progettare relazioni di ereditarietà tra le classi di entità.

## <a name="open-the-or-designer"></a>Aprire la finestra di Progettazione relazionale oggetti

Per aggiungere un LINQ al modello di entità SQL al progetto, scegliere **Project** > **Aggiungi nuovo elemento**, quindi selezionare **classi LINQ to SQL** dall'elenco di elementi di progetto:

![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un file con estensione dbml e aggiungerlo alla soluzione. Questo è il file di mapping XML e i relativi file di codice correlate.

![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Quando si seleziona il file. dbml, Visual Studio Mostra l'area di Progettazione relazionale che consente di creare visivamente il modello. Nella figura seguente mostra la finestra di progettazione dopo che sono state trascinate le tabelle Northwind Customers e Orders da Esplora Server. Si noti la relazione tra le tabelle.

![LINQ to SQL Designer](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> O/R Designer è un'utilità di mapping relazionale oggetti semplice, poiché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Mapping complesso, quale il mapping di una classe di entità a una tabella unita in join, non è supportato. utilizzo di Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali al file di codice non vengono riflesse nella finestra di Progettazione relazionale oggetti. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate da O/R Designer, vedere [procedura: estendere il codice generato da Progettazione relazionale oggetti](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Creare e configurare l'oggetto DataContext

Dopo aver aggiunto un **classi LINQ to SQL** elemento a un progetto e aprire la finestra di Progettazione relazionale oggetti, l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per essere configurato. il <xref:System.Data.Linq.DataContext> è configurato con informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione... Pertanto, il <xref:System.Data.Linq.DataContext> viene configurato utilizzando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per ulteriori informazioni sul <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Creare le classi di entità con mapping a tabelle di database e visualizzazioni

È possibile creare classi di entità con mappate a tabelle e visualizzazioni trascinando le tabelle del database e a viste appartenenti **Esplora Server**/**Esplora Database** nella finestra di Progettazione relazionale oggetti. Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se un elemento successivo che usa una connessione diversa viene aggiunto a O/R Designer, è possibile modificare la connessione per il <xref:System.Data.Linq.DataContext>. Per ulteriori informazioni, vedere [procedura: creare classi LINQ to SQL mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creare metodi DataContext che chiamano stored procedure e funzioni

È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano (viene eseguito il mapping a) stored procedure e funzioni trascinandole da **Esplora Server**/**Esplora Database** nella finestra di Progettazione relazionale oggetti. Stored procedure e funzioni vengono aggiunti alla finestra di Progettazione relazionale oggetti come metodi del <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Quando si trascinano stored procedure e funzioni da **Esplora Server**/**Esplora Database** nella finestra di Progettazione relazionale oggetti, il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> è diverso (metodo) a seconda della posizione in cui si rilascia l'elemento. Per ulteriori informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurare un metodo DataContext per l'utilizzo di stored procedure per salvare i dati tra le classi di entità e un database

Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è inoltre possibile assegnare stored procedure che possono essere utilizzate per il valore predefinito LINQ al comportamento di runtime SQL che esegue i comandi di inserimento, aggiornamento ed eliminazione. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>L'ereditarietà e O/R designer

Analogamente ad altri oggetti, classi LINQ to SQL possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. O/R Designer supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per ulteriori informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Query LINQ to SQL

Le classi di entità create da O/R Designer sono progettate per l'utilizzo con [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Per altre informazioni, vedere [procedura: eseguire Query per informazioni](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separare il codice della classe entità e DataContext generato in diversi spazi dei nomi

O/R Designer fornisce il **contesto Namespace** e **Entity Namespace** proprietà il <xref:System.Data.Linq.DataContext>. Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi dell'applicazione diverso da, immettere un valore nel **contesto Namespace** e/o **Entity Namespace** proprietà.

## <a name="reference-content"></a>Contenuto di riferimento

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vedere anche

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Domande frequenti (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)