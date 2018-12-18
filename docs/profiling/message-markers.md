---
title: Marcatori messaggio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e341db6e1c83e268d7074c2b8afed307f6c0840f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="message-markers"></a>Marcatori di messaggi
Un marcatore del messaggio rappresenta l'output del log. Un messaggio è una stringa che viene emessa da un thread specifico in un momento specifico. È possibile esportare i messaggi in un file di testo per usarli con altri strumenti. È possibile posizionare il puntatore del mouse su un messaggio nel visualizzatore di concorrenza per visualizzare la stringa del messaggio. È anche possibile visualizzare tutti i marcatori del messaggio nel [rapporto Marcatori](../profiling/markers-report.md).  La figura seguente mostra un marcatore del messaggio.  
  
## <a name="message-aggregation-markers"></a>Marcatori di aggregazione di messaggi  
 Talvolta più messaggi si presentano a così poca distanza tra loro nel visualizzatore di concorrenza da non poter essere rappresentati singolarmente. In questo caso, viene visualizzato un *marcatore di aggregazione di messaggi* che rappresenta i messaggi sottostanti. Quando si posiziona il puntatore del mouse su una di queste icone, compare una descrizione comando che mostra il numero di messaggi sottostanti rappresentati. Per visualizzare i messaggi, fare zoom avanti.  Se viene fatto zoom avanti completamente e viene visualizzato ancora un marcatore di aggregazione, è possibile visualizzare i messaggi sottostanti nel [rapporto Marcatori](../profiling/markers-report.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)   
 [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md) (SDK del visualizzatore di concorrenza)