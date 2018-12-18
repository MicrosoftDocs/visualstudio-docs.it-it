---
title: 'Visualizzazione Chiamante/chiamato: dati di campionamento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81c10d85b9dc88115e7dbc57a03a6da4362fa945
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="caller--callee-view---sampling-data"></a>Visualizzazione Chiamante/chiamato: dati di campionamento
La visualizzazione Chiamante/chiamato consente di visualizzare informazioni di profilatura per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie.  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura per la funzione selezionata. Sono incluse tutte le chiamate campionate alla funzione.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza i contributi individuali delle funzioni chiamanti (padre) i valori della funzione selezionata (corrente).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza informazioni di profilatura per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Nome funzione**|Nome completo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Indirizzo funzione**|Indirizzo della funzione.|  
|**Type**|Il contesto della funzione:<br /><br /> -   **0**: la funzione corrente<br />-   **1**: una funzione che chiama la funzione corrente<br />-   **2**: una funzione chiamata dalla funzione corrente|  
|**Nome funzione radice**|Nome della funzione corrente.|  
|**Esempi inclusivi**|- Per la funzione corrente, il numero di esempi raccolti anche se era in esecuzione questa funzione o una delle relative funzioni figlio.<br />- Per una funzione chiamante, il numero di esempi inclusivi della funzione corrente raccolti quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il numero di esempi inclusivi di questa funzione raccolti quando la funzione corrente ha chiamato questa funzione.|  
|**% esempi inclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che costituivano esempi inclusivi di questa funzione.|  
|**Esempi esclusivi**|- Per la funzione corrente, il numero di esempi nell'esecuzione della profilatura raccolti quando era in corso l'esecuzione diretta di questa funzione, ovvero quando questa funzione era in cima allo stack di chiamate. Gli esempi raccolti durante l'esecuzione di funzioni figlio di questa funzione non sono inclusi nei conteggi esclusivi.<br />- Per una funzione chiamante, il numero di esempi esclusivi della funzione corrente raccolti quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il numero di esempi esclusivi di questa funzione raccolti quando la funzione corrente ha chiamato questa funzione.|  
|**% esempi esclusivi**|Percentuale di tutti gli esempi nell'esecuzione della profilatura che costituivano esempi esclusivi di questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)