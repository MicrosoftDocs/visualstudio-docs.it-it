---
title: Aggiungere nuove connessioni
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 28633fcc4c744269a2a90cc72c8136afbda6f561
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="add-new-connections"></a>Aggiungere nuove connessioni

Verificare la connessione a un database o un servizio è esplorare i contenuti del database e schemi, utilizzando **Esplora Server**, **Cloud Explorer**, o **Esplora oggetti di SQL Server**. La funzionalità di queste finestre si sovrappone in parte. Le differenze di base sono:

- Esplora server

   Installato per impostazione predefinita in Visual Studio. Può essere utilizzato per testare le connessioni e visualizzare i database di SQL Server, nessun altro database a cui è installato un provider ADO.NET e alcuni servizi di Azure. Mostra anche gli oggetti di basso livello, ad esempio i contatori delle prestazioni di sistema, log eventi e le code di messaggi. Se un'origine dati non dispone di alcun provider ADO.NET, non verranno visualizzati qui, ma sarà comunque possibile utilizzarla da Visual Studio tramite la connessione a livello di codice.

- Cloud Explorer

   Installare manualmente questa finestra come un'estensione di Visual Studio selezionando **strumenti**, **estensioni e aggiornamenti**, **Online**, **Visual Studio Markeplace**. Fornisce funzionalità specializzate per l'esplorazione e la connessione a servizi di Azure.

- Esplora oggetti di SQL Server

   Installato con SQL Server Data Tools e visibile nel **vista** menu. Se non viene visualizzato non esiste, passare a **programmi e funzionalità** nel Pannello di controllo, individuare Visual Studio e quindi selezionare **modifica** per eseguire nuovamente il programma di installazione dopo aver selezionato la casella di controllo per SQL Server Data Tools. Utilizzare **Esplora oggetti di SQL Server** ai database SQL di visualizzazione (se dispongono di un provider ADO.NET), creare nuovi database, modificare gli schemi, creare stored procedure, recuperare le stringhe di connessione, visualizzare i dati e altro ancora. I database SQL di cui non è installato alcun provider ADO.NET non verranno visualizzati qui, ma non è possibile connettersi a essi a livello di codice.

## <a name="add-a-connection-in-server-explorer"></a>Aggiungere una connessione in Esplora Server

Per creare una connessione al database, fare clic sul **Aggiungi connessione** icona in **Esplora Server**, oppure fare clic **Esplora Server** sul **dati Connessioni** nodo e selezionare **Aggiungi connessione**. Da qui, è anche possibile connettersi a un database in un altro server, un servizio di SharePoint o un servizio di Azure.

![Icona nuova connessione di Esplora server](../data-tools/media/raddata-server-explorer-new-connection-icon.png "icona nuova connessione Esplora Server raddata")

Verrà visualizzata la **Aggiungi connessione** la finestra di dialogo. In questo caso, è stato immesso il nome dell'istanza di LocalDB di SQL Server.

![Aggiungi nuova connessione](../data-tools/media/raddata-add-new-connection-dialog.png "raddata Aggiungi nuova finestra di dialogo di connessione")

## <a name="change-the-provider"></a>Modificare il provider

Se non si desidera l'origine dati, scegliere il **modifica** pulsante per selezionare una nuova origine dati e/o un nuovo provider di dati ADO.NET. Il nuovo provider potrebbero essere richieste le credenziali, a seconda di come è stato configurato.

![Modificare il Provider di dati AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata Provider di dati di modifica AD0.NET")

## <a name="test-the-connection"></a>Testare la connessione

Dopo aver scelto l'origine dati, fare clic su **Test connessione**. Se non viene completato, è necessario risolvere i problemi in base alla documentazione del fornitore.

![Test connessione](../data-tools/media/raddata-test-connection.png "raddata Test connessione")

Se il test ha esito positivo, si è pronti a creare un *origine dati*, che è un termine di Visual Studio che in realtà indica un *modello di dati* basato sul database o del servizio sottostante.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)