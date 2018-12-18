---
title: Raccolta di statistiche sulle prestazioni tramite il campionamento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fea27cdfbcc843b30fbb4500dd9528df5b65c3d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Raccolta di statistiche sulle prestazioni tramite il campionamento

Per impostazione predefinita, il metodo di campionamento degli strumenti di profilatura di Visual Studio raccoglie informazioni di profilatura ogni 10.000.000 di cicli del processore, ovvero ogni centesimo di secondo circa in un computer da 1 GHz. Il metodo di campionamento è utile per individuare problemi relativi all'uso del processore e rappresenta il metodo consigliato nella maggior parte dei casi per iniziare l'analisi delle prestazioni.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

È possibile specificare il metodo di campionamento tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura fare clic su **Campionamento CPU (consigliato)**.
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Campionamento**.
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Campionamento**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo *Pagine delle proprietà***Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.

 Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo *Pagine delle proprietà***Sessione di prestazioni** quando si esegue la profilatura con il metodo di campionamento.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** aggiungere la raccolta dei dati di durata e allocazione di memoria .NET e specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [How to: Set Performance Data File Name Options](../profiling/how-to-set-performance-data-file-name-options.md) (Procedura: Impostare le opzioni relative ai nomi file dei dati di profilatura)|
|Nella pagina **Campionamento** modificare la frequenza di campionamento, scegliere come evento di campionamento un altro contatore delle prestazioni del processore anziché i cicli di clock o modificare entrambe le impostazioni.|- [How to: Choose Sampling Events](../profiling/how-to-choose-sampling-events.md) (Procedura: Scegliere eventi di campionamento)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare e l'ordine di avvio.|- [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Interazioni tra livelli** aggiungere le informazioni sulle chiamate ADO.NET ai dati raccolti con l'esecuzione della profilatura.|- [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Eventi di Windows** specificare uno o più eventi Event Tracing for Windows (ETW) da raccogliere con i dati di campionamento.|- [How to: Collect Event Tracing for Windows (ETW) Data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md) (Procedura: Raccogliere dati ETW (Event Tracing for Windows))|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [How to: Collect Windows Counter Data](../profiling/how-to-collect-windows-counter-data.md) (Procedura: Raccogliere i dati dei contatori Windows)|
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [How to: Specify the .NET Framework Runtime](../profiling/how-to-specify-the-dotnet-framework-runtime.md) (Procedura: Specificare il runtime di .NET Framework)|