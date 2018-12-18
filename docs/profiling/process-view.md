---
title: Visualizzazione Processo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86e8a11f55edd2f7a04498b81ec6b8713876f718
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="process-view"></a>Visualizzazione Processo
La visualizzazione Processo visualizza i dati di profilatura per i processi e i thread eseguiti durante l'esecuzione della profilatura.  
  
 I processi sono elencati per nome. I thread sono elencati come nodi figlio del processo che li ha creati. Il nome dei thread viene definito in base alla funzione che ha definito il thread o all'etichetta **[ntdll.dll]** in assenza di simboli disponibili.  
  
 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse sulla visualizzazione e quindi scegliere **Aggiungi/Rimuovi colonne**. È anche possibile ordinare i dati facendo clic su un nome di colonna. Per altre informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
 Le colonne della visualizzazione Processo sono le stesse per i dati generati usando i metodi di campionamento e strumentazione e per i dati che includo i dati sulla memoria .NET. Nella tabella seguente sono descritti i valori delle colonne.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID univoco**|Identificatore generato dal profiler univoco per il processo o il thread.|  
|**ID**|Identificatore generato dal sistema per il processo o il thread.|  
|**Name**|Nome del processo o del thread.|  
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|  
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)   
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)