---
title: 'Visualizzazione Albero delle chiamate: dati di campionamento di memoria .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c50e27ef43acc62c1dcf13403ce510064c986541
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Visualizzazione Albero delle chiamate: dati di campionamento di memoria .NET
La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati di allocazione della memoria .NET per queste chiamate di funzione.  
  
 I valori nella visualizzazione Albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore dell'istanza della funzione e il numero totale o le dimensioni delle allocazioni nell'esecuzione della profilatura.  
  
## <a name="highlighting-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione  
 Nella visualizzazione Albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione del processo o della funzione che ha creato gli oggetti più grandi o il numero maggiore di oggetti in memoria. Per visualizzare il percorso più attivo fare clic con il pulsante destro del mouse sul processo o sulla funzione e quindi scegliere **Espandi percorso critico**.  
  
## <a name="setting-the-call-tree-root-node"></a>Impostare il nodo radice dell'albero delle chiamate  
 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare un altro nodo come nodo di inizio della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e selezionare **Imposta radice**.  
  
 Quando imposti il nodo radice, elimini dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. Per reimpostare il nodo radice sul nodo che si stava visualizzando, fare clic con il pulsante destro del mouse nella finestra della visualizzazione Albero delle chiamate e selezionare **Reimposta radice**.  
  
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
|**Livello**|Profondità della funzione nell'albero delle chiamate.|  
|**Allocazioni inclusive**|Numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Allocazioni esclusive**|Numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero non include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate.|  
|**Byte inclusivi**|Numero di byte in memoria allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|Numero di byte in memoria allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero non include le allocazioni effettuate dalle funzioni figlio.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Albero delle chiamate: strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-sampling-data.md)   
 [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)