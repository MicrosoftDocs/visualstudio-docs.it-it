---
title: L'accesso ai dati in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a7c7e031eb3fbe0330ab752882c8ac89eb7617bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="accessing-data-in-visual-studio"></a>L'accesso ai dati in Visual Studio

In Visual Studio, è possibile creare applicazioni che si connettono ai dati in qualsiasi prodotto di database o un servizio, in qualsiasi formato, in qualsiasi punto, in un computer locale, in una rete locale o in un cloud pubblico, privato o ibrido.

Le applicazioni in JavaScript, Python, PHP, Ruby o in C++, è necessario connettersi ai dati come se si trattasse di qualsiasi altro, ottenendo librerie e la scrittura di codice. Per le applicazioni .NET, Visual Studio fornisce strumenti che è possibile utilizzare per esplorare le origini dati, creare i modelli a oggetti per archiviare e gestire i dati in memoria e associare i dati per l'interfaccia utente. Microsoft Azure fornisce SDK per .NET, Java, Node.js, PHP, Python, Ruby e App per dispositivi mobili e gli strumenti di Visual Studio per la connessione al servizio di archiviazione Azure.

Gli elenchi seguenti illustrano alcune di molti sistemi di database e l'archiviazione che possono essere utilizzati da Visual Studio. Il [Microsoft Azure](https://azure.microsoft.com/) offerte sono servizi dati che includono il provisioning e amministrazione dell'archivio dati sottostante.  [Strumenti di Azure per Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) è un componente facoltativo che consente di lavorare con gli archivi di dati di Azure direttamente da Visual Studio. La maggior parte dei altri NoSQL e SQL database prodotti che sono elencati di seguito possono essere ospitata in un computer locale, in una rete locale o in Microsoft Azure in una macchina virtuale. In questo scenario, si è responsabili della gestione del database stesso.

**Microsoft Azure**

||||
|-|-|-|
|Database SQL|DB Cosmos Azure|Archiviazione (BLOB, tabelle, code, i file)|
|SQL Data Warehouse|Estensione Database SQL Server|StorSimple|

E molto altro ancora.

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, tra cui LocalDB Express e SQL Server|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

E molto altro ancora.

**NoSQL**

||||
|-|-|-|
|Cassandra Apache|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

E molto altro ancora.

