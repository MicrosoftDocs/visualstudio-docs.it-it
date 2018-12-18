---
title: 'Visualizzazione Riepilogo: visualizzazione dei conflitti tra le risorse | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed1db5bd560c32cdb40ddc728b3ede63c70dbc88
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="summary-view---resource-contention-view"></a>Visualizzazione Riepilogo: visualizzazione dei conflitti tra le risorse
La visualizzazione Riepilogo riporta informazioni sugli eventi dell'applicazione in cui un thread o un processo in attesa di accedere a una risorsa è stato sospeso.  
  
 Per altre informazioni, inclusa una descrizione degli elenchi dei collegamenti di notifica e dei rapporti, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Grafico della sequenza temporale  
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra il numero di eventi di conflitto dell'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni dei rapporti dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Risorse con più conflitti  
 In **Risorse con più conflitti** sono elencate le risorse dell'applicazione che hanno causato la maggior parte degli eventi di conflitto. È possibile fare clic sul nome di una risorsa per visualizzare la visualizzazione Conflitti. La visualizzazione Conflitti fornisce una sequenza temporale dettagliata dei conflitti tra le risorse in base al thread.  
  
 L'opzione **Risorse con più conflitti** include i dati seguenti per ogni risorsa.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della risorsa.|  
|**% conflitti**|Percentuale di tutti gli eventi di conflitto nei dati di profilatura che rappresentano conflitti per questa risorsa.|  
  
## <a name="most-contended-thread"></a>Thread con più conflitti  
 In **Thread con più conflitti** sono elencati i thread dell'applicazione in cui si è verificato il maggior numero di eventi di conflitto. È possibile fare clic sul nome di un thread per visualizzare la visualizzazione Conflitti che fornisce una sequenza temporale dettagliata dei conflitti tra le risorse in base al thread.  
  
 L'opzione **Thread con più conflitti** include i dati seguenti per ogni thread.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID**|L'identificatore del thread.|  
|**Name**|Nome del processo proprietario del thread.|  
|**% conflitti**|Percentuale di tutti gli eventi di conflitto nei dati di profilatura che rappresentano conflitti per questa risorsa.|