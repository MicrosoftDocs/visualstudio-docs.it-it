---
title: Tempo di gestione della memoria | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.paging
helpviewer_keywords: Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 08c111b89ee265820d314150ff28096eb9bf5d2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="memory-management-time"></a>Tempo di gestione della memoria
Questi segmenti nella sequenza temporale sono associati a tempi di blocco categorizzati come gestione della memoria. Ciò implica che un thread è bloccato da un evento associato a un'operazione di gestione della memoria quale il paging. Durante questo periodo, un thread è stato bloccato in un'API o in uno stato del kernel che il visualizzatore di concorrenza calcola come gestione della memoria. Si tratta di eventi come il paging e l'allocazione di memoria.  
  
 Esaminare gli stack di chiamate e i rapporti di profilo associati per comprendere meglio i motivi alla base della categorizzazione dei blocchi come gestione della memoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)