Molti fornitori di database e terze parti supportano l'integrazione di Visual Studio da pacchetti NuGet. È possibile esplorare le offerte di nuget.org o tramite Gestione pacchetti NuGet in Visual Studio (**strumenti** > **Gestione pacchetti NuGet** > **Gestisci NuGet Pacchetti per la soluzione**). Altri prodotti del database è integrato con Visual Studio come estensione. È possibile esplorare queste offerte di Visual Studio Marketplace, passare a **strumenti**, **estensioni e aggiornamenti** e quindi selezionando **Online** nel riquadro sinistro della finestra di la finestra di dialogo. Per ulteriori informazioni, vedere [sistemi di database compatibili per Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Supporto esteso per SQL Server 2005 è terminato il 12 aprile 2016. Non c'è garanzia che gli strumenti di dati in Visual Studio 2015 e versioni successive continuano a funzionare con SQL Server 2005 dopo tale data. Per ulteriori informazioni, vedere il [annuncio di fine del supporto per SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Linguaggi .NET

Ogni accesso ai dati .NET, incluso in .NET Core, si basa su un set di classi che definisce un'interfaccia per l'accesso a qualsiasi tipo di origine dati, sia non relazionali e ADO.NET. Visual Studio è disponibili diversi strumenti e finestre di progettazione che funzionano con ADO.NET consentono di connettersi al database, modificare i dati e presentare i dati all'utente. La documentazione in questa sezione viene descritto come utilizzare questi strumenti. È anche possibile programmare direttamente usando gli oggetti comando ADO.NET. Per ulteriori informazioni su come chiamare direttamente le APIs ADO.NET, vedere [ADO.NET](/dotnet/framework/data/adonet/index).

Per la documentazione di accesso ai dati in modo specifico correlata ad ASP.NET, vedere [utilizzo dei dati](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sul sito ASP.NET. Per un'esercitazione sull'utilizzo di Entity Framework con ASP.NET MVC, vedere [Introduzione a Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

App universali di Windows Platform (UWP) in c# o Visual Basic è possibile utilizzare Microsoft Azure SDK per .NET per l'accesso di archiviazione di Azure e altri servizi di Azure. La classe Windows.Web.HttpClient consente la comunicazione con qualsiasi servizio RESTful. Per ulteriori informazioni, vedere [come connettersi a un server HTTP utilizzando Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Per l'archiviazione dei dati nel computer locale, l'approccio consigliato consiste nell'utilizzare SQLite, che viene eseguito nello stesso processo dell'app. Se è necessario un livello di mapping relazionale a oggetti (ORM), è possibile utilizzare Entity Framework. Per ulteriori informazioni, vedere [accesso ai dati](/windows/uwp/data-access/index) nel centro per sviluppatori Windows.

Se ci si connette ai servizi di Azure, assicurarsi di scaricare la versione più recente [strumenti di Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Provider di dati

Per un database essere utilizzabile in ADO.NET, deve avere un oggetto personalizzato *provider di dati ADO.NET* o altrimenti deve esporre un'interfaccia ODBC o OLE DB. Microsoft fornisce un [elenco di provider di dati ADO.NET](https://msdn.microsoft.com/data/dd363565) per i prodotti SQL Server, nonché i provider OLE DB e ODBC.

### <a name="data-modeling"></a>Modellazione dei dati

In .NET, sono disponibili tre opzioni per la modellazione e la modifica dei dati in memoria dopo avere recuperato da un'origine dati:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) la tecnologia Microsoft ORM preferita. È possibile utilizzare per la programmazione per dati relazionali come oggetti .NET di prima classe. Per le nuove applicazioni, deve essere la prima opzione predefinita quando è necessario un modello. È necessario supporto personalizzato dal provider ADO.NET sottostante.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) un mapping relazionale a oggetti di generazione precedente. Funziona anche per scenari meno complessi, ma non è più in fase di sviluppo attivo.

[Set di dati](../data-tools/dataset-tools-in-visual-studio.md) meno recente di tre tecnologie di modellazione. È progettato principalmente per lo sviluppo rapido di applicazioni "form su dati" in cui si sono non elaborazione enormi quantità di dati o l'esecuzione di query complesse o trasformazioni. Un oggetto set di dati è costituito da oggetti DataTable e DataRow logicamente di più oggetti .NET simili a oggetti di database SQL. Per le applicazioni relativamente semplici basate su origini dati SQL, i set di dati può essere ancora una buona scelta.

Non è necessario utilizzare uno qualsiasi di queste tecnologie. In alcuni scenari, in particolare quando le prestazioni sono critiche, è possibile utilizzare semplicemente un oggetto DataReader per leggere dal database e copiare i valori che è necessario in un oggetto di raccolta, ad esempio elenco\<T >.

## <a name="native-c"></a>C++ nativo

Le applicazioni C++ che si connettono a SQL Server devono utilizzare il [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) nella maggior parte dei casi. Se i server collegati, OLE DB è necessaria e per cui si utilizza il [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). È possibile accedere ad altri database usando [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o driver OLE DB direttamente. ODBC è l'interfaccia standard del database corrente, ma la maggior parte dei sistemi di database forniscono funzionalità personalizzate che non sono accessibili tramite l'interfaccia ODBC. OLE DB è una tecnologia di accesso ai dati COM legacy che è ancora supportata ma non consigliata per le nuove applicazioni. Per ulteriori informazioni, vedere [accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

I programmi C++ che utilizzano i servizi REST è possibile utilizzare il [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

I programmi C++ che utilizzano l'archiviazione di Microsoft Azure è possibile utilizzare il [Client di archiviazione di Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modellazione dei dati&mdash;Visual Studio non fornisce un livello ORM per C++. [ODB](http://www.codesynthesis.com/products/odb/) è una diffusa ORM open source per C++.

Per ulteriori informazioni sulla connessione ai database da app C++, vedere [Visual Studio data tools per C++](../data-tools/visual-studio-data-tools-for-cpp.md). Per ulteriori informazioni sulle tecnologie di accesso ai dati legacy Visual C++, vedere [accesso ai dati](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript in Visual Studio](/scripting/javascript/javascript-language-reference) è un costrutto di linguaggio per la compilazione di App multipiattaforma, le app UWP, servizi cloud, siti Web e App web. Per installare le librerie JavaScript preferite e prodotti del database, è possibile utilizzare Grunt, Bower, Gulp, npm e NuGet da Visual Studio. Connettersi ad archiviazione di Azure e servizi scaricando SDK dal [sito Web di Azure](https://azure.microsoft.com/). Edge.js è una libreria che si connette a server-side JavaScript (Node.js) a origini dati ADO.NET.

## <a name="python"></a>Python

Installare [Python supporto in Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) per creare applicazioni di Python. Documentazione di Azure presenta diverse esercitazioni sulla connessione ai dati, inclusi i seguenti:

- [Django e Database SQL in Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL in Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Lavorare con [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [file](/azure/storage/files/storage-python-how-to-use-file-storage), [code](/azure/storage/queues/storage-python-how-to-use-queue-storage), e [tabelle (database di installazione)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Argomenti correlati

[Piattaforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;viene fornita un'introduzione al cloud intelligente Microsoft, nonché il supporto per Internet of Things Cortana Analitica Suite.

[Archiviazione di Microsoft Azure](/azure/storage/)&mdash;archiviazione di Azure viene descritto e illustrato come creare applicazioni usando i BLOB di Azure, tabelle, code e i file.

[Database SQL di Azure](/azure/sql-database/)&mdash;viene descritto come connettersi al Database SQL di Azure, un database relazionale come servizio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;vengono descritti gli strumenti che semplificano la progettazione, esplorazione, test e distribuzione di applicazioni connesse a dati e database.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;descrive l'architettura ADO.NET e come utilizzare le classi ADO.NET per gestire i dati dell'applicazione e interagire con le origini dati e XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;viene descritto come creare applicazioni di dati che consentono agli sviluppatori di programmare in base a un modello concettuale anziché direttamente in un database relazionale.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;viene descritto come utilizzare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] per distribuire servizi dati nel web o in una rete intranet che implementano il [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)&mdash;contiene collegamenti ad argomenti che illustrano il funzionamento dei dati nelle soluzioni Office. Sono incluse informazioni sulla programmazione orientata agli schemi, la memorizzazione nella cache di dati e l'accesso ai dati sul lato server.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;descrive le funzionalità di query integrate nei linguaggi c# e Visual Basic e il modello comune per l'esecuzione di query su database relazionali, i documenti XML, i set di dati e raccolte in memoria.

[Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;illustra l'uso di funzionalità XML di .NET Framework di dati, debug XSLT, XML e l'architettura di Query XML.

[Documenti e dati XML](/dotnet/standard/data/xml/index)&mdash;viene fornita una panoramica a un set completo e integrato di classi che vengono usate con documenti XML e i dati in .NET Framework.
