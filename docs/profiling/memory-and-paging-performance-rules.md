---
title: Regole di prestazioni relative a memoria e paging | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7949f19198aebe37b4a846cc37f274940415fb8e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="memory-and-paging-performance-rules"></a>Regole di prestazioni relative a memoria e paging
Le regole di prestazioni nelle categoria memoria e paging identificano l'attività di paging in un'esecuzione di profilatura che può influire sulla velocità di risposta e le prestazioni dell'applicazione.  
  
|||  
|-|-|  
|[DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza estremamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria. Questa regola viene attivata quando la quantità di attività di paging supera la soglia superiore della regola D0017.|  
|[DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza relativamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria.|