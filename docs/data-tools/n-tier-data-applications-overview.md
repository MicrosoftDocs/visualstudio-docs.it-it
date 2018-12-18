---
title: Cenni preliminari sull'applicazione dati a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 226fe4206af9e41d1d071b34e6985e00ce4041f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="n-tier-data-applications-overview"></a>Cenni preliminari sull'applicazione dati a più livelli
*A più livelli* le applicazioni di dati sono dati applicazioni separate in più *livelli*. Acronimo di "applicazioni distribuite" e "applicazioni multilivello", le applicazioni a più livelli separano l'elaborazione in livelli discreti che vengono distribuite tra il client e il server. Quando si sviluppano applicazioni che accedono ai dati, è necessario una netta separazione tra i vari livelli che costituiscono l'applicazione.

Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il modo più semplice per separare i vari livelli di un'applicazione a più livelli è possibile creare progetti discreti per ogni livello che si desidera includere nell'applicazione. Ad esempio, il livello di presentazione potrebbe essere un'applicazione Windows Form, mentre la logica di accesso ai dati potrebbe essere una libreria di classi che si trova nel livello intermedio. Inoltre, il livello di presentazione può comunicare con la logica di accesso ai dati nel livello intermedio tramite un servizio, ad esempio un servizio. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, Ciò avviene mediante l'adozione semplificata di nuove tecnologie che possono essere applicati a un singolo livello senza la necessità di riprogettare l'intera soluzione. Inoltre, le applicazioni a più livelli in genere archiviano informazioni riservate nel livello intermedio, che mantiene l'isolamento dal livello di presentazione.

Visual Studio è disponibili molte funzionalità che consentono agli sviluppatori di creare applicazioni a più livelli:

-   Il set di dati fornisce un **progetto DataSet** proprietà che consente di separare il set di dati (il livello di entità di dati) e TableAdapter (livello di accesso ai dati) in progetti discreti.

-   Il [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce le impostazioni per generare le classi di dati e DataContext in spazi dei nomi separato. In questo modo la separazione logica dell'accesso ai dati e i livelli di entità dati.

-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fornisce il <xref:System.Data.Linq.Table%601.Attach%2A> metodo che consente di raggruppare DataContext da livelli diversi in un'applicazione. Per ulteriori informazioni, vedere [a più livelli e applicazioni Remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Livello di presentazione
Il *livello presentazione* è il livello in cui gli utenti interagiscono con un'applicazione. Spesso contiene la logica dell'applicazione aggiuntivi anche. Componenti del livello presentazione tipiche includono:

-   Associazione di componenti, ad esempio dati di <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

-   Rappresentazioni di oggetti di dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità da utilizzare nel livello di presentazione.

Il livello di presentazione accede in genere il livello intermedio con un riferimento al servizio (ad esempio, un [servizi Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) applicazione). Il livello di presentazione non accede direttamente al livello dati. Il livello di presentazione comunica con il livello dati tramite il componente di accesso ai dati nel livello intermedio.

## <a name="middle-tier"></a>Livello intermedio
Il *livello intermedio* è il livello che il livello di presentazione e i livello dati utilizzato per comunicare tra loro. I componenti di livello intermedio tipiche includono:

-   Logica di business, ad esempio la convalida di regole e dati di business.

-   Componenti di accesso ai dati e logica, come illustrato di seguito:

    -   [Gli oggetti TableAdapter](create-and-configure-tableadapters.md) e [DataAdapter e DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

    -   Rappresentazioni di oggetti di dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità.

    -   Servizi delle applicazioni comuni, ad esempio l'autenticazione, autorizzazione e la personalizzazione.

Nella figura seguente mostra le funzionalità e tecnologie che sono disponibili in Visual Studio e il relativo utilizzo al livello intermedio di un'applicazione a più livelli.

![Componenti di livello intermedio](../data-tools/media/ntiermid.png "NtierMid") livello intermedio

Il livello intermedio in genere si connette al livello dati tramite una connessione dati. Questa connessione dati è in genere archiviata nel componente di accesso ai dati.

## <a name="data-tier"></a>Livello dati
Il *livello dati* è fondamentalmente il server che archivia dati di un'applicazione (ad esempio, un server che esegue [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]).

Nella figura seguente mostra le funzionalità e tecnologie che sono disponibili in Visual Studio e il relativo utilizzo un livello dati di un'applicazione a più livelli.

![Componenti di livello dati](../data-tools/media/ntierdatatier.png "ntierdatatier") livello dati

Il livello dati non sono accessibili direttamente dal client al livello presentazione. Il componente di accesso ai dati nel livello intermedio, invece, viene utilizzato per la comunicazione tra i livelli presentazione e dati.

## <a name="help-for-n-tier-development"></a>Guida per lo sviluppo di più livelli
Gli argomenti seguenti forniscono informazioni sull'utilizzo di applicazioni a più livelli:

[Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applicazioni a più livelli e remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)