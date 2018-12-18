---
title: Aggiornare i file con estensione mdf | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b0e12b716d98920ea2d358a43116042ca54ffd2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="upgrade-mdf-files"></a>Aggiornare i file con estensione mdf

In questo argomento vengono descritte le opzioni per l'aggiornamento di un file di database (con estensione mdf) dopo aver installato una versione più recente di Visual Studio. Include istruzioni per le attività seguenti:

- Aggiornamento di un file di database per l'utilizzo di una versione più recente di SQL Server Express LocalDB

- Aggiornamento di un file di database per l'utilizzo di una versione più recente di SQL Server Express

- Utilizzare un file di database in Visual Studio, ma mantenere la compatibilità con una versione precedente di SQL Server Express o LocalDB

- Assicurarsi di SQL Server Express il motore di database predefinito

È possibile utilizzare Visual Studio per aprire un progetto che contiene un file di database (con estensione mdf) che è stato creato con una versione precedente di SQL Server Express o LocalDB. Tuttavia, per continuare a sviluppare il progetto in Visual Studio, è necessario disporre di tale versione di SQL Server Express o LocalDB installato nello stesso computer di Visual Studio oppure è necessario aggiornare il file di database. Se si aggiorna il file di database, non sarà in grado di accedervi tramite le versioni precedenti di SQL Server Express o LocalDB.

Potrebbe anche essere richiesto per eseguire l'aggiornamento di un file di database che è stato creato tramite una versione precedente di SQL Server Express o LocalDB se la versione del file non è compatibile con l'istanza di SQL Server Express o LocalDB attualmente installata. Per risolvere il problema, Visual Studio verrà richiesto di aggiornare il file.

> [!IMPORTANT]
> È consigliabile eseguire il backup del file di database prima di eseguirne l'aggiornamento.

> [!WARNING]
> Se si aggiorna un file con estensione mdf che è stato creato in LocalDB 2014 (V12) a 32 bit a LocalDB 2016 (V13) o versione successiva, non sarà in grado di aprire nuovamente il file nella versione a 32 bit del database locale.

Prima di aggiornare un database, considerare i seguenti criteri:
  
-   Se si desidera lavorare sul progetto in una versione precedente sia una versione più recente di Visual Studio, non eseguire l'aggiornamento.  
  
-   Non effettua l'aggiornamento se l'applicazione verrà utilizzata in ambienti che utilizzano SQL Server Express anziché LocalDB.  
  
-   Non effettua l'aggiornamento se l'applicazione usa le connessioni remote, perché non accetti LocalDB.  
  
-   Non aggiornare l'applicazione si basa su Internet Information Services (IIS).  
  
-   Se si desidera testare le applicazioni di database in un ambiente sandbox, ma non si desidera amministrare un database, prendere in considerazione l'aggiornamento.  
  
### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Per eseguire l'aggiornamento di un file di database per utilizzare la versione del database locale
  
1.  In **Esplora Server**, selezionare il **Connetti al Database** pulsante.  
  
2.  Nel **Aggiungi connessione** finestra di dialogo specificare le informazioni seguenti:  
  
    -   **Origine dati**:`Microsoft SQL Server (SqlClient)`  
  
    -   **Nome del server**:  
  
        -   Utilizzare la versione predefinita: `(localdb)\MSSQLLocalDB`.  Si specificherà ProjectV12 o ProjectV13, a seconda di quale versione di Visual Studio sia installata e quando si è creata la prima istanza di LocalDB. Il **MSSQLLocalDB** nodo **Esplora oggetti di SQL Server** Mostra la versione fa riferimento.  
  
        -   Per usare una versione specifica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13`, dove V12 è 2014 LocalDB e V13 2016 LocalDB.  
  
    -   **Collegare un file di database**: il percorso fisico del file mdf primario.  
  
    -   **Nome logico**: il nome che si desidera utilizzare con il file.  
  
3.  Selezionare il pulsante **OK** .  
  
4.  Quando richiesto, selezionare il **Sì** pulsante per aggiornare il file.  
  
    Il database viene aggiornato, è collegato al motore di database LocalDB e non è più compatibile con la versione precedente del database locale.  
  
È inoltre possibile modificare una connessione a SQL Server Express per usare LocalDB aprendo il menu di scelta rapida per la connessione e quindi selezionando **Modifica connessione**. Nel **Modifica connessione** finestra di dialogo, modificare il nome del server per `(LocalDB)\MSSQLLocalDB`. Nel **proprietà avanzate** finestra di dialogo, assicurarsi che **istanza utente** è impostato su **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Per eseguire l'aggiornamento di un file di database per utilizzare la versione di SQL Server Express  
  
1.  Dal menu di scelta rapida per la connessione al database, selezionare **Modifica connessione**.  
  
2.  Nel **Modifica connessione** la finestra di dialogo, seleziona il **avanzate** pulsante.  
  
3.  Nel **proprietà avanzate** la finestra di dialogo, seleziona il **OK** pulsante senza modificare il nome del server.  
  
    Il file di database viene aggiornato in base alla versione corrente di SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Per utilizzare il database in Visual Studio, ma mantenere la compatibilità con SQL Server Express  
  
-   In Visual Studio, aprire il progetto senza l'aggiornamento.  
  
    -   Per eseguire il progetto, selezionare il **F5** chiave.  
  
    -   Per modificare il database, aprire il file con estensione mdf in **Esplora**, espandere il nodo in **Esplora Server** per funzionare con il database.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Eseguire SQL Server Express il motore di database predefinito  
  
1.  Nella barra dei menu, selezionare **strumenti**, **opzioni**.  
  
2.  Nel **opzioni** finestra di dialogo espandere il **Database Tools** opzioni e quindi selezionare **connessioni dati**.  
  
3.  Nel **nome dell'istanza di SQL Server** testo, specificare il nome dell'istanza di SQL Server Express o LocalDB che si desidera utilizzare. Se l'istanza non è stato denominato, specificare `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.  
  
4.  Selezionare il pulsante **OK** .  
  
    SQL Server Express è il motore di database predefinito per le applicazioni.

## <a name="see-also"></a>Vedere anche

[Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)
