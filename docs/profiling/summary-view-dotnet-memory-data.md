---
title: 'Visualizzazione Riepilogo: dati di memoria .NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f5f821f936ffa8e157eb61e5daab25d1421c6899
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935216"
---
# <a name="summary-view---net-memory-data"></a>Visualizzazione Riepilogo: dati di memoria .NET
La visualizzazione Riepilogo riporta informazioni sui tipi e sulle funzioni .NET che hanno allocato la quantità di memoria maggiore e sui tipi che sono stati creati più frequentemente in un'esecuzione della profilatura. Per altre informazioni, inclusa una descrizione dei collegamenti di notifica e degli elenchi di report, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Grafico della sequenza temporale  
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra l'utilizzo del processore (CPU) per l'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni report dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funzioni che allocano molta memoria  
 Elenca le funzioni che hanno allocato il maggior numero di byte di memoria nell'esecuzione della profilatura.  
  
|Colonna|Description|  
|------------|-----------------|  
|**Name**|Nome della funzione.|  
|**% byte**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che sono stati allocati da questa funzione o da una funzione figlio chiamata da questa funzione.|  
  
## <a name="types-with-most-memory-allocated"></a>Tipi con molta memoria allocata  
 Elenca i tipi per cui è stato allocato il maggior numero di byte di memoria nell'esecuzione della profilatura.  
  
|Colonna|Description|  
|------------|-----------------|  
|**Name**|Nome del tipo.|  
|**% byte**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che sono stati allocati per questo tipo.|  
  
## <a name="types-with-most-instances"></a>Tipi con molte istanze  
 Elenca i tipi creati più frequentemente nell'esecuzione della profilatura. stato  
  
|Colonna|Description|  
|------------|-----------------|  
|**Name**|Nome del tipo.|  
|**% istanze**|Percentuale del numero totale di oggetti .NET creati nell'esecuzione della profilatura corrispondenti a istanze di questo tipo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Riepilogo: dati di campionamento](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo: dati di strumentazione](../profiling/summary-view-instrumentation-data.md)