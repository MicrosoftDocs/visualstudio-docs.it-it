---
title: "Attività GPU (paging) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01c61fb193ebc29c6eb76615e339327e71c24002
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-paging"></a>Attività GPU (paging)
I segmenti **Attività GPU (paging)** nella scheda Thread rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste di paging.  La lunghezza di un segmento rappresenta l'intervallo di tempo per cui la GPU ha elaborato un pacchetto di paging di accesso diretto alla memoria (DMA). In genere, i pacchetti di paging vengono associati al trasferimento di memoria tra la CPU e la GPU.  
  
 Quando si seleziona un segmento di paging GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato. Ciò include la quantità di tempo per cui è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto DMA e il tempo richiesto per elaborare il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Utilizzo](../profiling/utilization-view.md)