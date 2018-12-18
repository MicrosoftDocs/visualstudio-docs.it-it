---
title: Visualizzazione Dettagli funzione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81133dadb79cc4fba24b66e97f7384232b6171ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="function-details-view"></a>Visualizzazione Dettagli funzione
La finestra **Visualizzazione Dettagli funzione** visualizza le informazioni seguenti:  
  
-   Grafico a barre **Distribuzione costi**, che rappresenta le relazioni tra una funzione selezionata e le funzioni chiamanti che hanno eseguito la funzione selezionata e tra la funzione selezionata e le funzioni che ha chiamato.  
  
-   Tabella **Dettagli prestazioni funzione**, che visualizza i dati di profilatura di riepilogo per la funzione specificata.  
  
-   Finestra **Visualizzazione codice funzione**, che visualizza il codice della funzione quando questo è disponibile.  
  
 La finestra **Visualizzazione codice funzione** è un riquadro separato. Per impostazione predefinita,i due riquadri sono suddivisi orizzontalmente e la finestra **Visualizzazione codice funzione** è posizionata nella parte inferiore del frame.  
  
-   Per suddividere i due riquadri verticalmente, fare clic su **Dividi schermo verticalmente** sulla barra degli strumenti.  
  
-   Per modificare le dimensioni relative dei riquadri, fare clic sul bordo ombreggiato tra i frame e trascinare il bordo in un'altra posizione.  
  
## <a name="cost-distribution-bar-chart"></a>Grafico a barre Distribuzione costi  
  
### <a name="performance-metrics"></a>Metriche delle prestazioni  
 Nell'elenco a discesa **Metrica prestazioni** è possibile specificare i valori da visualizzare. I valori disponibili dipendono dal metodo di profilatura usato nel file dei dati di profilatura. I nomi tra parentesi sono i nomi delle righe nella tabella **Dettagli prestazioni funzione**.  
  
### <a name="bar-chart"></a>Grafico a barre  
 **Funzioni chiamanti**  
  
 La barra **Funzioni chiamanti** visualizza le funzioni che hanno chiamato la funzione selezionata. Le dimensioni del blocco che contiene la funzione chiamante sono proporzionali al contributo della funzione chiamante rispetto al valore totale della metrica prestazioni per la funzione selezionata.  
  
 È possibile fare clic sul nome di una funzione chiamante per selezionarla nella visualizzazione.  
  
-   Se le funzioni chiamanti da elencare sono troppe, le funzioni con i contributi meno importanti vengono raccolte in un blocco **Altro**. Fare clic su **Altro** per visualizzare tutte le funzioni chiamanti e chiamate della funzione selezionata nella finestra della **visualizzazione Chiamante/chiamato**. Per altre informazioni, vedere [Visualizzazione Chiamante/chiamato](../profiling/caller-callee-view.md).  
  
-   Se non sono presenti funzioni chiamanti o se la funzione è la funzione di ingresso di un thread o di un processo, viene visualizzato un blocco **Inizio dello Stack**.  
  
 **Funzione selezionata**  
  
 La barra della funzione selezionata mostra i contributi delle funzioni chiamate e del codice nella funzione selezionata rispetto alla metrica prestazioni totale della funzione selezionata. Le dimensioni del blocco che contiene una funzione chiamata o il corpo della funzione sono proporzionali al relativo contributo rispetto al valore totale della metrica prestazioni per la funzione selezionata.  
  
 È possibile fare clic sul nome di una funzione chiamata per selezionarla nella visualizzazione.  
  
-   Il valore **Totale** corrisponde alla metrica prestazioni per la funzione selezionata.  
  
-   Il blocco **Corpo della funzione** rappresenta la quantità del valore totale della metrica prestazioni relativo all'esecuzione diretta del codice nel corpo della funzione.  
  
-   Le funzioni chiamate dalla funzione selezionata sono elencate in blocchi. Le dimensioni del blocco delle funzioni selezionate rappresentano il valore della metrica prestazioni totale per la funzione selezionata riscontrato nella funzione chiamata.  
  
-   Se le funzioni chiamanti da elencare sono troppe, le funzioni con i contributi meno importanti vengono raccolte in un blocco **Altro**. Fare clic su **Altro** per visualizzare tutte le funzioni chiamanti e chiamate della funzione selezionata nella finestra della **visualizzazione Chiamante/chiamato**. Per altre informazioni, vedere [Visualizzazione Chiamante/chiamato](../profiling/caller-callee-view.md).  
  
-   Se non sono presenti funzioni chiamate, viene visualizzato un blocco **Fine dello stack**.  
  
## <a name="function-performance-details"></a>Dettagli prestazioni funzione  
 La tabella Dettagli prestazioni funzione contiene dati di riepilogo per le metriche prestazioni della funzione selezionata. Vengono visualizzati il valore e la percentuale. Specificare i dati di profilatura visualizzati nel grafico e nella tabella dei dettagli nell'elenco **Metrica prestazioni**.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Esclusivo**|-   Valore della metrica prestazioni relativo all'esecuzione del corpo della funzione.|  
|**In chiamate**|-    Valore della metrica prestazioni relativo a funzioni chiamate dalla funzione selezionata.|  
|**Totale inclusivo**|-   Totale dei valori **Esclusivo** e **In chiamate**.|  
  
## <a name="function-code-view"></a>Visualizzazione codice funzione  
 La finestra **Visualizzazione codice funzione** visualizza il listato del codice sorgente quando è disponibile. Accanto alle righe di codice sorgente che chiamano altre funzioni è presente una colonna ombreggiata contenente i valori della metrica prestazioni per la funzione chiamata. Per modificare il codice sorgente, fare clic sul collegamento al file del codice sorgente.  
  
