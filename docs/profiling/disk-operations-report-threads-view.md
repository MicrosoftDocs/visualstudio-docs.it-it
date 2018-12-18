---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.diskoperations
helpviewer_keywords: Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7fcef6ffd829ea999c1ed8d62d34083f5adab46
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
Nel rapporto delle operazioni su disco vengono descritte le operazioni I/O eseguite nei canali del disco.  
  
 Per ogni accesso al disco che avviene per conto del processo sottoposto a profilatura nell'intervallo di tempo attualmente visibile, vengono segnalate le informazioni seguenti:  
  
-   Nome e PID del processo che ha eseguito l'accesso al disco  
  
-   ID del thread che ha eseguito l'accesso al disco  
  
-   Nome del file al quale è stato eseguito l'accesso.  
  
-   Numero di letture per ogni file  
  
-   Numero di byte letti.  
  
-   Latenza di lettura in millisecondi  
  
-   Numero di operazioni di scrittura  
  
-   Numero di byte scritti  
  
-   Latenza di scrittura in millisecondi  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)