---
title: 'Visualizzazione Puntatore all''istruzione: dati sui conflitti | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d6dcabe310743fee85c4560a0a37f029660bc90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Visualizzazione Puntatore all'istruzione: dati sui conflitti
Nella visualizzazione Puntatore all'istruzione dei dati sui conflitti sono elencati i dati per le istruzioni dell'assembly di cui è stata impedita l'esecuzione durante la profilatura.  
  
 La tabella seguente illustra i valori delle colonne nella visualizzazione Puntatore all'istruzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo blocco esclusivo**|Tempo di blocco in questa funzione.|  
|**% tempo blocco esclusivo**|Percentuale di tempo di blocco durante l'esecuzione dell'istruzione.|  
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati durante l'esecuzione dell'istruzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione della profilatura che si sono verificati durante l'esecuzione dell'istruzione.|  
|**Indirizzo funzione**|Indirizzo di memoria iniziale della funzione nel file binario caricato.|  
|**Nome funzione**|Nome della funzione contenente l'istruzione.|  
|**Indirizzo istruzione**|Indirizzo di memoria dell'istruzione nel file binario caricato.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo contenente l'istruzione.|  
|**Percorso modulo**|Percorso del modulo contenente l'istruzione.|  
|**ID processo**|ID di processo (PID) del processo profilato.|  
|**Nome processo**|Nome del processo.|  
|**Inizio carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale inizia questa istruzione.|  
|**Fine carattere di origine**|Offset del carattere nella riga del file di origine in corrispondenza del quale termina questa istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Inizio riga di origine**|Numero di riga del file di origine dove inizia questa istruzione.|  
|**Fine riga di origine**|Numero di riga del file di origine dove termina questa istruzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view.md)   
 [Visualizzazione Puntatore all'istruzione - Campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)