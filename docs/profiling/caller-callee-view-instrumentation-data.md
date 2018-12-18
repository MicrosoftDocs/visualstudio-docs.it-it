---
title: 'Visualizzazione Chiamante/chiamato: dati di strumentazione | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c8048d7dfd54627394705b2ca9e2ba9949f2bca1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="callercallee-view---instrumentation-data"></a>Visualizzazione Chiamante/chiamato: dati di strumentazione
La visualizzazione Chiamante/chiamato consente di visualizzare informazioni di profilatura per una funzione selezionata e le relative funzioni padre e figlio nell'albero delle chiamate. La visualizzazione Chiamante/chiamato contiene tre griglie.  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura relative alla funzione selezionata. Sono incluse tutte le chiamate alla funzione.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza informazioni di profilatura relative alle funzioni chiamanti (padre) della funzione selezionata. I valori indicano la quantità del valore della funzione corrente generato da chiamate da questa funzione chiamante.  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza informazioni di profilatura relative alle istanze delle funzioni chiamate (figlio) della funzione selezionata. I valori indicano solo il tempo trascorso nella funzione figlio quando è stata chiamata dalla funzione corrente.  
  
## <a name="general"></a>Generale  
 Le colonne generali identificano la funzione in una riga della visualizzazione.  
  
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
|**Nome processo**|Nome del processo.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i valori di tempo esclusivo.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Type**|Il contesto della funzione:<br /><br /> **0**: la funzione corrente<br /><br /> **1**: una funzione che chiama la funzione corrente<br /><br /> **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo trascorso nelle funzioni figlio e il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|- Per la funzione corrente, il tempo dedicato alla funzione. Il valore include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo inclusivo trascorso della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in istanze di questa funzione generato da chiamate dalla funzione corrente. Il valore include il tempo dedicato alle funzioni figlio della funzione chiamata e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo trascorso di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 I valori relativi al tempo esclusivo trascorso indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma è escluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo trascorso**|- Per la funzione corrente, il tempo dedicato all'esecuzione diretta della funzione. Il valore include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo esclusivo trascorso della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in istanze di questa funzione generato da chiamate dalla funzione corrente. Il valore esclude il tempo dedicato alle funzioni figlio della funzione chiamata ma include le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma include il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|- Per la funzione corrente, il tempo dedicato alla funzione e alle relative funzioni figlio. Il valore esclude il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo inclusivo applicazione della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in istanze di questa funzione generato da chiamate dalla funzione corrente. Il valore include il tempo trascorso nelle funzioni figlio della funzione chiamata ma esclude il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori di tempo esclusivo applicazione indicano il tempo trascorso nella funzione. Esclude il tempo trascorso nelle funzioni figlio ed esclude anche le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|- Per la funzione corrente, il tempo dedicato all'esecuzione diretta della funzione. Il valore non include il tempo trascorso nelle funzioni figlio né le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo esclusivo applicazione della funzione corrente che è stato generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in istanze di questa funzione generato da chiamate dalla funzione corrente. Il valore non include il tempo trascorso nelle funzioni figlio della funzione chiamata né le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)