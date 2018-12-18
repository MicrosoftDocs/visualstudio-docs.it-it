---
title: Configurazione di sessioni di prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85155bb357f808b477d9d6041c16cdc2d0f3681b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="configuring-performance-sessions"></a>Configurazione di sessioni di prestazioni
Usando gli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile raccogliere un'ampia gamma di dati sulle prestazioni per un numero elevato di tipi di applicazioni. In questa sezione viene illustrato come usare le proprietà della Creazione guidata sessione di prestazioni della sessione di prestazioni e del file binario di destinazione per configurare gli strumenti di profilatura per raccogliere i dati di interesse. Le proprietà di configurazione degli strumenti per la profilatura possono essere usate anche per controllare quanti dati vengono raccolti in un'esecuzione di profilatura. Per altre informazioni, vedere [Controlling Data Collection](../profiling/controlling-data-collection.md) (Controllo della raccolta di dati).  
  
> [!NOTE]
>  In molti casi l'uso delle proprietà della Creazione guidata sessione di prestazioni è un metodo efficace per raccogliere dati di profilatura. Per altre informazioni, vedere [Beginners Guide to Performance Profiling](../profiling/beginners-guide-to-performance-profiling.md) (Guida per principianti alla profilatura delle prestazioni) e [Getting Started with Performance Tools](../profiling/getting-started-with-performance-tools.md) (Introduzione agli strumenti di profilatura).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Impostare le opzioni di profilatura di base:** è necessario configurare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] per usare il server dei simboli Microsoft. Ciò consente di avere accesso ai simboli, come ad esempio i nomi di parametri e funzioni, per la versione corrente di Windows e per altre applicazioni Microsoft. È anche possibile specificare altre opzioni generali prima di avviare una sessione di profilatura, ad esempio autorizzazioni di sistema per gli strumenti di profilatura e i nomi dei file di dati di profilatura.|-   [How to: Reference Windows Symbol Information](../profiling/how-to-reference-windows-symbol-information.md) (Procedura: Fare riferimento alle informazioni sui simboli di Windows)<br />-   [How to: Serialize Symbol Information](../profiling/how-to-serialize-symbol-information.md) (Procedura: Serializzare le informazioni sui simboli)<br />-   [How to: Set the Current Session](../profiling/how-to-set-the-current-session.md) (Procedura: Impostare la sessione corrente)<br />-   [How to: Set Permissions](../profiling/how-to-set-permissions.md) (Procedura: Impostare le autorizzazioni)<br />-   [How to: Set Performance Data File Name Options](../profiling/how-to-set-performance-data-file-name-options.md) (Procedura: Impostare le opzioni relative ai nomi file dei dati di profilatura)|  
|**Specificare i dati che si vuole raccogliere:** le procedure per configurare una sessione di profilatura variano a seconda del tipo di applicazione di destinazione che si vuole profilare e del tipo di dati sulle prestazioni che si vuole raccogliere.|-   [How to: Choose Collection Methods](../profiling/how-to-choose-collection-methods.md) (Procedura: Scegliere un metodo di raccolta)<br />-   [Collecting Performance Statistics by Using Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md) (Raccolta di statistiche sulle prestazioni tramite il campionamento)<br />-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) (Raccolta di dati di durata e allocazione di memoria .NET)<br />-   [Collecting Detailed Timing Data by Using Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md) (Raccolta di dati di intervallo dettagliati tramite la strumentazione)<br />-   [How to: Profile JavaScript Code in Web Pages](../profiling/how-to-profile-javascript-code-in-web-pages.md) (Procedura: Profilare codice JavaScript nelle pagine Web)<br />-   [Collecting Thread and Process Concurrency Data](../profiling/collecting-thread-and-process-concurrency-data.md) (Raccolta di dati di concorrenza di thread e processi)<br />-   [Collecting Additional Performance Data](../profiling/collecting-additional-performance-data.md) (Raccolta di dati aggiuntivi relativi alle prestazioni)|  
|**Impostare le opzioni di configurazione avanzata:** quando si esegue la profilatura delle applicazioni .NET Framework che caricano più versioni di common language runtime (CLR), è possibile specificare di quale versione eseguire la profilatura. Quando in una sessione di prestazioni si hanno più file con estensione exe, è possibile impostare l'ordine di avvio dei file binari.|-   [How to: Specify the .NET Framework Runtime](../profiling/how-to-specify-the-dotnet-framework-runtime.md) (Procedura: Specificare il runtime di .NET Framework)<br />-   [How to: Specify the Binary to Start](../profiling/how-to-specify-the-binary-to-start.md) (Procedura: Specificare il file binario da avviare)|  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Controlling Data Collection](../profiling/controlling-data-collection.md) (Controllo della raccolta di dati)  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)