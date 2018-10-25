---
title: Profilatura dei servizi tramite riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87ebf5e363a85c90a7a546491e76044c0c8c1791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813362"
---
# <a name="command-line-profiling-of-services"></a>Profilatura dei servizi tramite riga di comando
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per i servizi Windows tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla riga di comando.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Attività comuni

  
| Attività | Contenuto correlato |
| - | - |
| **Raccogliere statistiche delle applicazioni:** usare il metodo di campionamento per raccogliere statistiche delle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni. | -   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni. | -   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che illustrano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection. | -   [Raccogliere dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema. | -   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone ADO.NET che il servizio ha eseguito nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|