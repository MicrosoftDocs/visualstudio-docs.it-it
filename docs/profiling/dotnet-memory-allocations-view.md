---
title: Visualizzazione Allocazioni per la memoria .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b293c5a6fe64324cb306933d90049548e7a6098
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="net-memory-allocations-view"></a>Visualizzazione Allocazioni per la memoria .NET
Nella visualizzazione Allocazioni sono elencati i tipi creati durante l'esecuzione della profilatura. Ogni tipo è il nodo radice di un albero delle chiamate in cui vengono visualizzati i percorsi di esecuzione delle funzioni che hanno generato le allocazioni del tipo.  
  
 I dati presenti in una riga di tipo visualizzano il numero totale di oggetti del tipo che sono stati creati nell'esecuzione della profilatura e il numero totale di byte allocati per gli oggetti di quel tipo. I valori inclusivi ed esclusivi per un tipo sono sempre gli stessi.  
  
-   I valori inclusivi riguardano gli oggetti creati nelle istanze della funzione e delle relative funzioni figlio chiamate dalla funzione padre nell'albero delle chiamate.  
  
-   I valori esclusivi riguardano gli oggetti creati direttamente dalla funzione quando sono stati chiamati dalla funzione padre. Gli oggetti creati nelle funzioni figlio non sono inclusi.  
  
 I dati per una funzione consentono di visualizzare il numero di oggetti creati e il numero di byte allocati per gli oggetti del tipo padre.  
  
## <a name="highlighting-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione  
 È possibile trovare il percorso di esecuzione dell'albero delle chiamate che ha creato la maggior parte degli oggetti del tipo padre.  
  
-   Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sul tipo o sulla funzione e quindi scegliere **Espandi percorso critico**.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione o del tipo allocato.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**Nome modulo**|Nome del modulo che contiene il tipo o la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il tipo o la funzione.|  
|**File di origine**|File di origine che contiene la definizione per il tipo o la funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa definizione di tipo o funzione nel file di origine.|  
|**Livello**|Indica se i dati sono per un tipo o una funzione.|  
|**Allocazioni inclusive**|- Per una funzione, il numero totale di oggetti del tipo padre creati dalla funzione. Il numero include gli oggetti creati nelle funzioni figlio.<br />- Per un tipo, il numero totale di istanze create per quel tipo.|  
|**% allocazioni inclusive**|- Per una funzione, la percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentano allocazioni del tipo padre da parte della funzione.<br />- Per un tipo, la percentuale del numero totale di oggetti creati nell'esecuzione della profilatura corrispondenti a istanze del tipo.|  
|**Allocazioni esclusive**|- Per una funzione, il numero di oggetti creati durante l'esecuzione diretta della funzione nella parte superiore dello stack di chiamate. Questo numero non include gli oggetti creati nelle funzioni figlio.<br />- Per un tipo, il numero totale di istanze create per quel tipo.|  
|**% allocazioni esclusive**|- Per una funzione, la percentuale di tutti gli oggetti creati nell'esecuzione della profilatura corrispondenti ad allocazioni esclusive del tipo padre da parte della funzione.<br />- Per un tipo, la percentuale del numero totale di oggetti creati nell'esecuzione della profilatura corrispondenti a istanze del tipo.|  
|**Byte inclusivi**|- Per una funzione, il numero di byte di memoria allocati dalla funzione per gli oggetti del tipo padre. Questo numero include la memoria allocata dalle funzioni figlio.<br />- Per un tipo, il numero totale di byte allocati durante l'esecuzione della profilatura per le istanze del tipo.|  
|**% byte inclusivi**|- Per una funzione, la percentuale di tutta la memoria allocata nell'esecuzione della profilatura che rappresenta allocazioni del tipo padre da parte della funzione.<br />- Per un tipo, la percentuale di tutta la memoria allocata nell'esecuzione della profilatura che è stata allocata per le istanze del tipo.|  
|**Byte esclusivi**|- Per una funzione, il numero di byte di memoria allocati dalla funzione per gli oggetti del tipo padre. Questo numero non include la memoria allocata dalle funzioni figlio.<br />- Per un tipo, il numero totale di byte allocati nell'esecuzione della profilatura per le istanze del tipo.|  
|**% byte esclusivi**|- Per una funzione, la percentuale di tutta la memoria allocata nell'esecuzione della profilatura che rappresenta allocazioni esclusive del tipo padre da parte della funzione.<br />- Per un tipo, la percentuale di tutta la memoria allocata nell'esecuzione della profilatura che è stata allocata per le istanze del tipo.|