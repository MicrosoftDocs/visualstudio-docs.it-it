---
title: Controllo della raccolta di dati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 824a67ec2ce71a9b7810ace93001a942dc73e60e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="controlling-data-collection"></a>Controllo della raccolta di dati
Gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consentono di controllare quando i dati di profilatura vengono raccolti durante una sessione prestazioni e di specificare le funzioni che vengono profilate. In questa sezione viene descritto come avviare e arrestare la raccolta dei dati dalle finestre **Esplora prestazioni** e **Controllo raccolta dati** e come limitare gli oggetti per i quali vengono raccolti i dati di profilatura.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Avviare e interrompere la profilatura:** è possibile avviare la profilatura di un'applicazione all'avvio dell'applicazione, oppure collegare il profiler a un processo già in esecuzione. Quando l'applicazione di destinazione è in esecuzione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura chiudere l'applicazione di destinazione o disconnettere il profiler da un processo in esecuzione.|-   [How to: Start and End Performance Data Collection](../profiling/how-to-start-and-end-performance-data-collection.md) (Procedura: Iniziare e terminare la raccolta dei dati sulle prestazioni)<br />-   [How to: Attach and Detach Performance Tools to Running Processes](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) (Procedura: Connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione)<br />-   [How to: Pause and Resume Performance Data Collection](../profiling/how-to-pause-and-resume-performance-data-collection.md) (Procedura: Sospendere e riprendere la raccolta dei dati sulle prestazioni)|  
|**Configurare la profilatura della strumentazione per limitare i dati raccolti:** è possibile usare la configurazione della sessione prestazioni per limitare i dati raccolti durante le esecuzioni della profilatura che usano il metodo di strumentazione. È possibile includere o escludere specifici file con estensione dll, spazi dei nomi, classi e funzioni. È anche possibile escludere le funzioni che non soddisfano una soglia di dimensioni specificata.|-   [How to: Limit Instrumentation to Specific DLLs](../profiling/how-to-limit-instrumentation-to-specific-dlls.md) (Procedura: Limitare la strumentazione a specifiche DLL)<br />-   [How to: Limit Instrumentation to Specific Functions](../profiling/how-to-limit-instrumentation-to-specific-functions.md) (Procedura: Limitare la strumentazione a specifiche funzioni)<br />-   [How to: Exclude or Include Short Functions from Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md) (Procedura: Escludere o includere funzioni brevi nella strumentazione)|  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)