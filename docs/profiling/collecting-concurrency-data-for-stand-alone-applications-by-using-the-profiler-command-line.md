---
title: Raccolta di dati di concorrenza per applicazioni autonome tramite la riga di comando del profiler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f0003370525dafd29195473b2de0a02e18f3070
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Raccolta di dati di concorrenza per applicazioni autonome tramite la riga di comando del profiler
Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Avviare un'applicazione .NET Framework e sottoporre a profilatura dati di concorrenza** |-   [How to: Launch a .NET Framework Application to Collect Concurrency Data](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md) (Procedura: Avviare un'applicazione .NET Framework per raccogliere dati di concorrenza)|  
|**Avviare un'applicazione C/C++ e sottoporre a profilatura dati di concorrenza** |-   [How to: Launch a Native Application to Collect Concurrency Data](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md) (Procedura: Avviare un'applicazione nativa per raccogliere dati di concorrenza)|  
|**Connettere il profiler a un'applicazione .NET Framework in esecuzione**|-   [How to: Attach the Profiler to a .NET Framework Application to Collect Concurrency Data](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md) (Procedura: Connettere il profiler a un'applicazione .NET Framework per raccogliere dati di concorrenza)|  
|**Connettere il profiler a un'applicazione C/C++ in esecuzione**|-   [How to: Attach the Profiler to a Native Application and Collect Concurrency Data](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md) (Procedura: Connettere il profiler a un'applicazione nativa per raccogliere dati di concorrenza)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-stand-alone-applications"></a>Profilatura di applicazioni autonome  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccolta di dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Aggiunta di dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilatura di problemi di concorrenza  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura i servizi**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di concorrenza  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)