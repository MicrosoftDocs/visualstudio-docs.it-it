---
title: Debug in tempo reale delle app di Azure ASP.NET - Visual Studio | Documenti Microsoft
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: e6ef3acf3373f03249b9ffa4456195f25b9991a3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debug in tempo reale delle app di Azure ASP.NET utilizzando il Debugger di Snapshot

Il Debugger Snapshot crea uno snapshot delle applicazioni in produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Snappoints e logpoints sono simili ai punti di interruzione, ma a differenza dei punti di interruzione, snappoints non interrompere l'applicazione quando raggiunto. In genere, l'acquisizione dello snapshot in un snappoint accetta 10-20 millisecondi. 

La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

- Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
- Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

Inoltre, il Debugger dello Snapshot è disponibile solo per Visual Studio 2017 Enterprise 15,5 o versione successiva e piani di servizio App di base o versione successiva. 

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare il Debugger di Snapshot
> * Impostare un snappoint e visualizzare uno snapshot
> * Impostare un logpoint

## <a name="start-the-snapshot-debugger"></a>Avviare il Debugger di Snapshot

1. Installare [2017 Enterprise di Visual Studio versione 15,5](https://www.visualstudio.com/downloads/) o versione successiva. Se si sta aggiornando un'installazione precedente di Visual Studio 2017, eseguire il programma di installazione Visual Studio e controllare il componente del Debugger di Snapshot del carico di lavoro di sviluppo ASP.NET e web.

2. Aprire il progetto che si desidera eseguire il debug di snapshot. 

    > [!IMPORTANT] 
    > Eseguire il debug dello snapshot, è necessario aprire la **stessa versione del codice sorgente** che viene pubblicato il servizio App di Azure. 

3. In Esplora risorse Cloud (**Vista > Cloud Explorer**), il servizio App di Azure il progetto viene distribuito e scegliere **collega Debugger Snapshot**.

   ![Avviare il debugger di snapshot](../debugger/media/snapshot-launch.png)

    La prima volta, si seleziona **collega Debugger Snapshot**, viene chiesto di installare l'estensione del sito Debugger Snapshot nel servizio App di Azure. Questa installazione richiede un riavvio del servizio App di Azure. 

   Visual Studio è in modalità di debug di snapshot.

    > [!NOTE]
    > L'estensione del sito di Application Insights supporta anche il debug dello Snapshot. Se viene visualizzato un messaggio di errore "estensione aggiornata del sito", vedere [risoluzione dei problemi noti per il debug dello snapshot e suggerimenti](../debugger/debug-live-azure-apps-troubleshooting.md) per l'aggiornamento dei dettagli.

   ![Modalità di debug di snapshot](../debugger/media/snapshot-message.png)

   Il **moduli** finestra viene visualizzato quando tutti i moduli sono caricati per il servizio App di Azure (scegliere **Debug / Windows / moduli** per aprire questa finestra).

   ![Controllare la finestra moduli](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Impostare un snappoint

1. Nell'editor di codice, fare clic sulla barra di navigazione a sinistra accanto a una riga di codice che si desidera impostare un snappoint. Verificare che si tratta di codice che verrà eseguita.

   ![Impostare un snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Fare clic su **Start Collection** per attivare il snappoint.  

   ![Attivare il snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Non è possibile eseguire durante la visualizzazione di uno snapshot, ma è possibile inserire più snappoints nel codice per seguire l'esecuzione in diverse righe di codice. Se si dispone di più snappoints nel codice, il Debugger Snapshot garantiscono che gli snapshot corrispondenti siano dalla stessa sessione dell'utente finale. Il Debugger Snapshot avviene anche se sono presenti molti utenti raggiunge l'app.

## <a name="take-a-snapshot"></a>Creare uno snapshot

Quando un snappoint è attivata, acquisisce uno snapshot ogni volta che viene eseguita la riga di codice in cui viene inserito il snappoint. L'esecuzione può essere causata da una richiesta effettiva sul server. Per forzare il snappoint riscontri, passare alla visualizzazione esplorazione del sito web e intraprendere le azioni necessarie che causano il snappoint da sottoporre a hit.

## <a name="inspect-snapshot-data"></a>Controllare i dati dello snapshot

1. Quando viene raggiunto il snappoint, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Per aprire questa finestra, scegliere **Debug / Windows / Mostra strumenti di diagnostica**.

   ![Aprire un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Fare doppio clic per aprire lo snapshot nell'editor di codice il snappoint.

   ![Controllare i dati dello snapshot](../debugger/media/snapshot-inspect-data.png)

   In questa vista è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, utilizzare il **variabili locali**, **controlla**, e **Stack di chiamate** windows e anche valutare le espressioni.

    Il sito Web è ancora in tempo reale e gli utenti finali non sono interessati. Un solo snapshot viene acquisito per snappoint per impostazione predefinita: dopo aver acquisito uno snapshot di snappoint viene disattivata. Se si desidera acquisire snapshot di un altro nel snappoint, è possibile attivare il snappoint indietro facendo **Aggiorna insieme**.

È anche possibile aggiungere ulteriori snappoints all'app e attivarli con il **Aggiorna insieme** pulsante.

**Serve aiuto?** Vedere il [problemi noti e risoluzione dei problemi](../debugger/debug-live-azure-apps-troubleshooting.md) e [domande frequenti relative al debug snapshot](../debugger/debug-live-azure-apps-faq.md) pagine.

## <a name="set-a-conditional-snappoint"></a>Impostare un snappoint condizionale

Se è difficile ricreare un determinato stato nell'app, è consigliabile se si consente l'utilizzo di un snappoint condizionale. Snappoints condizionale di evitare l'esecuzione di uno snapshot finché l'app passa allo stato desiderato, ad esempio quando una variabile contiene un valore specifico che si desidera controllare. È possibile impostare le condizioni di utilizzo di espressioni, filtri, o conteggio.

#### <a name="to-create-a-conditional-snappoint"></a>Per creare un snappoint condizionale

1. Fare doppio clic su un'icona di snappoint (la palla vuota) e scegliere **impostazioni**.

   ![Scegliere le impostazioni](../debugger/media/snapshot-snappoint-settings.png)

1. Nella finestra Impostazioni snappoint, digitare un'espressione.

   ![Digitare un'espressione](../debugger/media/snapshot-snappoint-conditions.png)

   Nell'illustrazione precedente, viene creato lo snapshot solo per il snappoint quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Impostare un logpoint

Oltre a creare uno snapshot quando viene raggiunto un snappoint, è inoltre possibile configurare un snappoint per registrare un messaggio (ossia, creare un logpoint). È possibile impostare logpoints senza dover ridistribuire l'applicazione. Logpoints vengono eseguiti quasi e non causare alcun impatto o effetti collaterali all'applicazione in esecuzione.

#### <a name="to-create-a-logpoint"></a>Per creare un logpoint

1. Fare doppio clic su un'icona di snappoint (esagono blu) e scegliere **impostazioni**.

1. Nella finestra Impostazioni snappoint selezionare **azioni**.

    ![Creare un logpoint](../debugger/media/snapshot-logpoint.png)

1. Nel campo messaggio, è possibile immettere il nuovo messaggio di log che si desidera registrare. È inoltre possibile valutare le variabili nel messaggio di log, inserirli all'interno delle parentesi graffe.

    Se si sceglie **inviare alla finestra di Output**, quando viene raggiunto il logpoint, viene visualizzato il messaggio nella finestra Strumenti di diagnostica.

    ![Dati Logpoint nella finestra di diagsession](../debugger/media/snapshot-logpoint-output.png)

    Se si sceglie **invia al registro applicazioni**, quando viene raggiunto il logpoint, il messaggio viene visualizzato in qualsiasi punto che è possibile visualizzare i messaggi da `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato spiegato come utilizzare il Debugger di Snapshot. È possibile leggere altre informazioni su questa funzionalità.

> [!div class="nextstepaction"]
> [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)
