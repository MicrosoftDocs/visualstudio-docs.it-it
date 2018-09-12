---
title: Visualizzatore di concorrenza | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2a9e85f94e4c6baa06984b2b84e03c836eab53
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669025"
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
|[Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)|Descrive come analizzare le interazioni tra thread nel programma.|  
|[Cores View](../profiling/cores-view.md) (Visualizzazione Core)|Descrive come analizzare la migrazione di thread tra componenti principali.|  
|[Modelli comuni per applicazioni multithreading con comportamenti non validi](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Descrive vari modelli comuni e ne illustra l'uso nel Visualizzatore di concorrenza.|  
|[Sviluppo parallelo nel blog di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Fornisce suggerimenti e procedure consigliate per il Visualizzatore di concorrenza.|  
|[Performance Report Views](../profiling/performance-report-views.md)(Visualizzazioni dei rapporti di prestazioni)|Fornisce informazioni di riferimento relative a report e visualizzazioni degli strumenti per la profilatura di Visual Studio.|  
|[SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)|Spiega come eseguire la strumentazione del codice sorgente per visualizzare informazioni aggiuntive nel Visualizzatore di concorrenza.|  
|[Utilità della riga di comando del visualizzatore di concorrenza (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Spiega come usare l'utilità riga di comando del Visualizzatore di concorrenza (CVCollectionCmd.exe) per raccogliere ed elaborare le tracce sulle macchine che non hanno Visual Studio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
