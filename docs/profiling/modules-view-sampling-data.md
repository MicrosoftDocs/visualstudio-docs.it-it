---
title: 'Visualizzazione Moduli: dati di campionamento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 053b1ea5903675f60d59c3574f982f2461e39e4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="modules-view---sampling-data"></a>Visualizzazione Moduli: dati di campionamento
Nella visualizzazione Moduli dei dati di campionamento vengono visualizzati i dati sulle prestazioni raggruppati in base ai moduli campionati nei dati di profilatura. Ogni modulo è la radice di una struttura gerarchica. Le funzioni campionate del modulo sono elencate sotto il nodo del modulo.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
 Se era in corso l'esecuzione della funzione quando sono stati raccolti i campioni, ovvero la funzione si trovava in cima allo stack di chiamate, le righe di codice sorgente e gli indirizzi delle istruzioni in esecuzione sono elencati sotto il nodo della funzione. Poiché i dati vengono raccolti per una riga di codice sorgente o per un puntatore all'istruzione durante l'esecuzione della riga o dell'istruzione, i valori inclusivi ed esclusivi sono sempre gli stessi sia per i dati di riga che per quelli di istruzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome del modulo, della funzione, del numero di riga o dell'indirizzo del puntatore all'istruzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo che contiene la funzione, la riga o il puntatore all'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il modulo, la funzione, la riga o il puntatore all'istruzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Campioni inclusivi**|- Per una funzione, il numero di campioni in cui era in corso l'esecuzione di questa funzione o di una funzione chiamata da questa funzione, ovvero il numero di campioni dello stack di chiamate che contenevano questa funzione.<br />- Per un modulo, il numero di campioni in cui era in esecuzione almeno una funzione del modulo.<br />- Per una riga o istruzione, il numero di campioni in cui era in esecuzione questa riga o istruzione.|  
|**% esempi inclusivi**|- Per una funzione o un modulo, la percentuale di tutti i campioni nell'esecuzione della profilatura che costituivano campioni inclusivi di questa funzione o di questo modulo.<br />- Per una riga o istruzione, la percentuale di tutti i campioni nell'esecuzione di profilatura in cui era in esecuzione questa riga o istruzione.|  
|**Esempi esclusivi**|- Per una funzione, il numero di campioni dello stack di chiamate in cui era in corso l'esecuzione diretta di questa funzione, ovvero il numero di campioni in cui questa funzione era in cima allo stack di chiamate.<br />- Per un modulo, la somma dei campioni esclusivi delle funzioni nel modulo.<br />- Per una riga o istruzione, il numero di campioni in cui era in esecuzione questa riga o istruzione.|  
|**% esempi esclusivi**|- Per una funzione o un modulo, la percentuale di tutti i campioni nell'esecuzione della profilatura che costituivano campioni esclusivi di questa funzione o di questo modulo.<br />- Per una riga o istruzione, la percentuale di tutti i campioni nell'esecuzione di profilatura in cui era in esecuzione questa riga o istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Moduli - Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli - Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione moduli](../profiling/modules-view-instrumentation-data.md)