## <a name="cost-distribution-bar-chart-values"></a>Valori del grafico a barre Distribuzione costi  
  
### <a name="sampling"></a>Campionamento  
 La tabella seguente descrive i valori nell'elenco Metrica prestazioni per i dati di profilatura raccolti tramite il metodo di campionamento.  
  
|||  
|-|-|  
|**Campioni inclusivi (campioni raccolti)**|-   Per una funzione chiamante, numero di campioni raccolti quando la funzione selezionata è stata chiamata da questa funzione chiamante.<br />-   Per il corpo della funzione, numero di campioni raccolti durante l'esecuzione del codice della funzione selezionata.<br />-   Per una funzione chiamata, numero di campioni raccolti durante l'esecuzione della funzione chiamata in seguito a una chiamata dalla funzione selezionata.|  
  
### <a name="instrumentation"></a>Strumentazione  
 La tabella seguente descrive i valori nell'elenco Metrica prestazioni per i dati di profilatura raccolti tramite il metodo di strumentazione.  
  
|||  
|-|-|  
|**Tempo inclusivo trascorso (tempo trascorso)**|Il tempo trascorso include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br /><br /> -   Per una **Funzione chiamante**, quantità di tempo trascorso durante l'esecuzione delle istanze della funzione selezionata chiamate dalla funzione. È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, quantità totale di tempo trascorso durante l'esecuzione del codice della funzione selezionata. Non è incluso il tempo trascorso nelle funzioni chiamate.<br />-   Per una funzione chiamata, quantità di tempo trascorso durante l'esecuzione delle istanze della funzione chiamate dalla funzione selezionata. È incluso il tempo trascorso nelle funzioni chiamate dalla funzione. È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.|  
|**Tempo inclusivo applicazione (tempo applicazione)**|Il tempo applicazione non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br /><br /> -   Per una **Funzione chiamante**, quantità di tempo applicazione durante l'esecuzione delle istanze della funzione selezionata chiamate dalla funzione. È incluso il tempo trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, quantità totale di tempo applicazione durante l'esecuzione del codice della funzione selezionata. Non è incluso il tempo trascorso nelle funzioni chiamate.<br />-   Per una funzione chiamata, quantità di tempo applicazione trascorso durante l'esecuzione delle istanze della funzione chiamate dalla funzione selezionata. È incluso il tempo trascorso nelle funzioni chiamate dalla funzione.|  
  
### <a name="net-memory"></a>Memoria .NET  
 La tabella seguente descrive i valori nell'elenco Metrica prestazioni per i dati di profilatura raccolti tramite il metodo di profilatura di memoria .NET.  
  
|||  
|-|-|  
|**Allocazioni inclusive (Allocazioni)**|-   Per una **Funzione chiamante**, numero di oggetti allocati dalle istanze della funzione selezionata chiamate dalla funzione. Sono inclusi gli oggetti allocati dalle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, numero di oggetti allocati dalla funzione selezionata durante l'esecuzione del codice relativo. Non sono inclusi gli oggetti allocati nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, numero di oggetti allocati dalle istanze della funzione chiamate dalla funzione selezionata. Sono inclusi gli oggetti allocati da funzioni chiamate dalla funzione.|  
|**Byte inclusivi (Byte)**|-   Per una **Funzione chiamante**, numero di byte allocati dalle istanze della funzione selezionata chiamate dalla funzione. Sono inclusi i byte allocati dalle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, numero totale di byte allocati dalla funzione selezionata durante l'esecuzione del codice relativo. Non sono inclusi i byte allocati nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, numero di byte allocati dalle istanze della funzione chiamate dalla funzione selezionata. Sono inclusi i byte allocati da funzioni chiamate dalla funzione.|  
  
### <a name="concurrency"></a>Concorrenza  
 La tabella seguente descrive i valori nell'elenco Metrica prestazioni per i dati di profilatura raccolti tramite il metodo di concorrenza.  
  
|||  
|-|-|  
|**Conflitti inclusivi (conflitti)**|-   Per una **Funzione chiamante**, numero di eventi di conflitto di risorse che si sono verificati nelle istanze della funzione selezionata chiamata dalla funzione. Sono inclusi gli eventi di conflitto nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, numero totale di eventi di conflitto che si sono verificati durante l'esecuzione del codice della funzione. Non sono inclusi i conflitti nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, numero di eventi di conflitto che si sono verificati nelle istanze della funzione chiamate dalla funzione selezionata. Sono inclusi gli eventi di conflitto che si sono verificati nelle funzioni chiamate dalla funzione.|  
|**Tempo blocco inclusivo (tempo blocco)**|-   Per una funzione chiamante, tempo trascorso in eventi di conflitto di risorse per le istanze della funzione selezionata chiamate dalla funzione. È incluso il tempo blocco trascorso nelle funzioni chiamate dalla funzione selezionata.<br />-   Per il **Corpo della funzione**, tempo totale trascorso in eventi di conflitto che si sono verificati durante l'esecuzione del codice della funzione. Non sono inclusi i conflitti che si verificano nelle funzioni chiamate dalla funzione selezionata.<br />-   Per una funzione chiamata, tempo trascorso in eventi di conflitto di risorse per le istanze della funzione selezionata chiamate dalla funzione selezionata. È incluso il tempo blocco trascorso nelle funzioni chiamate dalla funzione.|