---
title: Tempo di esecuzione (Visualizzazione thread) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bce4b4e5c0d4a9d4f66fade6b01044ac149968a0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="execution-time-threads-view"></a>Tempo di esecuzione (visualizzazione Thread)
Questi segmenti nella sequenza temporale della visualizzazione thread rappresentano il tempo di esecuzione, quando il thread è in esecuzione su un core logico nel sistema.  
  
 Le modifiche allo stato del thread vengono rilevate tramite eventi di cambio di contesto del kernel. Event Tracing for Windows (ETW) acquisisce gli stack dei campioni ogni millisecondo. In un segmento verde molto breve è possibile che non venga acquisito alcun campione. Di conseguenza, alcuni segmenti di breve esecuzione possono non visualizzare alcuno stack di chiamate.  
  
 Quando si fa clic su un segmento di esecuzione, il visualizzatore di concorrenza visualizza lo stack di campioni più vicino alla posizione di clic. La posizione dello stack di campioni viene indicata da una freccia di colore nero, o da un accento circonflesso, sopra la sequenza temporale e lo stack di campioni viene visualizzato nella scheda **Corrente**.  
  
 Per visualizzare un profilo di campionamento tradizionale per tutti i segmenti di esecuzione nella visualizzazione corrente, fare clic su **Esecuzione** in Profilo cronologia visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Rapporto profilo di esecuzione](../profiling/execution-profile-report.md)   
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione thread)