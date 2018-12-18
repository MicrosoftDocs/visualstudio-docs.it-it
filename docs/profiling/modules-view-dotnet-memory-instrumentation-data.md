---
title: 'Visualizzazione Moduli: dati di strumentazione di memoria .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c04ecdc1de848a95ad9f5051cc9ec54da02a3625
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Visualizzazione Moduli: dati di strumentazione di memoria .NET
La visualizzazione Moduli dei dati di allocazione di memoria .NET raccolti tramite il metodo di strumentazione raggruppa i dati temporali e di memoria in base ai moduli eseguiti nell'esecuzione della profilatura. I dati di profilatura per le funzioni del modulo sono elencati sotto il nodo del modulo.  
  
## <a name="general"></a>Generale  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|Nome della funzione o del modulo.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Numero di chiamate**|Numero totale di chiamate effettuate a questa funzione o modulo.|  
|**File di origine**|File di origine che contiene la definizione di questa funzione.|  
|**Nome modulo**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo in cui era in esecuzione il modulo o la funzione.|  
|**Sovraccarico temporale per probe esclusivi**|Sovraccarico temporale per questa funzione o per questo modulo causato dalla strumentazione.|  
|**Sovraccarico temporale per probe inclusivi**|Sovraccarico temporale per questa funzione o per questo modulo e per le relative funzioni figlio causato dalla strumentazione.|  
  
## <a name="net-memory-values"></a>Valori di memoria .NET  
 I valori di memoria .NET inclusivi di una funzione indicano il numero (allocazioni) e le dimensioni (byte) di oggetti creati dalla funzione e dalle relative funzioni figlio.  
  
 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dalla funzione, ma non dalle relative funzioni figlio.  
  
 I valori di memoria inclusivi ed esclusivi di un modulo sono la somma dei valori di memoria inclusivi ed esclusivi delle funzioni nel modulo.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Allocazioni inclusive**|- Per una funzione, il numero totale di oggetti creati dalla funzione. Questo numero include gli oggetti creati dalle funzioni chiamate dalla funzione.<br />- Per un modulo, il numero di oggetti in un'esecuzione della profilatura che sono stati allocati durante l'esecuzione di almeno una funzione del modulo. Questo numero include gli oggetti allocati nelle funzioni generate da chiamate provenienti dalle funzioni del modulo.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni inclusive del modulo o della funzione.|  
|**Allocazioni esclusive**|- Per una funzione, il numero di oggetti creati durante l'esecuzione di codice nel corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Questo numero non include gli oggetti creati nelle funzioni chiamate dalla funzione.<br />- Per un modulo, la somma delle allocazioni esclusive delle funzioni nel modulo.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che rappresentavano allocazioni esclusive del modulo o della funzione.|  
|**Byte esclusivi**|- Per una funzione, il numero totale di byte di memoria allocati durante l'esecuzione di codice nel corpo della funzione, vale a dire quando la funzione si trovava in cima allo stack di chiamate. Questo numero non include i byte allocati nelle funzioni chiamate dalla funzione.<br />- Per un modulo, la somma dei byte esclusivi allocati dalle funzioni nel modulo.|  
|**% byte esclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresenta i byte esclusivi del modulo, della funzione, della riga o dell'istruzione.|  
|**Byte inclusivi**|- Per una funzione, il numero totale di byte allocati dalla funzione. Questo numero include i byte allocati nelle funzioni chiamate dalla funzione.<br />- Per un modulo, il numero di byte allocati in un'esecuzione della profilatura che sono stati allocati durante l'esecuzione di almeno una funzione del modulo. Questo numero include gli oggetti creati in tutte le funzioni chiamate dalle funzioni del modulo.|  
|**% byte inclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi del modulo o della funzione.|  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 I valori relativi al tempo inclusivo trascorso indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo trascorso**|- Per una funzione, il tempo dedicato alla funzione. Include il tempo dedicato alle funzioni figlio e alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per un modulo, il periodo di tempo di permanenza nello stack di chiamate di almeno una funzione nel modulo.|  
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
 I valori relativi al tempo inclusivo applicazione indicano il tempo di permanenza di una funzione nello stack di chiamate. Il tempo non include il tempo dedicato alle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output, ma include il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo inclusivo applicazione**|- Per una funzione, il tempo dedicato alle chiamate alla funzione. Include il tempo dedicato alle funzioni figlio, ma esclude le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.<br />- Per un modulo, il periodo di tempo in cui almeno una funzione del modulo si trovava nello stack di chiamate, escluso il tempo trascorso nelle chiamate al sistema operativo.|  
|**% tempo inclusivo applicazione**|Percentuale del tempo inclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo inclusivo applicazione di questo modulo o questa funzione.|  
|**Tempo inclusivo applicazione medio**|- Per una funzione, il tempo inclusivo applicazione medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione massimo**|- Per una funzione, il tempo inclusivo applicazione massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione minimo**|- Per una funzione, il tempo inclusivo applicazione minimo di una chiamata a questo modulo o a questa funzione.<br />- Per un modulo, il tempo inclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 I valori relativi al tempo esclusivo applicazione indicano il tempo dedicato al modulo o alla funzione, escluso il tempo trascorso nelle funzioni figlio. Il tempo indicato esclude anche le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input/output.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo esclusivo applicazione**|- Per una funzione, il tempo esclusivo applicazione totale di chiamate a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione totale di tutte le chiamate a funzioni nel modulo.|  
|**% tempo esclusivo applicazione**|Percentuale del tempo esclusivo trascorso totale di esecuzione della profilatura corrispondente al tempo esclusivo applicazione di questo modulo o questa funzione.|  
|**Tempo esclusivo applicazione medio**|- Per una funzione, il tempo esclusivo applicazione medio di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione massimo**|- Per una funzione, il tempo esclusivo applicazione massimo di una chiamata a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione minimo**|- Per una funzione, il tempo esclusivo applicazione minimo di una chiamata a questo modulo o a questa funzione.<br />- Per un modulo, il tempo esclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Moduli - Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)   
 [Visualizzazione moduli](../profiling/modules-view-sampling-data.md)