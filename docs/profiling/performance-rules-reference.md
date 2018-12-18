---
title: Tabella di riferimento delle regole di prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7707dad3e839ccc1bd306cb840555d1091e75a8a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="performance-rules-reference"></a>Tabella di riferimento delle regole di prestazioni
Le regole di prestazioni degli strumenti di profilatura forniscono informazioni e avvisi aggiuntivi sulle prestazioni dell'applicazione. Le regole di prestazioni consentono di analizzare in un'esecuzione di profilatura i dati raccolti da origini quali i contatori delle prestazioni dei processori e di Windows. I messaggi relativi alle regole vengono visualizzati nella finestra di output degli errori dell'ambiente di sviluppo integrato di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. I messaggi sono elencati con uno dei livelli di regole seguenti:  
  
|||  
|-|-|  
|**Erroree**|Poche regole generano messaggi di errore poiché la maggior parte dei problemi di prestazioni non sono effettivamente errori. Un messaggio di errore può indicare un errore nella raccolta dei dati di profilatura.|  
|**Avviso**|Gli avvisi indicano un'area dell'applicazione che potenzialmente può dare origine a problemi di prestazioni o che potrebbe essere ottimizzata.|  
|**Informazioni**|I messaggi di informazioni indicano che l'analisi di una condizione della regola non ha raggiunto la soglia per generare un messaggio di errore o che le informazioni nel messaggio sono utili ma non indicano un problema di prestazioni.|  
  
## <a name="in-this-section"></a>In questa sezione  
 [Regole di prestazioni in base all'ID](../profiling/performance-rules-by-id.md)  
  
 Le regole di prestazioni degli strumenti di profilatura sono organizzate in quattro categorie:  
  
|||  
|-|-|  
|[Regole di prestazioni per l'utilizzo di .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Regole che consentono di usare .NET Framework in modo efficiente.|  
|[Regole di prestazioni relative a memoria e paging](../profiling/memory-and-paging-performance-rules.md)|Regole che analizzano il comportamento di paging e Managed Memory dell'applicazione.|  
|[Regole di utilizzo degli strumenti di profilatura](../profiling/profiling-tools-usage-rules.md)|Regole che permettono di usare gli strumenti di profilatura in modo efficiente.|  
|[Regole di prestazioni relative al monitoraggio delle risorse](../profiling/resource-monitoring-performance-rules.md)|Messaggi di informazioni sull'uso del processore e della memoria in un'esecuzione di profilatura.|