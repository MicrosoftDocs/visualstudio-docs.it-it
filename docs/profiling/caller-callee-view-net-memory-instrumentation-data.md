---
title: 'Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8ee600d74da21c328e0cb374bad1ffdf55083254
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET
La visualizzazione Chiamante/chiamato dei dati di profilatura della memoria .NET raccolti con il metodo di strumentazione consente di visualizzare i dati relativi ad allocazione e temporizzazione per una funzione selezionata e le relative funzioni padre e figlio di tale funzione. La visualizzazione Chiamante/chiamato contiene tre griglie.  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura della memoria relative alla funzione selezionata. Sono incluse tutte le chiamate campionate alla funzione.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza la quantità del valore della funzione selezionata (corrente) generato da chiamate da parte della funzione chiamante (padre).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza dati di profilatura di memoria per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Fare doppio clic su una riga della funzione chiamante o chiamata per rendere quella riga la funzione corrente.  
  
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
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome processo**|Nome assegnato al processo.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i valori di tempo esclusivo.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione. Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Type**|Il contesto della funzione:<br /><br /> **0**: la funzione corrente<br /><br /> **1**: una funzione che chiama la funzione corrente<br /><br /> **2**: una funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente. Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-allocation-values"></a>Valori di allocazione della memoria .NET  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Allocazioni esclusive**|- Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice nel corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Il numero non include gli oggetti creati nelle funzioni chiamate da questa funzione.<br />- Per una funzione chiamante, il numero delle allocazioni esclusive della funzione corrente generate da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il numero di oggetti creati dalle istanze di questa funzione chiamate dalla funzione corrente. Questo numero non include gli oggetti creati dalle funzioni chiamate dalla funzione chiamata.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|  
|**Allocazioni inclusive**|- Per la funzione corrente, il numero di oggetti allocati dalla funzione nell'esecuzione della profilatura. Il numero include gli oggetti creati nelle funzioni chiamate che sono state chiamate dalla funzione.<br />- Per una funzione chiamante, il numero delle allocazioni inclusive della funzione corrente generate da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il numero di oggetti allocati dalle istanze di questa funzione generati da chiamate dalla funzione corrente. Il numero include le allocazioni effettuate dalle funzioni chiamate da questa funzione chiamata.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Il numero non include la memoria allocata nelle funzioni chiamate che sono state chiamate dalla funzione.<br />- Per una funzione chiamante, il numero dei byte esclusivi della funzione corrente generati da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze di questa funzione generati da chiamate dalla funzione corrente. Il numero non include i byte allocati dalle funzioni chiamate dalla funzione chiamata.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive di questa funzione.|  
|**Byte inclusivi**|- Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione della profilatura. Il numero include la memoria allocata nelle funzioni chiamate che sono state chiamate dalla funzione.<br />- Per una funzione chiamante, il numero di byte inclusivi delle istanze della funzione corrente generati da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il numero di byte allocati dalle istanze di questa funzione generati da chiamate dalla funzione corrente. Il numero include i byte allocati dalle funzioni chiamate da questa funzione chiamata.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive di questa funzione.|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|- Per la funzione corrente, il tempo dedicato alla funzione. Il valore include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo inclusivo trascorso della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in questa funzione generato da chiamate dalla funzione corrente. Il valore include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo trascorso di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 I valori relativi al tempo esclusivo trascorso indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma non include il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo trascorso**|- Per la funzione corrente, il tempo dedicato all'esecuzione del corpo della funzione. Il valore esclude il tempo trascorso nelle funzioni figlio ma include le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo esclusivo trascorso della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in questa funzione generato da chiamate dalla funzione corrente. Il valore esclude il tempo dedicato alle funzioni figlio della funzione chiamata ma include le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma include il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|- Per la funzione corrente, il tempo dedicato alla funzione e alle relative funzioni figlio. Il valore esclude il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo inclusivo applicazione della funzione corrente generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in questa funzione e nelle relative funzioni figlio generato da chiamate dalla funzione corrente. Il valore non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori di tempo esclusivo applicazione indicano il tempo dedicato alla funzione, escluso il tempo trascorso nelle funzioni figlio. Il tempo indicato esclude anche il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|- Per la funzione corrente, il tempo dedicato all'esecuzione del corpo della funzione. Il valore non include il tempo trascorso nelle funzioni figlio né le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per una funzione chiamante, la quantità di tempo esclusivo applicazione della funzione corrente che è stato generato da chiamate da questa funzione chiamante.<br />- Per una funzione chiamata, il tempo trascorso in questa funzione generato da chiamate dalla funzione corrente. Il valore non include il tempo trascorso nelle funzioni figlio della funzione chiamata né le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)