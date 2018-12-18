---
title: 'Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5a80233a6c1aaed56770e0ec2bb6733a800ce06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET
La visualizzazione Chiamante/chiamato consente di visualizzare i dati di profilatura della memoria .NET per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie.  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura della memoria relative alla funzione selezionata. Sono incluse tutte le chiamate campionate alla funzione.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza la quantità del valore della funzione selezionata (corrente) generato da chiamate da parte della funzione chiamante (padre).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza dati di profilatura di memoria per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Fare doppio clic su una riga della funzione chiamante o chiamata per rendere quella riga la funzione corrente.  
  
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
|**Type**|Il contesto della funzione:<br /><br /> **0**: la funzione corrente<br /><br /> **1**: una funzione che chiama la funzione corrente<br /><br /> **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Livello**|Profondità della funzione nell'albero delle chiamate. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Allocazioni inclusive**|- Per la funzione corrente, il numero di oggetti allocati dalla funzione nell'esecuzione della profilatura. Il numero include gli oggetti creati nelle funzioni chiamate.<br />- Per una funzione chiamante, il numero delle allocazioni inclusive della funzione corrente generate da chiamate da questa funzione.<br />- Per una funzione chiamata, il numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione corrente. Il numero include le allocazioni effettuate dalle funzioni chiamate dalla funzione chiamata.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Allocazioni esclusive**|- Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice del corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Il numero non include gli oggetti creati nelle funzioni chiamate dalla funzione.<br />- Per una funzione chiamante, il numero delle allocazioni esclusive della funzione corrente generate da chiamate da questa funzione.<br />- Per una funzione chiamata, il numero di oggetti creati dalle istanze di questa funzione chiamate dalla funzione corrente. Il numero non include gli oggetti creati dalle funzioni chiamate dalla funzione chiamata.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Byte inclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Il numero include la memoria allocata nelle funzioni chiamate da questa funzione.<br />- Per una funzione chiamante, il numero dei byte inclusivi della funzione corrente generati da chiamate dalla funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze di questa funzione generati da chiamate dalla funzione corrente. Il numero include i byte allocati dalle funzioni chiamate dalla funzione chiamata.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Questo numero non include la memoria allocata dalle funzioni chiamate dalla funzione corrente.<br />- Per una funzione chiamante, il numero dei byte esclusivi della funzione corrente generati da chiamate dalla funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze della funzione generati da chiamate dalla funzione corrente. Il numero non include i byte allocati dalle funzioni chiamate dalla funzione chiamata.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)