---
title: Raccolta di dati di concorrenza di thread e processi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5314977b527358ebb3417423a20271c15a51130
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Raccolta di dati di concorrenza di thread e processi

Il metodo di profilatura della concorrenza degli strumenti di profilatura di Visual Studio consente di raccogliere dati sui conflitti di risorse, ovvero informazioni relative a tutti gli eventi di sincronizzazione a causa dei quali una funzione nell'applicazione sottoposta a profilatura deve attendere per accedere a una risorsa.

È possibile specificare il metodo di profilatura della concorrenza tramite una delle procedure seguenti:

- Nella prima pagina della procedura guidata di profilatura fare clic su **Concorrenza**.
- Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni fare clic su **Concorrenza**.
- Nell'elenco **Metodo** della barra degli strumenti di **Esplora prestazioni** fare clic su **Concorrenza**.

## <a name="common-tasks"></a>Attività comuni

È possibile specificare altre opzioni nella finestra di dialogo *Pagine delle proprietà***Sessioni prestazioni** della sessione di prestazioni. Per aprire questa finestra di dialogo:

- In **Esplora prestazioni**fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e quindi scegliere **Proprietà**.

Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo *Pagine delle proprietà***Sessioni prestazioni* quando si esegue la profilatura con il metodo di concorrenza.

|Attività|Contenuto correlato|
|----------|---------------------|
|Nella pagina **Generale** specificare i dettagli di denominazione per il file di dati di profilatura (con estensione vsp) generato.|- [How to: Set Performance Data File Name Options](../profiling/how-to-set-performance-data-file-name-options.md) (Procedura: Impostare le opzioni relative ai nomi file dei dati di profilatura)|
|Se il codice contiene più progetti Exe, nella pagina **Avvia** specificare l'applicazione da avviare.|- [How to: Specify the Binary to Start](../profiling/how-to-specify-the-binary-to-start.md) (Procedura: Specificare il file binario da avviare)|
|Nella pagina **Interazione tra livelli** aggiungere i dati delle chiamate ADO.NET per l'esecuzione della profilatura.|- [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|
|Nella pagina **Contatori Windows** specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilatura come contrassegni.|- [How to: Collect Windows Counter Data](../profiling/how-to-collect-windows-counter-data.md) (Procedura: Raccogliere i dati dei contatori Windows)|
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework da sottoporre a profilatura se i moduli dell'applicazione usano più versioni di questo. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.|- [How to: Specify the .NET Framework Runtime](../profiling/how-to-specify-the-dotnet-framework-runtime.md) (Procedura: Specificare il runtime di .NET Framework)|