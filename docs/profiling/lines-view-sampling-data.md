---
title: 'Visualizzazione Righe: dati di campionamento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d08d090ad8e130e209af0d2057a065ed0bc474a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="lines-view---sampling-data"></a>Visualizzazione Righe: dati di campionamento
Nella visualizzazione Righe dei dati di campionamento sono elencati i dati delle prestazioni per le istruzioni eseguite durante la raccolta dei campioni nell'esecuzione della profilatura.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
 In un file di origine un'istruzione può occupare più di una riga in un file di origine e una singola riga può includere più di un'istruzione. Un'istruzione viene identificata in base agli elementi seguenti:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di origine in cui inizia l'istruzione.  
  
-   Carattere nella riga di origine in cui inizia l'istruzione.  
  
-   Riga di origine in cui termina l'istruzione.  
  
-   Carattere nella riga di origine in cui termina l'istruzione.  
  
 Nella colonna Nome riga è disponibile una concatenazione ordinabile dei dati dell'identificatore.  
  
 Per definizione, un'istruzione non chiama altre funzioni. Vengono quindi elencati solo valori esclusivi.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo che contiene la riga della funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la riga della funzione.|  
|**File di origine**|File di origine che contiene la riga della funzione.|  
|**Nome funzione**|Nome della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Indirizzo funzione**|Indirizzo iniziale della funzione.|  
|**Inizio riga di origine**|Numero di riga iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Fine riga di origine**|Numero di riga finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Inizio carattere di origine**|Offset del carattere iniziale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Fine carattere di origine**|Offset del carattere finale nel file di origine in corrispondenza del quale è stato raccolto il campione.|  
|**Nome riga**|Identificatore generato dal profiler della riga con la sintassi seguente:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number End`**,**`Character End`**]**|  
|**Esempi esclusivi**|Numero totale di campioni raccolti durante l'esecuzione della riga della funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione della profilatura che sono stati raccolti durante l'esecuzione della riga della funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Righe - Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)