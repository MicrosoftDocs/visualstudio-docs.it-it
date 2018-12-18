---
title: Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati
description: Il carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati in Visual Studio riunisce Python, R, F# e le rispettive distribuzioni di runtime, inclusa Anaconda.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs - vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: dc6d1548a95dd60f2dc05dc1a04953525c4b3b4a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="data-science-and-analytical-applications-workload"></a>Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati

Il carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, che può essere selezionato e installato tramite il programma di installazione di Visual Studio, riunisce tre linguaggi e le rispettive distribuzioni di runtime:

- [R e Microsoft R Client](../rtvs/index.md)
- [Python e Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)

![Carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati nel programma di installazione di Visual Studio](media/data-science-workload.png)

R e Python sono due dei principali dei linguaggi di scripting usati per le attività di data science. Entrambi i linguaggi sono facili da imparare e sono supportati da un nutrito ecosistema di pacchetti. Questi pacchetti soddisfano le esigenze di un'ampia gamma di scenari, ad esempio l'acquisizione e la pulizia dei dati, il training di modelli di dati, la distribuzione dei dati e i tracciati. F# è inoltre un linguaggio .NET potente e prima di tutto funzionale, adatto a una grande varietà di attività di elaborazione dati.

<!--Note link on the image because this one is large -->
[![Screenshot di Visual Studio con R, Python e F#](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Opzioni del carico di lavoro

Per impostazione predefinita, il carico di lavoro installa le opzioni seguenti, che è possibile modificare nella sezione di riepilogo per il carico di lavoro nel programma di installazione di Visual Studio:

- Supporto per il linguaggio F#
- Python:
  - Supporto linguaggio Python
  - [Anaconda3 a 64 bit](https://www.continuum.io) (Una distribuzione di Python che include librerie complete di data science e un interprete Python)
  - Supporto Web Python
  - Supporto modello Cookiecutter
- R:
  - Supporto linguaggio R
  - Supporto runtime per strumenti di sviluppo R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Interprete R di Microsoft supportato dalla community e completamente compatibile con librerie ScaleR per calcoli più veloci su singoli nodi o cluster. È anche possibile usare qualsiasi versione di R da [CRAN](https://cran.r-project.org/).)

Sebbene F# sia incluso in vari altri carichi di lavoro e Python abbia un carico di lavoro specifico, il carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati è l'unico al momento a includere R. È comunque possibile installare R anche in modo indipendente dal carico di lavoro. Nella scheda **Singoli componenti** nel programma di installazione selezionare le opzioni di R seguenti:

- **Attività di sviluppo >Supporto per il linguaggio R**
- **Attività di sviluppo > Microsoft R Client**
- **Compilatori, strumenti di compilazione e runtime > Supporto del runtime per strumenti di sviluppo R**

## <a name="sql-server-integration"></a>Integrazione con SQL Server

SQL Server supporta l'uso sia R che di Python per eseguire attività di analisi avanzate direttamente all'interno di SQL Server. Il supporto di R è incluso in SQL Server 2016 e versioni successive, mentre il supporto di Python è disponibile in SQL Server 2017 CTP 2.0 e versioni successive.

L'esecuzione del codice nella posizione in cui si trovano già i dati offre i vantaggi seguenti:

- **Nessuno spostamento dei dati**: anziché spostare dati dal database all'applicazione o al modello, è possibile compilare applicazioni R e Python nel database. Questa funzionalità consente di evitare le barriere a livello di sicurezza, conformità, governance e integrità, oltre a una serie di problemi simili correlati allo spostamento di grandi quantità di dati. È anche possibile usare set di dati che non potrebbero essere gestiti con la memoria di un computer client.

- **Semplicità di distribuzione**: quando un modello R o Python è pronto, per la sua distribuzione nell'ambiente di produzione è sufficiente incorporarlo in uno script T-SQL. Qualsiasi applicazione client SQL scritta in qualsiasi linguaggio può quindi sfruttare modelli e intelligence tramite una chiamata di stored procedure. Non sono necessarie integrazioni specifiche di R o Python.

- **Prestazioni e scalabilità di livello aziendale**: è possibile usare funzionalità avanzate di SQL Server come le tabelle in memoria e gli indici columnstore con le API scalabile ad alte prestazioni nei pacchetti RevoScaleR e RevoScalePy. Evitare gli spostamenti di dati significa anche evitare i vincoli di memoria client man mano che aumentano le dimensioni dei dati oppure se si desidera aumentare le prestazioni dell'applicazione.

- **Ampia estendibilità**: è possibile installare ed eseguire qualsiasi pacchetto R o Python open source tra i più recenti in SQL Server per realizzare applicazioni per l'apprendimento avanzato e AI su enormi quantità di dati in SQL Server. Installare un pacchetto in SQL Server è semplice come l'installazione di un pacchetto nel computer locale.

- **Disponibilità estesa senza costi aggiuntivi**: sono disponibili integrazioni R e Python in tutte le edizioni di SQL Server 2017 e versioni successive, inclusa l'edizione Express. (Il supporto di R è disponibile in SQL Server 2016 e versioni successive.)

Per sfruttare al meglio l'integrazione in SQL Server, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Elaborazione ed archiviazione dati** con l'opzione **SQL Server Data Tools**. Questa opzione abilita SQL IntelliSense, l'evidenziazione della sintassi e la distribuzione.

![Carico di lavoro Elaborazione ed archiviazione dati](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opzioni del carico di lavoro Elaborazione ed archiviazione dati](media/data-storage-workload-options.png)

Per ulteriori informazioni:

- [Uso di SQL Server ed R](../rtvs/sql-server.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/) (Analisi avanzata all'interno del database con R in SQL Server 2016)
- [Python in SQL Server 2017: enhanced in-database machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) (Python in SQL Server 2017: funzionalità avanzate di Machine Learning all'interno del database)

## <a name="additional-services-and-sdks"></a>Servizi aggiuntivi e SDK

Oltre ai componenti inclusi direttamente nel carico di lavoro Applicazioni analitiche e di analisi scientifica dei dati, per le esigenze di data science sono utili anche il servizio Azure Notebooks e Azure SDK per Python.

Azure SDK per Python semplifica l'uso e la gestione dei servizi di Microsoft Azure dalle applicazioni eseguite in Windows, Mac e Linux. Per altre informazioni, vedere [Azure SDK per Python](../python/azure-sdk-for-python.md).

Azure Notebooks (attualmente in anteprima) consente l'accesso online gratuito ai notebook di Jupyter in esecuzione nel cloud in Microsoft Azure. Il servizio include notebook di esempio in Python, R e F# per iniziare. Visitare [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Screenshot di Azure Notebooks con l'esempio Introduction to R (Introduzione a R)](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)