---
title: Aggiungere nuove connessioni
description: Aggiungere una connessione in Visual Studio a un database o a un servizio ed esplorare il contenuto e gli schemi del database usando Esplora server, Cloud Explorer o Esplora oggetti di SQL Server.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ddcc5dd06a4e71d445c94c860b2a3ab92429ab2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859385"
---
# <a name="add-new-connections"></a>Aggiungere nuove connessioni

È possibile testare la connessione a un database o a un servizio ed esplorare il contenuto e gli schemi del database usando **Esplora server**, **Cloud Explorer** o **Esplora oggetti di SQL Server**. La funzionalità di queste finestre si sovrappone a una certa misura. Le differenze di base sono:

- Esplora server

   Installato per impostazione predefinita in Visual Studio. Può essere usato per testare le connessioni e visualizzare SQL Server database, tutti gli altri database in cui è installato un provider ADO.NET e alcuni servizi di Azure. Vengono inoltre visualizzati oggetti di basso livello, ad esempio contatori delle prestazioni del sistema, log eventi e code di messaggi. Se un'origine dati non ha un provider ADO.NET, non verrà visualizzata qui, ma è comunque possibile usarla da Visual Studio tramite la connessione a livello di codice.

- Cloud Explorer

   Installare questa finestra manualmente come estensione di Visual Studio da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Fornisce funzionalità specializzate per l'esplorazione e la connessione ai servizi di Azure.

- Esplora oggetti di SQL Server

   Installato con SQL Server Data Tools e visibile dal menu **Visualizza** . Se non viene visualizzata, passare a **programmi e funzionalità** nel pannello di controllo, trovare Visual Studio, quindi selezionare **Cambia** per eseguire di nuovo il programma di installazione dopo aver selezionato la casella di controllo SQL Server Data Tools. Utilizzare **Esplora oggetti di SQL Server** per visualizzare i database SQL (se hanno un provider ADO.NET), creare nuovi database, modificare schemi, creare stored procedure, recuperare stringhe di connessione, visualizzare i dati e altro ancora. I database SQL che non hanno un provider ADO.NET installato non vengono visualizzati qui, ma è comunque possibile connettersi a essi a livello di codice.

## <a name="add-a-connection-in-server-explorer"></a>Aggiungere una connessione in Esplora server

Per creare una connessione al database, fare clic sull'icona **Aggiungi connessione** in **Esplora server** oppure fare clic con il pulsante destro del mouse su **Esplora server** nel nodo **connessioni dati** e scegliere **Aggiungi connessione**. Da qui è inoltre possibile connettersi a un database in un altro server, un servizio SharePoint o un servizio di Azure.

![Icona nuova connessione Esplora server](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Verrà visualizzata la finestra di dialogo **Aggiungi connessione** . Qui è stato immesso il nome dell'istanza di SQL Server database locale.

![Aggiungere una nuova connessione](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Modificare il provider

Se l'origine dati non è quella desiderata, fare clic sul pulsante **Cambia** per scegliere una nuova origine dati e/o un nuovo provider di dati ADO.NET. Il nuovo provider potrebbe richiedere le credenziali, a seconda di come è stato configurato.

![Modificare provider di dati AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testare la connessione

Dopo aver scelto l'origine dati, fare clic su **Test connessione**. Se l'operazione non riesce, sarà necessario risolvere i problemi in base alla documentazione del fornitore.

![Test della connessione](../data-tools/media/raddata-test-connection.png)

Se il test ha esito positivo, si è pronti per creare un' *origine dati*, ovvero un termine di Visual Studio che significa realmente un *modello di dati* basato sul database o sul servizio sottostante.

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
