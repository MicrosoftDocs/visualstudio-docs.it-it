---
title: Integrazione di SQL Server con R Tools per Visual Studio | Microsoft Docs
description: Visual Studio supporta la creazione e l'esecuzione di query SQL da R e possibili interazioni tra R e le stored procedure.
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
- SQL
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 4733d51d40b0aabffa108a1f99e4e492599b67c2
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="working-with-sql-server-and-r"></a>Uso di SQL Server ed R

L'ottimo supporto di Visual Studio per SQL Server consente agli esperti di dati di lavorare con database R e SQL attraverso la possibilità di creare ed eseguire query SQL e di usare le stored procedure.

> [!Note]
> Per usare SQL ed R contemporaneamente, è necessario aver installato SQL Server Data Tools:
> - Visual Studio 2017: eseguire il programma di installazione di Visual Studio e selezionare il carico di lavoro Elaborazione ed archiviazione dati, che include SQL Server Data Tools.
> - Visual Studio 2015: seguire le istruzioni in [Download SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) (Scaricare SQL Server Data Tools).

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) per una panoramica di SQL Server e R (3m 03s). |

## <a name="creating-and-running-sql-queries"></a>Creazione ed esecuzione di query SQL

RTVS supporta l'aggiunta di query SQL all'interno di progetti R, consentendo di sviluppare in modo iterativo query SQL in un contesto separato fino a quando non si ottengono i risultati voluti.

Per aggiungere un file di query SQL, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, scegliere **Aggiungi > Nuovo elemento...** e selezionare il tipo di file **Query SQL**:

![Aggiungere un elemento Query SQL a un progetto](media/sql-add-item.png)

Questo comando apre il file nell'editor Transact-SQL di Visual Studio, che è dotato di funzionalità IntelliSense complete per SQL e consente di eseguire query. Perché sia possibile usare queste funzionalità, è necessario connettersi a un database attraverso il pulsante di connessione sulla barra degli strumenti dell'editor o tentare di eseguire una query (CTRL+MAIUSC+E; questa combinazione di tasti funziona anche su una selezione). In entrambi i casi viene visualizzata la finestra di dialogo di connessione:

![Finestra di dialogo di connessione SQL](media/sql-connection-dialog.png)

Dopo che è stata stabilita la connessione, è possibile eseguire query e visualizzarne i risultati:

![Risultati di una query SQL](media/sql-query-results.png)

