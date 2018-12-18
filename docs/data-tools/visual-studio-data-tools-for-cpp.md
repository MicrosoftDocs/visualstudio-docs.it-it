---
title: Strumenti di dati di Visual Studio per C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4b258db15ddf879e8ef64e442082936d0d37e732
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="visual-studio-data-tools-for-c"></a>Strumenti di dati di Visual Studio per C++

C++ nativo può spesso fornire la velocità delle prestazioni quando si accede a origini dati. Tuttavia, dati gli strumenti per le applicazioni C++ in Visual Studio non avanzati, come nel caso di applicazioni .NET. Ad esempio, è Impossibile utilizzare le finestre di origini dati di trascinamento della selezione di origini dati in un'area di progettazione di C++. Se è necessario un livello relazionale a oggetti, è necessario scrivere la propria oppure usare un prodotto di terze parti.  Lo stesso vale per la funzionalità di associazione dati, sebbene le applicazioni che utilizzano la libreria Microsoft Foundation Class è possono utilizzare alcune classi di database, insieme a documenti e visualizzazioni, per archiviare i dati in memoria e la visualizza all'utente. Per ulteriori informazioni, vedere [accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

Per connettersi al database SQL, è possono utilizzare le applicazioni C++ native i driver ODBC e OLE DB e il provider ADO che sono inclusi in Windows. Questi possono connettersi a qualsiasi database che supporta tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornita per compatibilità con le versioni precedenti. Per ulteriori informazioni su queste tecnologie di dati, vedere [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx).

Per sfruttare le funzionalità personalizzate in SQL Server 2005 e versioni successive, usare il [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Il client nativo contiene anche il driver ODBC di SQL Server e il provider OLE DB per SQL Server in una libreria a collegamento dinamico (DLL). Applicazioni che usano API in codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server è supportata.  SQL Server Native Client viene installato con SQL Server Data Tools. La Guida di programmazione è qui: [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per la connessione a localDB mediante ODBC e SQL Native Client da un'applicazione C++

1.  Installare SQL Server Data Tools.

2.  Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in una nuova posizione.

3.  Utilizzare SQL Server Management Studio per collegare il file mdf decompresso a localDB. All'avvio di SQL Server Management Studio, connettersi a (localdb) \MSSQLLocalDB.

     ![Finestra di connessione SQL Server Management Studio](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS connettersi finestra di dialogo")

     Pulsante destro del mouse sul nodo del database locale nel riquadro a sinistra, quindi scegliere **collegamento**.

     ![SSMS Collega database](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS Collega database")

4.  Scaricare l'esempio di SDK di Windows di ODBC e decomprimerlo in una nuova posizione. Questo esempio mostra i comandi di base di ODBC utilizzata per connettersi a un database e di eseguire query e comandi. Maggiori informazioni su queste funzioni nel [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Quando si carica innanzitutto la soluzione (si trova nella cartella C++), Visual Studio offre aggiornare la soluzione per la versione corrente di Visual Studio. Scegliere **Sì**.

5.  Per utilizzare il client nativo, è necessario un file di intestazione e un file lib. Questi file contengono le funzioni e le definizioni specifiche di SQL Server, oltre a funzioni ODBC definite in SQL. In **progetto** > **proprietà** > **directory di VC + +**, aggiungere le seguenti directory di inclusione:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

E la directory di libreria:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Aggiungere le righe seguenti in odbcsql.cpp. Il #define impedisce irrilevanti definizioni OLE DB che si sta compilando.

    ```cpp
    #define _SQLNCLI_ODBC_
    #include <sqlncli.h>
    ```

    Si noti che il codice di esempio non effettivamente utilizzare tutte le funzionalità native client, pertanto i passaggi precedenti non sono necessari per compilare ed eseguire. Ma il progetto è ora configurato per l'utilizzo di questa funzionalità. Per ulteriori informazioni, vedere [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client).

7.  Specificare i driver da utilizzare nel sottosistema ODBC. L'esempio passa l'attributo di stringa di connessione del DRIVER in come un argomento della riga di comando. In **progetto** > **proprietà** > **debug**, aggiungere questo argomento di comando:

    ```cpp
    DRIVER="SQL Server Native Client 11.0"
    ```

8.  Premere F5 per compilare ed eseguire l'applicazione. Si noterà una finestra di dialogo del driver che viene richiesto di immettere un database. Immettere `(localdb)\MSSQLLocalDB`e controllare **Usa connessione Trusted**. Press **OK**. Verrà visualizzata una console con i messaggi che indicano una connessione riuscita. Verrà inoltre visualizzato un prompt dei comandi in cui è possibile digitare in un'istruzione SQL. La schermata seguente mostra un esempio di query e i risultati:

     ![Output di query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "output della query di esempio ODBC raddata")

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)