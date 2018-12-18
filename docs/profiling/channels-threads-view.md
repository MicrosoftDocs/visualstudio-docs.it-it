---
title: Canali (visualizzazione Thread) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.channelnames
helpviewer_keywords: Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 74d0796b1d2d3ecbe3ff08cc1eb4cfe79153f738
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="channels-threads-view"></a>Canali (visualizzazione Thread)
Nel visualizzatore di concorrenza appaiono quattro tipi di canali: canali di thread, canali di disco, canali di indicatore e canali GPU.  
  
## <a name="thread-channels"></a>Canali di thread  
 Un canale di thread indica lo stato del thread, in base al colore, per un solo thread. Quando si posiziona il mouse sul nome del canale, viene visualizzata la funzione di avvio per il thread specificato. Il visualizzatore di concorrenza rileva diversi tipi di thread. I tipi più comuni sono descritti nella tabella seguente.  
  
|||  
|-|-|  
|Thread principale|Il thread che ha avviato l'applicazione.|  
|Thread di lavoro|Thread creato dal thread principale dell'applicazione.|  
|Thread processo di lavoro CLR|Thread di lavoro creato da Common Language Runtime (CLR).|  
|Supporto debugger|Thread di lavoro creato dal debugger di Visual Studio.|  
|Thread ConcRT|Thread creato dal runtime di concorrenza di Microsoft.|  
|Thread GDI|Thread creato da GDIPlus.|  
|Thread OLE/RPC|Thread creato come thread di lavoro RPC.|  
|Thread RPC|Thread creato come thread RPC.|  
|Thread Winsock|Thread creato come thread Winsock.|  
|Pool di thread|Thread creato dal pool di thread RPC.|  
  
## <a name="disk-channels"></a>Canali di disco  
 I canali di disco corrispondono alle unità fisiche nel computer. Poiché esistono canali separati per le operazioni di lettura e scrittura per ogni unità fisica nel sistema, ogni unità ha due canali. I numeri di disco corrispondono ai nomi dei dispositivi Kernel. Un canale di disco viene visualizzato solo se era presente attività nel disco.  
  
## <a name="marker-channels"></a>Canali di indicatore  
 I canali di indicatore corrispondono agli eventi generati dall'applicazione e dalle librerie usate dalla stessa. Ad esempio, Task Parallel Library, Parallel Patterns Library e C++ AMP generano eventi che vengono visualizzati come indicatori. Ogni canale di indicatore è associato un ID di thread, che viene visualizzato accanto alla descrizione del canale. L'ID identifica il thread che ha generato l'evento. La descrizione del canale include il nome del provider ETW (Event Tracing for Windows) che ha generato gli eventi. Se il canale visualizza eventi dall'[SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md), viene visualizzato anche il nome della serie.  
  
## <a name="gpu-channels"></a>Canali GPU  
 I canali GPU visualizzano informazioni sull'attività di DirectX 11 nel sistema.  Ogni motore DirectX associato alla scheda grafica ha un canale separato.  I singoli segmenti rappresentano il tempo trascorso per elaborare un pacchetto DMA.  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)