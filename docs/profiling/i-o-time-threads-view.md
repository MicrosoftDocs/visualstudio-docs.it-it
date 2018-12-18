---
title: Periodo di I/O (visualizzazione dei thread) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.io
helpviewer_keywords: Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: abea2c5ed246fe3463205894326a7f9611b56043
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="io-time-threads-view"></a>Tempo di I/O (visualizzazione Thread)
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come I/O. Ciò significa che un thread è in attesa del completamento di un'operazione di I/O. È possibile che il thread sia stato bloccato in un'API oppure da un tempo di attesa del kernel correlato all'I/O che il visualizzatore di concorrenza conteggia come I/O. Le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)