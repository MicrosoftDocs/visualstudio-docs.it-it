---
title: Regole di utilizzo degli strumenti di profilatura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd5733d950a0b7f2bdd2c433fa7bb91e9e02ec1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-tools-usage-rules"></a>Regole di utilizzo degli strumenti di profilatura
Le regole delle prestazioni nella categoria di utilizzo degli strumenti di profilatura forniscono indicazioni per l'uso del profiler per una raccolta più efficiente dei dati.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll mancante](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|La profilatura dalla riga di comando potrebbe contenere dati incompleti per i file binari di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Il problema può essere causato dalla mancata impostazione delle variabili di ambiente corrette.|  
|[DA0003: Numero elevato di campioni del kernel](../profiling/da0003-many-kernel-samples.md)|Sono stati registrati molti campioni di profilatura che si sono verificati all'esterno dell'esecuzione del file binario di destinazione. Per raccogliere dati più accurati, è consigliabile ricorrere al metodo di strumentazione.|  
|[DA0004: Uso elevato del processore](../profiling/da0004-high-processor-usage.md)|I dati di profilatura indicano che i processori sono stati occupati in modo costante durante l'esecuzione della profilatura. Per raccogliere dati più accurati, è consigliabile ricorrere al metodo di campionamento.|  
|[DA0008: Numero ridotto di campioni raccolti](../profiling/da0008-few-samples-collected.md)|Il numero di campioni raccolti nell'esecuzione della profilatura non è sufficiente per essere statisticamente significativo. È consigliabile rieseguire la profilatura mantenendo l'applicazione in esecuzione per un periodo di tempo più lungo. È anche possibile considerare l'uso del metodo di strumentazione per la raccolta dei dati.|  
|[DA0026: Tempo di elaborazione CPU kernel eccessivo](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|L'esecuzione della profilatura in modalità kernel del processore ha richiesto un periodo di tempo notevole. Considerare l'uso del metodo di campionamento usando come metrica le chiamate di sistema anziché il tempo.|  
|[DA0029: Versione CLR non supportata](../profiling/da0029-unsupported-clr-version.md)|Il file binario profilato usa una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] non supportata dal profiler. I rapporti del profiler indicano che non è possibile risolvere i nomi dei simboli.|  
|[DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|È stato raccolto un numero significativo di chiamate ai metodi nello spazio dei nomi <xref:System.Data?displayProperty=fullName>. Per includere i dati sulle chiamate di database, prendere in considerazione la raccolta dei dati sull'interazione tra livelli nelle esecuzioni di profilatura.|