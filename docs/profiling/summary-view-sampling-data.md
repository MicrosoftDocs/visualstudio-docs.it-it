---
title: 'Visualizzazione Riepilogo: dati di campionamento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c78ba45fda91650b5b7deb37ce9fd5dabbee6fb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="summary-view---sampling-data"></a>Visualizzazione Riepilogo: dati di campionamento
La visualizzazione Riepilogo mostra informazioni sulle funzioni che influiscono maggiormente sulle prestazioni in un'esecuzione della profilatura. Per altre informazioni, inclusa una descrizione degli elenchi dei collegamenti di notifica e dei rapporti, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
## <a name="timeline-graph"></a>Grafico della sequenza temporale  
 Il grafico della sequenza temporale nella visualizzazione Riepilogo mostra la percentuale di utilizzo del processore (CPU) dell'applicazione profilata nel periodo di profilatura. È possibile usare il grafico della sequenza temporale per filtrare la visualizzazione in base a un intervallo di tempo selezionato. Per altre informazioni, vedere [Procedura: Filtrare le visualizzazioni dei rapporti dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Percorso critico  
 In **Percorso critico** viene visualizzato il percorso di esecuzione in cui è stata raccolta la maggior parte dei campioni. È possibile fare clic su una funzione per attivare la visualizzazione Dettagli funzione per la funzione. Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione e scegliere una visualizzazione nell'elenco.  
  
 Il **Percorso critico** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione.|  
|**% esempi inclusivi**|Percentuale di tutti i campioni che si sono verificati durante l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.|  
|**% esempi esclusivi**|Percentuale di tutti i campioni che si sono verificati durante l'esecuzione di codice da parte della funzione nel corpo della funzione. Non sono inclusi i campioni raccolti nelle funzioni chiamate da questa funzione.|  
  
## <a name="functions-doing-most-individual-work"></a>Funzioni che svolgono più lavoro individuale  
 Nell'elenco **Funzioni che svolgono più lavoro individuale** vengono visualizzate le funzioni con il maggior numero di campioni esclusivi nell'esecuzione della profilatura. Un campione esclusivo viene assegnato a una funzione se il campione viene raccolto durante l'esecuzione del codice della funzione. Un campione esclusivo non viene assegnato a una funzione se il campione viene raccolto quando la funzione chiama un'altra funzione. Un numero elevato di campioni esclusivi indica che è stata impiegata una quantità significativa di tempo nella funzione stessa.  
  
 È possibile fare clic su una funzione per attivare la visualizzazione Dettagli funzione per la funzione. Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione e scegliere una visualizzazione nell'elenco.  
  
 L'opzione **Funzioni che svolgono più lavoro individuale** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione.|  
|**% esempi esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione di codice da parte della funzione nel corpo della funzione. Da questa percentuale sono esclusi i campioni raccolti durante l'esecuzione delle funzioni chiamate da questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-instrumentation-data.md)