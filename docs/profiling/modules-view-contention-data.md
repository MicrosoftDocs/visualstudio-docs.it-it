---
title: 'Visualizzazione Moduli: dati sui conflitti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 619e2a38c794a6823f7efcfb5606bd9fbe9f461c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="modules-view---contention-data"></a>Visualizzazione Moduli: dati sui conflitti
Nella visualizzazione Moduli dei dati sui conflitti vengono visualizzati i dati sulla concorrenza raggruppati in base ai moduli campionati nei dati di profilatura. Ogni modulo è la radice di una struttura gerarchica. Le funzioni del modulo in cui si sono verificati gli eventi di conflitto sono elencate nel nodo del modulo.  
  
 Se era in corso l'esecuzione del codice della funzione quando si è verificato un evento di conflitto, ovvero la funzione si trovava in cima allo stack di chiamate, le righe di codice sorgente e gli indirizzi delle istruzioni in esecuzione sono elencati sotto il nodo della funzione. Poiché i dati vengono raccolti per una riga di codice sorgente o per un puntatore all'istruzione durante l'esecuzione della riga o dell'istruzione, i valori inclusivi ed esclusivi sono sempre gli stessi sia per i dati di riga che per quelli di istruzione.  
  
 La tabella seguente descrive i valori delle colonne nella visualizzazione Moduli dei dati sui conflitti.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Tempo blocco esclusivo**|- Per una funzione, l'ora in cui è stata impedita l'esecuzione di codice nel corpo della funzione. È escluso il tempo di blocco nelle funzioni chiamate dalla funzione.<br />- Per un modulo, la somma del tempo di blocco esclusivo delle funzioni nel modulo.<br />- Per una riga o un'istruzione, il periodo durante il quale è stata bloccata l'esecuzione della riga o dell'istruzione.|  
|**% tempo blocco esclusivo**|- Per una funzione o un modulo, la percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco esclusivo per la funzione o il modulo.<br />- Per una riga o un'istruzione, la percentuale del tempo totale di blocco nell'esecuzione di profilatura durante la quale è stata bloccata l'esecuzione della riga o dell'istruzione.|  
|**Conflitti esclusivi**|- Per una funzione, il numero di volte che è stata impedita l'esecuzione di codice nel corpo della funzione. Non sono inclusi i conflitti in funzioni chiamate dalla funzione.<br />- Per un modulo, la somma dei conflitti esclusivi delle funzioni nel modulo.<br />- Per una riga o un'istruzione, il numero di volte per cui è stata bloccata l'esecuzione della riga o dell'istruzione.|  
|**% conflitti esclusivi**|- Per una funzione o un modulo, la percentuale di tutti i conflitti nell'esecuzione di profilatura che rappresentavano conflitti esclusivi di questa funzione o di questo modulo.<br />- Per una riga o un'istruzione, la percentuale di tutti i conflitti nell'esecuzione della profilatura che rappresentavano conflitti che bloccavano l'esecuzione di questa riga o istruzione.|  
|**Tempo blocco inclusivo**|- Per una funzione, il periodo di blocco dell'esecuzione di questa funzione o di una funzione chiamata da questa.<br />- Per un modulo, la somma del tempo di blocco di permanenza nello stack di almeno una funzione da questo modulo.<br />- Per una riga o un'istruzione, il periodo durante il quale è stata bloccata l'esecuzione della riga o dell'istruzione.|  
|**% tempo blocco inclusivo**|- Per una funzione o un modulo, la percentuale del tempo totale di blocco nell'esecuzione della profilatura corrispondente al tempo di blocco inclusivo per la funzione o il modulo.<br />- Per una riga o un'istruzione, la percentuale del tempo totale di blocco nell'esecuzione di profilatura durante la quale era in esecuzione la riga o l'istruzione.|  
|**Conflitti inclusivi**|- Per una funzione, il numero di volte in cui l'esecuzione di questa funzione o di una funzione chiamata da questa è stata bloccata.<br />- Per un modulo, il numero di conflitti in cui almeno una funzione da questo modulo era nello stack.<br />- Per una riga o un'istruzione, il numero di volte per cui è stata bloccata l'esecuzione della riga o dell'istruzione.|  
|**% conflitti inclusivi**|- Per una funzione o un modulo, la percentuale di tutti i campioni nell'esecuzione della profilatura che costituivano campioni esclusivi di questa funzione o di questo modulo.<br />- Per una riga o un'istruzione, la percentuale del tempo totale di blocco nell'esecuzione di profilatura durante la quale era in esecuzione la riga o l'istruzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Nome modulo**|Nome del modulo che contiene la funzione, la riga o il puntatore all'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il modulo, la funzione, la riga o il puntatore all'istruzione.|  
|**Name**|Nome del modulo o della funzione.|  
|**ID processo**|ID di processo (PID) dell'esecuzione della profilatura.|  
|**Nome processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Moduli](../profiling/modules-view.md)   
 [Visualizzazione Moduli - Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli - Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)   
 [Visualizzazione moduli](../profiling/modules-view-sampling-data.md)