---
title: 'Procedura: Raccogliere i dati di campionamento a livello di riga | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 56115f2605cfc2c5f9dc1c4a42062208056b172c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-collect-line-level-sampling-data"></a>Procedura: Raccogliere i dati di campionamento a livello di riga
Il campionamento a livello di riga è una capacità del profiler che consente di determinare il punto del codice di una funzione che richiede un uso intensivo del processore, ad esempio una funzione con esempi esclusivi elevati, in cui il processore impiega la maggior parte del tempo.  
  
## <a name="overview"></a>Panoramica  
 Nel campionamento a livello di riga il profiler analizza lo stack di chiamate del programma a intervalli prestabiliti e aggrega i risultati ottenuti. Questi risultati mostrano le istruzioni che il processore stava eseguendo quando i campioni sono stati prelevati. I dati raccolti sui campioni esclusivi vengono quindi analizzati per identificare le righe del codice e il puntatore all'istruzione (IP).  
  
 Il campionamento a livello di riga può essere usato per il codice gestito così come per quello nativo. I rapporti di prestazioni che consentono di visualizzare questi dati includono la visualizzazione Righe e la visualizzazione Moduli.  
  
 Le informazioni di inizio/fine carattere non sono disponibili per il codice nativo. Per le istruzioni su più righe, per il codice nativo non sono disponibili le informazioni di inizio riga, ma solo quelle di fine riga.  
  
### <a name="available-data"></a>Dati disponibili  
 I dati del campionamento a livello di riga disponibili includono le informazioni seguenti:  
  
-   Nome funzione.  
  
-   Indirizzo funzione.  
  
-   Inizio riga: numero riga del codice di esempio.  
  
-   Fine riga: numero riga di fine del codice sorgente. Generalmente corrisponde al valore di "Inizio riga" ad eccezione di quando una singola istruzione del programma si estende su più righe del codice sorgente.  
  
-   Inizio carattere: colonna iniziale dell'esempio di aggregazione. Generalmente questo valore è 0 ad eccezione di quando una singola riga contiene più istruzioni del programma.  
  
-   Fine carattere: colonna finale dell'esempio di aggregazione.  
  
-   IP: indirizzo da cui è stato prelevato l'esempio di aggregazione (solo visualizzazione IP).  
  
 Nella visualizzazione **Moduli**, se una funzione presenta statistiche a livello di riga, le statistiche vengono annidate in ogni funzione. Vengono inoltre visualizzate le statistiche a livello di IP annidate in ogni riga.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Disattivare il campionamento a livello di riga per il codice gestito  
 Per impostazione predefinita, il campionamento a livello di riga è attivato. È possibile disattivare la raccolta di dati a livello di riga per il codice gestito in uno dei seguenti modi:  
  
-   Prima della profilatura, digitare **VSPerfCLREnv /samplelineoff**. Questa operazione ha effetto sulle applicazioni e sui servizi.  
  
     oppure  
  
-   Quando si avvia un'applicazione, digitare **VSPerfCmd /lineoff \<altri argomenti>**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)