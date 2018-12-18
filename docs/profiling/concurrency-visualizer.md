---
title: Visualizzatore di concorrenza | Microsoft Docs
ms.custom: 
ms.date: 07/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords: Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8b811b664df5d64a2235d641a6facf6cec889fe4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency-visualizer"></a>Visualizzatore di concorrenze
> [!NOTE]
>  Il Visualizzatore di concorrenza è un'estensione facoltativa di Visual Studio. Scaricare il Visualizzatore di concorrenza e gli strumenti di raccolta del visualizzatore di concorrenza dai collegamenti seguenti:  
>   
>  -   Scaricare l'estensione              [Visualizzatore di concorrenza per Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview).  
>  -   Scaricare l'estensione              [Visualizzatore di concorrenza per Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9).  
> -   Scaricare gli              [Strumenti di raccolta del visualizzatore di concorrenza per Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103).  
>   
>      L’ [utilità della riga di comando per il visualizzatore di concorrenza (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) consente di raccogliere tracce dalla riga di comando che possono essere visualizzate nel visualizzatore di concorrenza per Visual Studio 2015. Lo strumento può essere usato nei computer in cui non è installato Visual Studio.  
  
 Il Visualizzatore di concorrenza permette di esaminare l'esecuzione di app in multi-threading. Le visualizzazioni nel Visualizzatore di concorrenza forniscono dati grafici, tabulari e in formato testo che mostrano le relazioni temporali tra i thread nel programma e il sistema nel suo complesso. È possibile usare il Visualizzatore di concorrenza per individuare problemi relativi a colli di bottiglia delle prestazioni, sottoutilizzo della CPU, conflitto di thread, migrazione di thread, ritardi di sincronizzazione, aree di I/O sovrapposte e per ottenere altre informazioni. Nelle visualizzazioni sono disponibili dati su cui è possibile agire mediante il collegamento dell'output grafico agli stack di chiamate e al codice sorgente.  

> [!NOTE]
>  Il Visualizzatore di concorrenza non supporta progetti Web.  
  
 Il Visualizzatore di concorrenza si basa sulla funzionalità [Event Tracing for Windows](http://go.microsoft.com/fwlink/?LinkId=234579) .  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Utilization View](../profiling/utilization-view.md) (Visualizzazione Utilizzo)|Descrive come visualizzare e analizzare l'attività del sistema attraverso tutti i processori.|  
|[Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)|Descrive come analizzare le interazioni tra thread nel programma.|  
|[Cores View](../profiling/cores-view.md) (Visualizzazione Core)|Descrive come analizzare la migrazione di thread tra componenti principali.|  
|[Common Patterns for Poorly-Behaved Multithreaded Applications](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md) (Modelli comuni per applicazioni multithreading con comportamenti non validi)|Descrive vari modelli comuni e ne illustra l'uso nel Visualizzatore di concorrenza.|  
|[Sviluppo parallelo nel blog di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Fornisce suggerimenti e procedure consigliate per il Visualizzatore di concorrenza.|  
|[Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)|Fornisce informazioni di riferimento relative a report e visualizzazioni degli strumenti per la profilatura di Visual Studio.|  
|[Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md) (SDK del visualizzatore di concorrenza)|Spiega come eseguire la strumentazione del codice sorgente per visualizzare informazioni aggiuntive nel Visualizzatore di concorrenza.|  
|[Utilità della riga di comando del visualizzatore di concorrenza (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Spiega come usare l'utilità riga di comando del Visualizzatore di concorrenza (CVCollectionCmd.exe) per raccogliere ed elaborare le tracce sulle macchine che non hanno Visual Studio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)
