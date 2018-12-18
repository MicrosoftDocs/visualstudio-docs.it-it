---
title: Informazioni sui valori dei dati di strumentazione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1addb93dfe5c4c39bb29507aa39eba66131f888
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-instrumentation-data-values"></a>Informazioni sui valori dei dati di strumentazione
Il metodo di profilatura *Strumentazione* di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra informazioni dettagliate sugli intervalli per le chiamate di funzione, le righe e le istruzioni nell'applicazione sottoposta a profilatura.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Il metodo di strumentazione inserisce codice all'inizio e alla fine delle funzioni di destinazione nel file binario sottoposto a profilatura, oltre che prima e dopo ogni chiamata da tali funzioni ad altre funzioni. Il codice inserito registra le informazioni seguenti:  
  
-   L'intervallo tra questo evento di raccolta e quello precedente.  
  
-   Se il sistema operativo ha eseguito un'operazione durante l'intervallo. Ad esempio, il sistema operativo potrebbe eseguire operazioni di lettura o scrittura su disco o passare dal thread di destinazione a un altro thread in un altro processo.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Per ogni intervallo, l'analisi del profiler ricostruisce lo stack di chiamate presente alla fine dell'intervallo. Uno stack di chiamate è l'elenco delle funzioni attive in un processore in un determinato momento. Una sola funzione (la funzione corrente) esegue codice: le altre funzioni sono la catena delle chiamate di funzione che ha determinato la chiamata alla funzione corrente (lo stack di chiamate).  
  
 Per ogni funzione nello stack di chiamate durante la registrazione dell'intervallo, l'analisi del profiler aggiunge l'intervallo a uno o più di quattro valori di dati per la funzione. L'analisi aggiunge l'intervallo a un valore di dati per una funzione in base ai due criteri:  
  
-   Se l'intervallo ha avuto luogo nel codice della funzione o in una *funzione figlio* (una funzione che è stata chiamata dalla funzione).  
  
-   Se si è verificato un evento del sistema operativo durante l'intervallo.  
  
 I valori di dati per un intervallo di una di funzione o un intervallo di dati sono denominati *Inclusivo trascorso*, *Esclusivo trascorso*, *Inclusivo applicazione* ed *Esclusivo applicazione*:  
  
-   Tutti gli intervalli di una funzione vengono aggiunti al valore di dati Inclusivo trascorso.  
  
-   Se l'intervallo ha avuto luogo nel codice della funzione e non in una funzione figlio, l'intervallo viene aggiunto al valore di dati Esclusivo trascorso della funzione.  
  
-   Se non si è verificato alcun evento del sistema operativo durante l'intervallo, l'intervallo viene aggiunto al valore di dati Inclusivo applicazione.  
  
-   Se non si è verificato alcun evento del sistema operativo durante l'intervallo e l'intervallo ha avuto luogo durante l'esecuzione diretta del codice della funzione (non in una funzione figlio), l'intervallo viene aggiunto al valore di dati Esclusivo applicazione.  
  
 I report degli strumenti di profilatura aggregano i valori totali delle funzioni nella sessione di profilatura, oltre che i processi, i thread e i file binari della sessione.  
  
## <a name="elapsed-inclusive-values"></a>Valori di tempo inclusivo trascorso  
 Tempo totale impiegato per l'esecuzione di una funzione e delle relative funzioni figlio.  
  
 I valori relativi al tempo inclusivo trascorso includono gli intervalli impiegati per eseguire direttamente il codice della funzione e gli intervalli impiegati per eseguire le funzioni figlio della funzione di destinazione. I valori relativi al tempo inclusivo trascorso includono anche gli intervalli della funzione o delle relative funzioni figlio che comprendono l'attesa del sistema operativo.  
  
## <a name="elapsed-exclusive-values"></a>Valori di tempo esclusivo trascorso  
 Tempo impiegato per l'esecuzione di una funzione, escluso il tempo trascorso nelle funzioni figlio.  
  
 I valori relativi al tempo esclusivo trascorso includono gli intervalli impiegati per eseguire direttamente il codice della funzione, indipendentemente dal fatto che si sia verificato o meno un evento del sistema operativo durante l'intervallo. I valori relativi al tempo esclusivo trascorso non includono tutti gli intervalli di tempo trascorsi nelle funzioni figlio che sono state chiamate dalla funzione di destinazione.  
  
## <a name="application-inclusive-values"></a>Valori di tempo inclusivo applicazione  
 Tempo impiegato per l'esecuzione di una funzione e delle relative funzioni figlio, escluso il tempo trascorso negli eventi del sistema operativo.  
  
 I valori Inclusivo applicazione non includono gli intervalli che contengono eventi del sistema operativo. I valori Inclusivo applicazione includono tutti gli altri intervalli impiegati per l'esecuzione di una funzione, indipendentemente dal fatto che l'intervallo sia stato impiegato per eseguire direttamente il codice della funzione o nelle funzioni figlio della funzione di destinazione.  
  
## <a name="application-exclusive-values"></a>Valori di tempo esclusivo applicazione  
 Tempo impiegato per l'esecuzione di una funzione, escluso il tempo trascorso nelle funzioni figlio e quello trascorso negli eventi del sistema operativo.  
  
 I valori relativi al tempo esclusivo applicazione non includono gli intervalli che contengono eventi del sistema operativo o gli intervalli impiegati per l'esecuzione delle funzioni chiamate dalla funzione. I valori relativi al tempo esclusivo applicazione includono solo gli intervalli che sono stati impiegati per eseguire direttamente il codice della funzione e che non contengono alcun evento del sistema operativo.  
  
## <a name="elapsed-inclusive-percent"></a>Percentuale Inclusivo trascorso  
 Percentuale dei valori di tempo inclusivo trascorso totali della sessione di profilatura che erano valori di tempo inclusivo trascorso della funzione, del modulo, del thread o del processo.  
  
 100 * Inclusivo trascorso funzione / Inclusivo trascorso sessione  
  
## <a name="elapsed-exclusive-percent"></a>Percentuale Esclusivo trascorso  
 Percentuale dei valori di tempo inclusivo trascorso totali della sessione di profilatura che erano valori di tempo esclusivo trascorso della funzione, del modulo, del thread o del processo.  
  
 100 * Esclusivo trascorso funzione / Inclusivo trascorso sessione  
  
## <a name="application-inclusive-percent"></a>Percentuale Inclusivo applicazione  
 Percentuale dei valori di tempo inclusivo applicazione totali della sessione di profilatura che erano valori di tempo inclusivo applicazione della funzione, del modulo, del thread o del processo.  
  
 100 * Inclusivo applicazione funzione / Inclusivo applicazione sessione  
  
## <a name="application-exclusive-percent"></a>Percentuale Esclusivo applicazione  
 Percentuale dei valori di tempo inclusivo applicazione totali della sessione di profilatura che erano intervalli di tempo esclusivo applicazione della funzione, del modulo, del thread o del processo.  
  
 100 * Esclusivo applicazione funzione / Inclusivo applicazione sessione  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)   
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)