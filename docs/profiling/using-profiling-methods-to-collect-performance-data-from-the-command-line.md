---
title: Uso di metodi di profilatura per raccogliere dati di prestazioni tramite la riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2117fc729ef7e7190e5f1a46fe05d0d91daf63c6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Uso di metodi di profilatura per raccogliere dati di prestazioni tramite la riga di comando
La scelta degli strumenti e delle opzioni della riga di comando per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dipende da fattori come il tipo di applicazione sottoposta a profilatura, il metodo di profilatura da usare e il fatto che l'applicazione di destinazione sia scritta in codice nativo o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Questo argomento organizza gli argomenti relativi alle procedure della riga di comando in base al metodo di profilatura scelto.  
  
## <a name="in-this-topic"></a>Contenuto dell'argomento  
 [Uso del metodo di campionamento per raccogliere statistiche sulle prestazioni](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Uso del metodo di strumentazione per raccogliere dati di intervallo dettagliati](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Uso dei metodi di memoria .NET per raccogliere dati sulla durata degli oggetti e sull'allocazione di memoria](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Uso del metodo di concorrenza per raccogliere dati su attività dei thread e conflitti delle risorse](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Uso del metodo di campionamento per raccogliere statistiche sulle prestazioni  
 Il metodo di campionamento degli strumenti di profilatura raccoglie dati sulle prestazioni a intervalli specificati durante l'esecuzione di una profilatura. I dati di campionamento forniscono informazioni sui problemi di prestazioni associati alla CPU e rappresentano un metodo efficace per iniziare a esplorare le prestazioni di un'applicazione.  
  
 È possibile avviare il profiler e l'applicazione contemporaneamente oppure collegare il profiler a un'istanza di un'applicazione in esecuzione.  
  
|Attività|Tipo di applicazione di destinazione|  
|----------|-----------------------------|  
|**Avviare un'applicazione**|-   [Applicazioni autonome](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazioni .NET Framework autonome](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Applicazioni autonome native](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi nativi](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Uso del metodo di strumentazione per raccogliere dati di intervallo dettagliati  
 Il metodo di strumentazione degli strumenti di profilatura raccoglie dati sulle prestazioni da copie dei file binari dell'applicazione che contengono probe software per registrare le informazioni sulle prestazioni. I dati di strumentazione vengono raccolti all'inizio e alla fine di ogni funzione instrumentata e a ogni chiamata ad altre funzioni dalla funzione instrumentata. Il metodo di strumentazione è utile per l'individuazione dei problemi di prestazioni relativi alle attività di I/O, ad esempio l'uso del disco.  
  
 Creare il file binario instrumentato con lo strumento [VInstr.exe](../profiling/vsinstr.md). Dopo l'inizializzazione del profiler, i dati vengono raccolti automaticamente dai file binari instrumentati quando si esegue l'applicazione di destinazione.  
  
 **Tipo di applicazione di destinazione**  
  
-   [Componenti .NET Framework autonomi](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Componenti autonomi nativi](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)  
  
-   [Servizi .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Servizi nativi](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Uso dei metodi di memoria .NET per raccogliere dati sulla durata degli oggetti e sull'allocazione di memoria  
 Il metodo di memoria .NET degli strumenti di profilatura consente di raccogliere dati sull'allocazione di memoria di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e informazioni sulla durata degli oggetti in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 È possibile avviare l'applicazione di destinazione tramite il profiler, collegare il profiler a un'istanza di un'applicazione in esecuzione e creare versioni instrumentate dell'applicazione per raccogliere informazioni dettagliate sugli intervalli insieme ai dati sulla memoria di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Attività|Tipo di applicazione di destinazione|  
|----------|-----------------------------|  
|**Avviare un'applicazione**|-   [Applicazioni .NET Framework autonome](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazioni .NET Framework autonome](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentare moduli**|-   [Componenti .NET Framework autonomi](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Servizi .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Uso del metodo di concorrenza per raccogliere dati su attività dei thread e conflitti delle risorse  
 Il metodo di concorrenza degli strumenti di profilatura consente di raccogliere informazioni sui conflitti di risorse e dati sull'attività di thread e processi da applicazioni multithread.  
  
 È possibile avviare l'applicazione tramite il profiler oppure collegare il profiler a un'istanza di un'applicazione in esecuzione.  
  
|Attività|Tipo di applicazione di destinazione|  
|----------|-----------------------------|  
|**Avviare un'applicazione**|-   [Applicazione .NET Framework autonoma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione autonoma nativa](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazione .NET Framework autonoma](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione autonoma nativa](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura  
 L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)