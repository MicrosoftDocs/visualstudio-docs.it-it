---
title: Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3bd10121973c88e7a211aa741664b8ffb9b7bbc
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler
Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Connettersi a un servizio .NET in esecuzione**|-   [How to: Attach the Profiler to a .NET Service to Collect Concurrency Data](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md) (Procedura: Connettere il profiler a un servizio .NET per raccogliere dati di concorrenza)|  
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Connettersi a un servizio C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un servizio nativo per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-windows-services"></a>Profilatura di servizi Windows  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Collecting .NET Memory Data](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) (Raccolta di dati di memoria .NET)|  
  
### <a name="profiling-concurrency-data"></a>Profilatura di dati di concorrenza  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni autonome**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
|**Sottoporre a profilatura applicazioni Web ASP.NET**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di concorrenza  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)