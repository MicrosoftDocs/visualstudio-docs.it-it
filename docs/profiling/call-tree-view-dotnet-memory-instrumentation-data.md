---
title: 'Visualizzazione Albero delle chiamate: dati di strumentazione di memoria .NET | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 043259d4ffd403abcffcfdfa724c8a8044caf5ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Visualizzazione Albero delle chiamate: dati di strumentazione di memoria .NET
La visualizzazione Albero delle chiamate dei dati di profilatura sull'allocazione di memoria .NET raccolti tramite il metodo di strumentazione contiene i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati temporali e di memoria .NET per la funzione.  
  
 I valori nella visualizzazione Albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate. I valori percentuali vengono calcolati confrontando il valore dell'istanza della funzione e il numero totale o le dimensioni delle allocazioni nell'esecuzione della profilatura.  
  
## <a name="highlighting-the-execution-hot-path"></a>Evidenziare il percorso critico di esecuzione  
 Nella visualizzazione Albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione del processo o della funzione che ha creato gli oggetti più grandi o il numero maggiore di oggetti in memoria. Per visualizzare il percorso più attivo fare clic con il pulsante destro del mouse sul processo o sulla funzione e quindi scegliere **Espandi percorso critico**.  
  
## <a name="setting-the-call-tree-root-node"></a>Impostare il nodo radice dell'albero delle chiamate  
 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare il nodo di inizio della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e selezionare **Imposta radice**.  
  
 Quando imposti il nodo radice, elimini dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. Per reimpostare il nodo radice sul nodo che si stava visualizzando, fare clic con il pulsante destro del mouse nella finestra della visualizzazione Albero delle chiamate e selezionare **Reimposta radice**.  
  
## <a name="general"></a>Generale  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Nome funzione**|Nome della funzione.|  
|**Indirizzo funzione**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Numero di chiamate**|Numero totale di chiamate effettuate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome assegnato al processo.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i valori di tempo esclusivo.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Type**|Il contesto della funzione:<br /><br /> -   **0**: la funzione corrente<br />-   **1**: una funzione che chiama la funzione corrente<br />-   **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-values"></a>Valori di memoria .NET  
 I valori di memoria .NET inclusivi di una funzione indicano il numero (allocazioni) e le dimensioni (byte) di oggetti creati dalla funzione e dalle funzioni chiamate da tale funzione.  
  
 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dal codice nel corpo della funzione e non da altre funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Allocazioni inclusive**|Numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate.|  
|**Allocazioni esclusive**|Numero di oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nell'albero delle chiamate. Questo numero non include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive delle istanze della funzione chiamate dalla funzione padre nell'albero delle chiamate.|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo dedicato alle funzioni chiamate dalla funzione e alle chiamate al sistema operativo, ad esempio a cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione eseguite dalla funzione padre nell'albero delle chiamate.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione della profilatura corrispondente al tempo inclusivo trascorso totale di questa funzione per le chiamate da parte della funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 I valori relativi al tempo esclusivo trascorso indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo include il tempo delle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output. Non è tuttavia incluso il tempo usato per le funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo trascorso**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione eseguite dalla funzione padre nell'albero delle chiamate.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questa funzione per le chiamate da parte della funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output. Il tempo include il tempo dedicato alle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione eseguite dalla funzione padre nell'albero delle chiamate.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione della profilatura corrispondente al tempo inclusivo applicazione totale di questa funzione per le chiamate da parte della funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori di tempo esclusivo applicazione indicano il tempo dedicato alla funzione, escluso il tempo dedicato alle funzioni figlio chiamate dalla funzione. Il tempo esclude anche le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione eseguite dalla funzione padre nell'albero delle chiamate.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione della profilatura corrispondente al tempo esclusivo applicazione totale di questa funzione per le chiamate da parte della funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione eseguita dalla funzione padre nell'albero delle chiamate.|