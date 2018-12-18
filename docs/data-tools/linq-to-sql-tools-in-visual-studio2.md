---
title: Panoramica di Visual Studio O/R Designer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a160cce25814cd2e110f8896ed6752a18b5dd0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL Tools in Visual Studio
LINQ to SQL è la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene in scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo. Utilizzo di LINQ to SQL per la manutenzione di un'applicazione legacy che è già in uso in o in semplici applicazioni che utilizzano SQL Server e non necessitano del mapping di più tabelle. In generale, le nuove applicazioni devono utilizzare Entity Framework quando è necessario un livello di mapping relazionale a oggetti.  
  
In Visual Studio creare classi LINQ to SQL che rappresentano le tabelle SQL utilizzando la Object Relational Designer (O/R Designer).  
  
Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sono presenti due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi è l'area di progettazione che consente di visualizzare il <xref:System.Data.Linq.DataContext> metodi che vengono eseguito il mapping a stored procedure e funzioni.  
  
Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornisce un'area di progettazione visiva per la creazione di [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità e associazioni (relazioni) che si basano su oggetti in un database. In altre parole, [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene usato per creare un modello a oggetti in un'applicazione con mapping agli oggetti in un database e genera inoltre un oggetto <xref:System.Data.Linq.DataContext> fortemente tipizzato, usato per inviare e ricevere dati tra le classi di entità e il database. In [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è disponibile anche una funzionalità per eseguire il mapping di stored procedure e funzioni ai metodi <xref:System.Data.Linq.DataContext> per la restituzione di dati e il popolamento delle classi di entità. Infine, in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene fornita la possibilità di progettare relazioni di ereditarietà tra le classi di entità.  
  
## <a name="opening-the-or-designer"></a>Apertura di Progettazione relazionale oggetti  
 Per aggiungere un LINQ per il modello entity SQL al progetto, scegliere **progetto**, **Aggiungi nuovo elemento** e quindi scegliere **classi LINQ to SQL** dall'elenco di elementi di progetto:  
  
 ![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata classi LINQ to SQL")  
  
 Visual Studio crea un file con estensione dbml e aggiungerlo alla soluzione. Questo è il file di mapping XML e i relativi file di codice correlate.  
  
 ![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "classi LINQ to SQL raddata in Esplora soluzioni")  
  
 Quando si seleziona il file. dbml, Visual Studio Mostra l'area di Progettazione relazionale che consente di creare visivamente il modello. Nella figura seguente mostra la finestra di progettazione dopo che sono state trascinate le tabelle Northwind Customers e Orders da Esplora Server. Si noti la relazione tra le tabelle.  
  
 ![Progettazione LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è un'utilità di mapping relazionale oggetti semplice, poiché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Mapping complesso, quale il mapping di una classe di entità a una tabella unita in join, non è supportato. utilizzo di Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali apportate al file di codice non vengono riflesse in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vedere [procedura: estendere il codice generato da Progettazione relazionale](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Creazione e configurazione dell'oggetto DataContext  
 Dopo aver aggiunto un **classi LINQ to SQL** elemento a un progetto e aperto il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per essere configurato. il <xref:System.Data.Linq.DataContext> è configurato con informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione... Pertanto, il <xref:System.Data.Linq.DataContext> viene configurato utilizzando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per ulteriori informazioni sul <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Creazione di classi di entità con mapping a tabelle e visualizzazioni di database  
 È possibile creare classi di entità con mappate alle tabelle e viste trascinando le tabelle del database e le viste da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] viene aggiunto un elemento successivo che usa una connessione diversa, è possibile modificare la connessione per l'oggetto <xref:System.Data.Linq.DataContext>. Per ulteriori informazioni, vedere [procedura: creare classi LINQ to SQL mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creazione di metodi DataContext che chiamano stored procedure e funzioni  
 È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano (viene eseguito il mapping a) stored procedure e funzioni trascinandole da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Le stored procedure e le funzioni vengono aggiunte a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] come metodi dell'oggetto <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Quando si trascinano stored procedure e funzioni da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> è diverso (metodo) a seconda della posizione in cui si rilascia l'elemento. Per ulteriori informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurazione di un oggetto DataContext in modo che utilizzi stored procedure per salvare i dati tra le classi di entità e un database  
 Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è anche possibile assegnare stored procedure utilizzabili per il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Progettazione relazionale oggetti  
 Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per ulteriori informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Query [LINQ to SQL]  
 Le classi di entità create dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sono progettati per l'utilizzo con [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/). Per ulteriori informazioni, vedere [procedura: eseguire Query per informazioni](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separazione del codice delle classi di entità e DataContext generate in diversi spazi dei nomi  
 Il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornisce il **contesto Namespace** e **Entity Namespace** proprietà il <xref:System.Data.Linq.DataContext>. Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi dell'applicazione diverso da, immettere un valore nel **contesto Namespace** e/o **Entity Namespace** proprietà.
  
## <a name="reference-content"></a>Contenuto di riferimento
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>Vedere anche
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[Domande frequenti (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 