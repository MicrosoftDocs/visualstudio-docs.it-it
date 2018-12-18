---
title: Rapporto profilo di esecuzione| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a6d699845d8cce3eb1a410720d4e5fbbfd69d0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="execution-profile-report"></a>Report del profilo di esecuzione
Il rapporto del profilo di esecuzione è un profilo di campionamento tradizionale. I campioni vengono presi ogni millisecondo circa durante i periodi in cui un thread è in esecuzione su un core logico e il visualizzatore di concorrenza compila un albero delle chiamate tipico collazionando il set di stack di campioni accumulato. I dati della tabella possono essere influenzati dall'intervallo di tempo corrente e dai thread nascosti e dai filtri seguenti che possono essere applicati:  
  
-   Se l'opzione Just My Code è selezionata, vengono visualizzati solo gli stack frame con codice utente, più un livello sotto il codice utente.  
  
-   Se è impostato il valore di Riduzione rumore, gli stack collazionati con una frequenza minore di quella specificata vengono esclusi dal filtro.  
  
 Nella tabella seguente vengono illustrate le colonne del rapporto.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|nome|Nome della funzione per ogni livello dello stack di chiamate.|  
|Campioni inclusivi|Numero totale di campioni raccolti per tutti gli stack accumulati nel livello dell'albero dello stack di chiamate. Il numero inclusivo è la somma dei campioni esclusivi per questa funzione e dei contatori inclusivi per tutti i nodi figlio.|  
|Campioni esclusivi|Numero totale di campioni raccolti per cui questa funzione è il livello più basso dello stack di chiamate.|  
|% inclusivi|La percentuale di campioni totali visualizzata nella colonna dei campioni inclusivi. Le percentuali vengono arrotondate a due cifre decimali.|  
|% esclusivi|La percentuale di campioni totali visualizzata nella colonna dei campioni esclusivi. Le percentuali vengono arrotondate a due cifre decimali.|  
|Dettagli|Nome completo della funzione. Include il conteggio delle righe, se disponibile.|  
  
 Questa tabella di rapporto viene illustrata in [Tempo di esecuzione (Visualizzazione thread)](../profiling/execution-time-threads-view.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)