---
title: Grafico Attività GPU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41b7812db05b61c351346e5f0dcfa1bf4bd7bd1f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-graph"></a>Grafico dell'attività GPU
Il grafico Attività GPU nel visualizzatore di concorrenza visualizza il livello di attività di DirectX nel sistema, misurato in base al numero dei motori di DirectX usati nel tempo.  Il grafico non mostra gli specifici motori usati.  Un motore viene considerato in uso se sta elaborando una qualsiasi operazione GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Colori del grafico Attività GPU  
 Il verde indica l'uso dei motori di DirectX da parte del processo corrente.  
  
 Il grigio chiaro indica l'uso dei motori di DirectX da parte di altri processi nel sistema. Per ridurre l'uso dei motori di DirectX da parte di altri processi, ridurre il numero di altri processi in esecuzione nel sistema.  
  
 Il bianco indica la disponibilità dei motori inutilizzati di DirectX nel sistema. Tali motori sono disponibili per il processo se è possibile trovare ulteriori opportunità per sfruttarli. Alcuni motori possono essere usati solo per tipi specifici di attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Utilizzo](../profiling/utilization-view.md)