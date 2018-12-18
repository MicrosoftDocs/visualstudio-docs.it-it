---
title: 'Visualizzazione Righe: dati sui conflitti | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1465b9d8a14d5889bf856caa52b807ee2954cd0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="lines-view---contention-data"></a>Visualizzazione Righe: dati sui conflitti
Nella visualizzazione Righe dei dati sui conflitti sono elencati i dati sulle prestazioni per le istruzioni eseguite durante la raccolta dei campioni nell'esecuzione della profilatura. In un file di origine un'istruzione può occupare più di una riga in un file di origine e una singola riga può includere più di un'istruzione.  
  
 Un'istruzione viene identificata in base ai dati seguenti:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di origine in cui inizia l'istruzione.  
  
-   Carattere nella riga di origine in cui inizia l'istruzione.  
  
-   Riga di origine in cui termina l'istruzione.  
  
-   Carattere nella riga di origine in cui termina l'istruzione.  
  
 Nella colonna Nome riga è disponibile una concatenazione ordinabile dei dati dell'identificatore.  
  
 La tabella seguente descrive le colonne del rapporto Visualizzazione Righe.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo blocco esclusivo**|Quantità di tempo durante la quale è stata impedita l'esecuzione del codice nell'istruzione a causa di un evento di conflitto. Non è incluso il tempo di blocco nelle funzioni chiamate dall'istruzione.|  
|**% tempo blocco esclusivo**|Percentuale di tutto il tempo di blocco nel processo che costituiva il tempo di blocco esclusivo dell'istruzione.|  
|**Conflitti esclusivi**|Numero di volte in cui è stata impedita l'esecuzione del codice nell'istruzione a causa di un evento di conflitto. Non sono inclusi gli eventi di conflitto nelle funzioni chiamate dall'istruzione.|  
|**% conflitti esclusivi**|Percentuale di tutti gli eventi di conflitto nel processo che costituivano conflitti esclusivi di questa istruzione.|  
|**Indirizzo funzione**|Indirizzo della funzione contenente questa istruzione.|  
|**Nome funzione**|Nome completo della funzione contenente questa istruzione.|  
|**Tempo blocco inclusivo**|Tempo di blocco in questa istruzione e nelle funzioni chiamate nell'istruzione.|  
|**% tempo blocco inclusivo**|Percentuale di tutto il tempo di blocco nel processo che costituiva il tempo di blocco inclusivo dell'istruzione.|  
|**Conflitti inclusivi**|Numero di volte in cui è stata impedita l'esecuzione di questa istruzione e delle funzioni chiamate nell'istruzione.|  
|**% conflitti inclusivi**|Percentuale di tutti gli eventi di conflitto nel processo che costituivano conflitti inclusivi di questa istruzione.|  
|**Nome riga**|Identificatore generato dal profiler della riga. L'identificatore usa la sintassi seguente:`SourceFile`**;[**`LineNumberStart`**,**`CharacterStart`**]->;[**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**ID processo**|ID di processo (PID) del processo profilato.|  
|**Nome processo**|Nome del processo.|  
|**Inizio carattere di origine**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale inizia questa istruzione.|  
|**Fine carattere di origine**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale termina questa istruzione.|  
|**File di origine**|Nome del file di origine che contiene l'istruzione della funzione.|  
|**Inizio riga di origine**|Numero di riga del file di origine dove inizia questa istruzione.|  
|**Fine riga di origine**|Numero di riga del file di origine dove termina questa istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne delle visualizzazioni dei rapporti](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Righe](../profiling/lines-view.md)   
 [Visualizzazione Righe - Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)