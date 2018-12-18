---
title: "Compatibilità di database di Visual Studio | Documenti Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 8fbe818e233c8bbdaf4431c70b8962baf43a2ed2
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemi di database compatibili per Visual Studio

Per sviluppare un'applicazione dati connessi in Visual Studio, in genere di installare il sistema di database nel computer di sviluppo locale e quindi distribuire l'applicazione e il database in un ambiente di produzione quando sono pronti. Visual Studio installa SQL Server Express LocalDB nel computer in uso come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro. Questa istanza di LocalDB è utile per lo sviluppo di applicazioni dati connessi in modo semplice e rapido.

Per un sistema di database deve essere accessibile da applicazioni .NET e per essere visibile nelle finestre di strumenti di Visual Studio dati deve avere un provider di dati ADO.NET. Un provider deve supportare Entity Framework se si prevede di utilizzare modelli di dati di entità nell'applicazione .NET. Molti provider sono disponibili tramite Gestione pacchetti NuGet o tramite Visual Studio Marketplace.

Se si utilizza l'API di archiviazione Azure, installare gli emulatori di archiviazione di Azure nel computer locale durante lo sviluppo per evitare i costi fino a quando non si è pronti a distribuire nell'ambiente di produzione. Per ulteriori informazioni, vedere [Usa l'emulatore di archiviazione di Azure per sviluppo e Testing](/azure/storage/common/storage-use-emulator).

Nell'elenco seguente include alcuni dei sistemi di database più comuni che possono essere usati nei progetti di Visual Studio. L'elenco non è completo. Per un elenco di fornitori di terze parti che offrono i provider di dati ADO.NET che consentono l'integrazione con strumenti di Visual Studio, vedere [provider di dati ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server è il database di Microsoft all'occhiello di offerta. SQL Server 2016 offre prestazioni elevate, la protezione avanzata e creazione di report completo e integrato e analitica. È disponibile nelle edizioni diverse progettate per usi diversi: da analitica aziendale altamente scalabile e ad alte prestazioni, utilizzare in un singolo computer. SQL Server Express è una versione completa di SQL Server progettato per la ridistribuzione e l'incorporamento.  LocalDB è una versione semplificata di SQL Server Express che non richiede alcuna configurazione e viene eseguito nel processo dell'applicazione. È possibile scaricare uno o entrambi i prodotti dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Molti degli esempi SQL in questa sezione utilizzare LocalDB di SQL Server. SQL Server Management Studio (SSMS) è un'applicazione di gestione di database autonomo che dispone di più funzionalità rispetto a quello fornito in Esplora oggetti di Visual Studio SQL Server. SQL Server Management Studio è possibile ottenere dal collegamento precedente.

## <a name="oracle"></a>Oracle

È possibile scaricare una versione a pagamento o gratuita del database Oracle dal [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) pagina. Per il supporto in fase di progettazione per Entity Framework e gli oggetti TableAdapter, è necessario il [strumenti di sviluppo Oracle per Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Altri prodotti Oracle ufficiale, tra cui Oracle Instant Client, sono disponibili tramite Gestione pacchetti NuGet.  È possibile scaricare gli schemi di esempio Oracle seguendo le istruzioni di [documentazione Online Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL è un sistema di database open source più comuni che è ampiamente utilizzato in aziende e siti Web. Download di MySQL, MySQL per Visual Studio e prodotti correlati sono [MySQL in Windows](http://www.mysql.com/why-mysql/windows/).  Alcuni fornitori offrono diverse estensioni di Visual Studio e le applicazioni di gestione autonoma per MySQL. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL è un sistema di database relazionale oggetto gratuita e open source. Per installarlo in Windows, è possibile scaricarlo dal [pagina di download PostgreSQL](http://www.postgresql.org/download/windows/).  È anche possibile compilare PostgreSQL dal codice sorgente.  Il sistema di base PostgreSQL include un'interfaccia del linguaggio C. Molte terze parti offrono pacchetti NuGet per l'utilizzo di PostgreSQL da applicazioni .NET.  È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) . Ad esempio viene eseguito il pacchetto più diffuso [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite è un motore di database SQL incorporato che viene eseguito nel processo dell'applicazione. È possibile scaricarlo dal [pagina di download di SQLite](http://www.sqlite.org/download.html). Sono disponibili anche molti pacchetti NuGet di terze parti per SQLite. È possibile esplorare le offerte in Gestione pacchetti NuGet (**strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**) .

## <a name="firebird"></a>Grande

Grande è un sistema di database SQL di open source. È possibile scaricarlo dal [pagina di download di grande](http://firebirdsql.org/en/downloads/). Un provider di dati ADO.NET è disponibile tramite Gestione pacchetti NuGet.

## <a name="see-also"></a>Vedere anche

[Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Come determinare la versione ed edizione di SQL Server e i relativi componenti](http://support.microsoft.com/kb/321185)