---
title: "Visualizzazione Puntatore all'istruzione: dati di campionamento | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 617ff8d4ed59aebefd3a4456ad36f148b1ee3de0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Visualizzazione Puntatore all'istruzione: dati di campionamento
Nella visualizzazione Puntatore all'istruzione dei dati di campionamento sono elencati i dati sulle prestazioni per le istruzioni dell'assembly eseguite direttamente durante la raccolta dei campioni nell'esecuzione della profilatura.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo contenente l'istruzione.|  
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Nome funzione**|Nome della funzione contenente l'istruzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|  
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Inizio carattere di origine**|Offset del carattere iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Fine carattere di origine**|Offset del carattere finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Indirizzo istruzione**|Indirizzo dell'istruzione nel file binario caricato.|  
|**Esempi esclusivi**|Numero totale di campioni raccolti durante l'esecuzione dell'istruzione.|  
|**% esempi esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione dell'istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Puntatore all'istruzione - Campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)