L'editor Transact-SQL supporta numerose funzionalità, ad esempio la visualizzazione del piano di esecuzione della query e il debugger di query.
Per altre informazioni, vedere [Utilizzare l'Editor Transact-SQL per modificare ed eseguire script](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Uso di stored procedure di SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 e versioni successive) consente di incorporare ed eseguire codice R da una stored procedure T-SQL. È possibile eseguire codice R da un computer SQL Server, usare dati restituiti da una query SQL e generare un set di risultati SQL che può essere elaborato da altro codice SQL o restituito al client.

Come descritto nelle sezioni seguenti, RTVS semplifica il processo di combinazione di codice SQL ed R all'interno di un'unica istruzione SQL, altrimenti macchinoso e a rischio di errore.

- [Aggiungere una connessione di database](#add-a-database-connection)
- [Scrivere e testare una stored procedure SQL](#write-and-test-a-sql-stored-procedure)
- [Pubblicare una stored procedure SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) per una panoramica di R e le stored procedure di SQL (6m 09s). |

### <a name="add-a-database-connection"></a>Aggiungere una connessione di database

1. Selezionare **Strumenti R > Dati > Aggiungi connessione di database...** per visualizzare la finestra di dialogo **Proprietà connessione**. In questa finestra viene specificato il nome dell'origine dati (SQL Server in questo caso), il nome del server, la modalità di autenticazione e il nome del database. Selezionare **Test connessione** per verificare l'input prima di chiudere la finestra di dialogo.

    ![Finestra di dialogo di connessione SQL](media/sql-connection-string-dialog.png)

1. Dopo avere verificato che la connessione sia valida, selezionare **OK**. Visual Studio genera una stringa di connessione denominata `dbConnection` in un nuovo file `settings.R`. RTVS origina (esegue) automaticamente questo file. È quindi possibile usare immediatamente la connessione da script R:

![File Settings.R SQL](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Scrivere e testare una stored procedure SQL

Per aggiungere una nuova stored procedure SQL, fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Nuovo elemento...**, selezionare **Stored Procedure SQL con R** dall'elenco di modelli, assegnare un nome al file (`StoredProcedure.R` in questo esempio) e selezionare **OK**.

RTVS crea tre file per la stored procedure, un file `.R` per il codice R, un file `.Query.sql` per il codice SQL e un file `.Template.sql` che combina i due file precedenti. Gli ultimi due sono visualizzati in Esplora soluzioni come elementi figlio del file `.R`:

![Visualizzazione espansa della stored procedure SQL con R in Esplora soluzioni](media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (in questo esempio) è il file in cui viene scritto il codice R. Il contenuto predefinito è:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

In parole semplici, il codice riceve un dataframe R denominato `InputDataSet` e restituisce i risultati in `OutputDataSet`, con il codice del modello che si limita a copiare l'input nell'output.

> [!Note]
> I nomi di questi dataframe sono controllati dai parametri `@input_data_1_name` e `@output_data_1_name` nella chiamata alla stored procedure di sistema `sp_execute_external_script`. Per altri dettagli sulla progettazione di questa convenzione di chiamata e per alcuni esempi d'uso, vedere [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Il rimanente codice generato all'interno di commenti è uno script di test di piccole dimensioni che usa il [pacchetto RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) per trasmettere un'istruzione SQL a SQL Server, eseguirla e recuperare il set di risultati come dataframe R. È possibile rimuovere il commento da questo codice di test per scrivere il codice R in modo interattivo a fronte del set di risultati ottenuto da SQL Server.

Nel file `StoredProcedure.Query.sql` è possibile scrivere e testare la query SQL che genera i dati per `InputDataSet`. Con questo file `.sql`, l'editor offre tutte le funzionalità di Transact-SQL consuete.

Quando si ritiene soddisfacente il codice SQL, integrarlo con il codice R in `StoredProcedure.R` trascinando il file `.sql` nell'editor aperto per il file `.R`. Nell'immagine seguente il file `StoredProcedure.Query.sql` è stato trascinato subito dopo la virgola in `sqlQuery(channel, )`:

![Lettura di un file SQL in una variabile stringa R](media/sql-reference-sql-file-from-r.png)

Come si può notare, questo semplice passaggio genera automaticamente il codice R che consente di aprire il file `.sql`, leggerne il contenuto in una stringa e passarlo al pacchetto RODBC per inviarlo a SQL Server.

A questo punto è possibile scrivere codice R in modo interattivo per modificare il dataframe `InputDataSet` in base alle esigenze. Tenere presente che è possibile selezionare codice R nell'editor e inviarlo alla [finestra interattiva](interactive-repl-for-r-in-visual-studio.md) semplicemente premendo CTRL + Invio.

`StoredProcedure.Template.sql`, infine, contiene il modello per la generazione della stored procedure SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- Il segnaposto `_RCODE_` viene sostituito dal contenuto di `StoredProcedure.R`.
- Il segnaposto `_INPUT_QUERY_` viene sostituito dal contenuto di `StoredProcedure.Query.sql`.
- Modificare la clausola `WITH RESULT SETS` per descrivere lo schema del set di risultati restituito dalla stored procedure. Identificare in modo specifico le colonne del dataframe `OutputDataSet` che si vogliono restituire al chiamante della stored procedure. 

Ad esempio, per la query seguente:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

è possibile usare la clausola `WITH RESULT SETS` seguente per specificare i tipi di dati dei valori restituiti:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Pubblicare una stored procedure SQL

1. Selezionare il comando di menu **R Tools > Dati > Pubblica con opzioni...**.
1. Nella finestra di dialogo visualizzata, modificare il valore di **Pubblica in:** in **Database**, specificare la destinazione e selezionare **Pubblica**. RTVS compila e pubblicha la stored procedure:

    ![Finestra di dialogo di pubblicazione di una stored procedure](media/sql-publish-with-options.png)

1. Per pubblicare tutte le stored procedure in un progetto, è possibile usare il comando **R Tools > Dati > Pubblica stored procedure**, anch'esso disponibile quando si fa clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.

> [!Tip]
> Se Esplora oggetti di SQL Server è aperto in Visual Studio, la stored procedure pubblicata viene visualizzata nella cartella **Programmabilità > Stored procedure** del database. È anche possibile eseguirla da Esplora oggetti facendo clic con il pulsante destro del mouse e selezionando **Esegui procedura**, o chiamandola in modo interattivo da una finestra Query `.sql`.
