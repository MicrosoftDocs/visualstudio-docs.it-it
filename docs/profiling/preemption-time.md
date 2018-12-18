---
title: Periodo di precedenza | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc117d84fb6d2b7076e4084c81f197ba3a464ab
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="preemption-time"></a>Tempo di annullamento
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Precedenza. Questa categoria implica che un thread viene disattivato per uno dei motivi seguenti:  
  
-   L'utilità di pianificazione lo ha sostituito con un thread con priorità maggiore.  
  
-   Il quantum di esecuzione del thread è scaduto e altri thread erano pronti per l'esecuzione.  
  
 Durante questo periodo, un thread è stato bloccato per un motivo di attesa del kernel che il visualizzatore di concorrenza conteggia come Precedenza. I segmenti con precedenza iniziano quando un thread viene escluso da un core logico e terminano quando tale thread riprende l'esecuzione.  
  
 La descrizione comando per un segmento con precedenza visualizza il nome del processo o del thread che ha causato il superamento. Tuttavia, ciò non implica che il processo o il thread con precedenza sia stato effettivamente eseguito per tutto il periodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)