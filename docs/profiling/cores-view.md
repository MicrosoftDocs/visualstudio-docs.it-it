---
title: Visualizzazione Core | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aeac6a7322cb5f08751512f68797560d83ac4fd8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="cores-view"></a>Visualizzazione Core
La **visualizzazione Core** mostra il mapping dell'esecuzione dei thread ai core del processore logico (scegliere **Analizza** > **Visualizzatore di concorrenza** per avviare il visualizzatore di concorrenza). Se si scrivono applicazioni server, questa visualizzazione consente di ottimizzare le prestazioni della cache tramite l'affinità di thread o la gestione dei pool di thread. Consente anche di esaminare i casi in cui l'uso di affinità di thread potrebbe aver peggiorato il problema della migrazione tra core. La visualizzazione Core include due parti, un grafico e una legenda.  
  
 Il grafico visualizza i core logici sull'asse y e il tempo sull'asse x. Ogni thread nel grafico possiede un colore univoco in modo che sia possibile tenere traccia del movimento tra core nel tempo. È possibile filtrare i thread sul grafico selezionandoli nell'area della legenda.  
  
 Nell'area della legenda è presente una voce per ogni colore nel grafico. Ogni voce indica colore e nome del thread, numero di scambi di contesto tra core diversi, numero totale di scambi di contesto e percentuale di scambi di contesto tra core diversi. La legenda viene ordinata per numero di scambi di contesto tra core, in ordine decrescente. Vengono elencati solo i thread eseguiti durante l'intervallo di tempo visualizzato.  L'elenco viene aggiornato se si esegue lo zoom o la panoramica.  
  
## <a name="see-also"></a>Vedere anche  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)  (Visualizzatore di concorrenza)  
 [Utilization View](../profiling/utilization-view.md)  (Visualizzazione Uso)  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)