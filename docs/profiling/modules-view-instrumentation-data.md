---
title: Visualizzazione Moduli - dati di strumentazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c7db34fb4913e3576f286aa7c34fe3cf80296ed
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="modules-view---instrumentation-data"></a>Visualizzazione Moduli - dati di strumentazione
Nella visualizzazione Moduli vengono visualizzati i dati sulle prestazioni raggruppati in base ai moduli presenti nei dati di profilatura. Le funzioni del modulo sono elencate sotto il nodo del modulo.  
  
## <a name="general"></a>Generale  
 Le colonne generali identificano la funzione in una riga della visualizzazione.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione o del modulo.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Numero di chiamate**|Numero totale di chiamate effettuate a questa funzione o modulo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo in cui era in esecuzione il modulo o la funzione.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione o per questo modulo causato dalla strumentazione.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione o per questo modulo e per le relative funzioni figlio causato dalla strumentazione.|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|- Per una funzione, il tempo dedicato alla funzione. Include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per un modulo, il tempo di permanenza nello stack di chiamate di almeno una funzione nel modulo.|  
|**% tempo inclusivo trascorso**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo trascorso totale di questo modulo o questa funzione.|  
|**Tempo inclusivo trascorso medio**|- Per una funzione, il tempo inclusivo trascorso medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso massimo**|- Per una funzione, il tempo inclusivo trascorso massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso minimo**|- Per una funzione, il tempo inclusivo trascorso minimo di una chiamata a questo modulo o questa funzione.<br />- Per un modulo, il tempo inclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 I valori relativi al tempo esclusivo trascorso indicano il tempo di esecuzione diretta di una funzione in cima allo stack di chiamate. Il tempo include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma è escluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo trascorso**|- Per una funzione, il tempo dedicato al modulo o alla funzione. Include le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma viene escluso il tempo dedicato alle funzioni figlio.<br />- Per un modulo, la somma del tempo esclusivo trascorso delle funzioni nel modulo.|  
|**% tempo esclusivo trascorso**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo trascorso totale di questo modulo o questa funzione.|  
|**Tempo esclusivo trascorso medio**|- Per una funzione, il tempo esclusivo trascorso medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso massimo**|- Per una funzione, il tempo esclusivo trascorso massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso minimo**|- Per una funzione, il tempo esclusivo trascorso minimo di una chiamata a questo modulo o questa funzione.<br />- Per un modulo, il tempo esclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output. Invece, è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|- Per una funzione, il tempo dedicato alle chiamate alla funzione. Include il tempo dedicato alle funzioni figlio, ma esclude le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per un modulo, il tempo di permanenza nello stack di chiamate di almeno una funzione nel modulo. Non include il tempo trascorso nelle chiamate al sistema operativo.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione di questo modulo o questa funzione.|  
|**Tempo inclusivo applicazione medio**|- Per una funzione, il tempo inclusivo applicazione medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione massimo**|- Per una funzione, il tempo inclusivo applicazione massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione minimo**|- Per una funzione, il tempo inclusivo applicazione minimo di una chiamata a questo modulo o a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori relativi al tempo esclusivo applicazione indicano il tempo dedicato al modulo o alla funzione. È escluso il tempo dedicato alle funzioni figlio così come alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|Tempo esclusivo applicazione totale di tutte le chiamate a questo modulo o a questa funzione.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione di questo modulo o questa funzione.|  
|**Tempo esclusivo applicazione medio**|- Per una funzione, il tempo esclusivo applicazione medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione massimo**|- Per una funzione, il tempo esclusivo applicazione massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione minimo**|- Per una funzione, il tempo esclusivo applicazione minimo di una chiamata a questo modulo o a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)   
 [Visualizzazione Moduli - Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli - Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)