---
title: Confronto di file di dati sulle prestazioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 734d0531cf1fbbbc2f7924cb1743cabf9e4a9578
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-performance-data-files"></a>Confronto di file di dati sulle prestazioni
La funzionalità di confronto tra file di dati offerta dagli strumenti per la profilatura consente di selezionare due file di rapporto con estensione vsp o vsps e generare un rapporto in cui siano indicate le differenze, la regressione delle prestazioni e i miglioramenti registrati tra una sessione di profilatura e l'altra.  
  
 In un rapporto di confronto di file di dati degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono messi a confronto i risultati di un'analisi in un file di dati per la profilatura e i risultati di un'analisi di base in un altro file di dati. È necessario che i due file di dati siano stati generati usando lo stesso metodo di profilatura. Il rapporto dei confronti analizzati viene salvato come file con estensione vsps.  
  
 Nella visualizzazione del rapporto di confronto i dati modificati vengono visualizzati sotto forma di tabella. La tabella contiene il delta o la modifica rispetto al valore di base. Il delta viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore risultato dalla nuova analisi.  
  
 I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione e tipi.  
  
 I dati di profilatura disponibili per il confronto includono le informazioni visualizzate nelle colonne. Per la definizione dei nomi di queste colonne, vedere [Performance Report Views](../profiling/performance-report-views.md) (Visualizzazioni dei rapporti di prestazioni).  
  
 È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dato nella visualizzazione tabella di confronto delle righe che non sono state modificate in base un valore specificato.  
  
## <a name="in-this-section"></a>In questa sezione  
 [How to: Compare Performance Data Files](../profiling/how-to-compare-performance-data-files.md) (Procedura: Confrontare i file di dati sulle prestazioni)