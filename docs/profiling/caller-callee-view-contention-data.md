---
title: 'Visualizzazione Chiamante/chiamato: dati sui conflitti | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 47e4f57ffac71d6fb4f1c3e8cd8176c80d9f002a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="caller--callee-view----contention-data"></a>Visualizzazione Chiamante/chiamato: dati sui conflitti
La visualizzazione Chiamante/chiamato consente di visualizzare informazioni sui conflitti per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie.  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni sui conflitti per la funzione selezionata. I valori includono tutti i conflitti di blocco per la funzione.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza i contributi individuali delle funzioni chiamanti (padre) i valori della funzione selezionata (corrente).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza informazioni sui conflitti per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Type**|Il contesto della funzione:<br /><br /> -   **0**: la funzione corrente<br />-   **1**: una funzione che chiama la funzione corrente<br />-   **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Tempo blocco esclusivo**|- Per la funzione corrente, il periodo in cui è stato impedito a questa funzione di eseguire codice nel corpo della funzione. Il tempo di blocco non è incluso nelle funzioni chiamate dalla funzione.<br />- Per una funzione chiamante, la parte del tempo di blocco esclusivo della funzione corrente usata quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il periodo in cui è stato impedito a questa funzione di eseguire il proprio codice quando la funzione è stata chiamata dalla funzione corrente. Il tempo di blocco non è incluso nelle funzioni figlio chiamate dalla funzione chiamata.|  
|**% tempo blocco esclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per questa funzione in questo contesto.|  
|**Conflitti esclusivi**|- Per la funzione corrente, il numero di volte in cui è stato impedito a questa funzione di eseguire codice nel corpo della funzione. Non sono inclusi i conflitti che si sono verificati in funzioni chiamate dalla funzione.<br />- Per una funzione chiamante, il numero di conflitti esclusivi della funzione corrente che si sono verificati quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il numero di volte in cui è stato impedito a questa funzione di eseguire codice nel corpo della funzione quando la funzione è stata chiamata dalla funzione corrente. Non sono inclusi i conflitti che si sono verificati in funzioni chiamate dalla funzione chiamata.|  
|**% conflitti esclusivi**|Percentuale del numero totale di conflitti nell'esecuzione della profilatura che rappresentano conflitti esclusivi per questa funzione in questo contesto.|  
|**Indirizzo funzione**|Indirizzo o token della funzione.|  
|**Nome funzione**|Nome completo della funzione.|  
|**Tempo blocco inclusivo**|- Per la funzione corrente, il periodo in cui è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate da questa funzione. Il tempo di blocco nelle funzioni chiamate dalla funzione corrente è incluso.<br />- Per una funzione chiamante, la parte del tempo di blocco inclusivo della funzione corrente usata quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il periodo in cui è stata impedita l'esecuzione di questa funzione o una delle funzioni chiamate dalla funzione quando questa funzione è stata chiamata dalla funzione corrente. Il tempo di blocco nelle funzioni chiamate dalla funzione chiamata è incluso.|  
|**% tempo blocco inclusivo**|Percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per questa funzione in questo contesto.|  
|**Conflitti inclusivi**|- Per la funzione corrente, il numero di volte in cui è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate dalla funzione. Sono inclusi i conflitti che si sono verificati in funzioni chiamate dalla funzione.<br />- Per una funzione chiamante, il numero di conflitti inclusivi della funzione corrente che si sono verificati quando questa funzione ha chiamato la funzione corrente.<br />- Per una funzione chiamata, il numero di volte in cui è stata impedita l'esecuzione di questa funzione o una delle funzioni chiamate dalla funzione quando questa funzione è stata chiamata dalla funzione corrente. Sono inclusi i conflitti che si sono verificati in funzioni chiamate dalla funzione chiamata.|  
|**% conflitti inclusivi**|Percentuale del numero totale di conflitti nell'esecuzione della profilatura che rappresentano conflitti esclusivi per questa funzione in questo contesto.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID processo (PID) del processo in cui si è verificato il conflitto.|  
|**Nome processo**|Nome del processo.|  
|**Nome funzione radice**|Nome della funzione corrente. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante/chiamato](../profiling/caller-callee-view.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)