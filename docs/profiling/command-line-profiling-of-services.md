---
title: Profilatura dei servizi tramite riga di comando | Microsoft Docs
description: Informazioni su come usare la Strumenti di profilatura dalla riga di comando per raccogliere dati sulle prestazioni per i servizi Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dd77161184c5cb8be89ed522bbf06b6d80ca4bee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969503"
---
# <a name="command-line-profiling-of-services"></a>Profilatura dei servizi tramite riga di comando
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per i servizi Windows tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla riga di comando.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Raccogliere statistiche delle applicazioni:** usare il metodo di campionamento per raccogliere statistiche delle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni. | -   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni. | -   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che illustrano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection. | -   [Raccolta di dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Raccogli dati di concorrenza:** Usare il metodo di concorrenza per raccogliere dati sui conflitti di risorse e dati relativi alle attività dei thread che mostrano l'utilizzo della CPU, la contesa di thread, la migrazione dei thread, i ritardi di sincronizzazione, le aree di i/o sovrapposte e altri eventi di sistema. | -   [Raccogli dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone ADO.NET che il servizio ha eseguito nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Raccolta dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Attività correlate

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
