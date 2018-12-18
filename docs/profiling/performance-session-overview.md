---
title: Panoramica delle sessioni di prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 885d01d0d8f363a0b5b3a6abe2d3c2c018334092
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="performance-session-overview"></a>Panoramica delle sessioni di prestazioni
In questa panoramica vengono illustrate le nozioni di base della profilatura. Gli sviluppatori non esperti di prestazioni potranno notare come gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] possano contribuire ad accrescere rapidamente la produttività e a migliorare le prestazioni del codice. Gli sviluppatori con esperienza nella profilatura possono trovare informazioni su specifici processi e funzionalità degli strumenti di profilatura.  
  
 Gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consentono di identificare problemi di prestazioni nel codice sorgente e di confrontare le prestazioni delle possibili soluzioni. Le procedure guidate e le impostazioni predefinite degli strumenti di profilatura permettono di ottenere immediatamente informazioni dettagliate su molti problemi relativi alle prestazioni. Le funzionalità e le opzioni degli strumenti di profilatura assicurano un controllo completo del processo di profilatura. Questo controllo include la destinazione precisa delle sezioni di codice, la raccolta di informazioni sulla temporizzazione a livello di blocco e l'inclusione nei dati di altre informazioni sulle prestazioni del sistema e del processore.  
  
 I passaggi seguenti costituiscono il processo di base per l'uso degli strumenti di profilatura:  
  
1.  Configurare la sessione di prestazioni specificando il metodo di raccolta e i dati da raccogliere.  
  
2.  Raccogliere i dati di profilatura eseguendo l'applicazione nella sessione di prestazioni.  
  
3.  Analizzare i dati per identificare il problema di prestazioni.  
  
4.  Modificare il codice nell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per migliorare le prestazioni del codice per l'applicazione.  
  
5.  Raccogliere dati di profilatura sul codice modificato e confrontare i dati di profilatura originali e modificati.  
  
6.  Generare un rapporto che documenti il miglioramento delle prestazioni.  
  
 Per usare le informazioni fornite dalla profilatura, è necessario disporre delle informazioni sui simboli disponibili per i file binari da profilare e per i file binari del sistema operativo Windows.  
  
## <a name="configure-the-performance-session"></a>Configurare la sessione di prestazioni  
 Per configurare una sessione di profilatura, selezionare il metodo di profilatura da usare e i dati da raccogliere. La **Creazione guidata sessione di prestazioni** degli strumenti di profilatura guida l'utente durante la configurazione di base e le pagine delle proprietà di Sessione prestazioni possono essere usate per aggiungere altre opzioni:  
  
-   I metodi di profilatura includono campionamento, traccia e allocazione di memoria.  
  
-   I valori dei dati includono ora, contatori delle prestazioni del processore e del sistema operativo ed eventi dell'applicazione, quali errori di pagina e transizioni del kernel.  
  
 È possibile configurare una sessione di prestazioni in un progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nell'ambito della soluzione del progetto o profilare i file binari arbitrari tramite l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile specificare le proprietà della sessione nelle pagine delle proprietà di Sessione prestazioni oppure è possibile usare la procedura guidata di profilatura.  
  
## <a name="collect-profiling-data"></a>Raccogliere i dati di profilatura  
 La raccolta dei dati di profilatura viene avviata da **Esplora prestazioni**. È possibile sospendere e riprendere la profilatura per limitare la quantità di dati raccolti. È anche possibile collegarsi a un processo già in esecuzione.  
  
 All'avvio dell'applicazione, viene visualizzata la finestra **Controllo raccolta dati** nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dalla finestra **Controllo raccolta dati** è possibile profilare parti specifiche dell'applicazione sospendendo e riprendendo il processo di raccolta. È anche possibile usare la finestra **Controllo raccolta dati** per inserire contrassegni nei dati raccolti. I contrassegni sono punti dati definiti dall'utente visibili nelle visualizzazioni del profilo e utilizzabili per filtrare i dati di profilatura.  
  
 Quando l'applicazione di destinazione viene arrestata, gli strumenti di profilatura generano un file di dati di profilatura (con estensione vsp) e un rapporto di riepilogo visualizzato nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizzare i dati e identificare i problemi di prestazioni  
 Al termine dell'esecuzione di una profilatura, i dati vengono analizzati e nelle finestre della visualizzazione **Rapporto di prestazioni** degli strumenti di profilatura viene visualizzato un riepilogo. I dati di profilatura sono raccolti per lo stack di chiamate e le singole funzioni dell'applicazione di destinazione. Le visualizzazioni del rapporto contengono l'analisi delle prestazioni per gli intervalli di dati dei processi, dei thread, dei moduli, delle funzioni e delle righe di codice sorgente dell'applicazione. I valori dei dati di profilatura per una funzione includono gli elementi seguenti:  
  
-   Il tempo totale impiegato nella funzione e nelle funzioni figlio chiamate dalla funzione (valori inclusivi).  
  
-   Il tempo impiegato per l'esecuzione del solo codice nella funzione (valori esclusivi).  
  
 Più di dodici visualizzazioni diverse consentono di analizzare i dati di profilatura nella modalità più efficiente. Le personalizzazioni delle visualizzazioni permettono di filtrare e ordinare i dati per trovare le funzioni che potrebbero causare problemi di prestazioni. Il filtro Percorso critico fornisce un'evidenziazione immediata dei percorsi più attivi nelle visualizzazioni Albero delle chiamate e Modulo.  
  
## <a name="modify-the-application-code"></a>Modificare il codice dell'applicazione  
 Dopo avere isolato uno o più problemi di prestazioni rilevanti, è possibile modificare il codice tramite l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e raccogliere i dati di profilatura relativi alle modifiche.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Raccogliere nuovamente i dati di profilatura e confrontare i dati tra le esecuzioni di profilatura  
 La visualizzazione Rapporto di confronto degli strumenti di profilatura consente di visualizzare la differenza delle prestazioni del modulo, della funzione o della riga tra due file di dati di profilatura selezionati. È possibile specificare i valori dei dati di profilatura da confrontare e passare dalla visualizzazione del confronto alle visualizzazioni dei singoli file e viceversa.  
  
## <a name="generate-a-report-of-the-results"></a>Generare un rapporto dei risultati  
 È possibile incollare le righe di qualsiasi visualizzazione dei rapporti di prestazioni in messaggi e-mail e fogli di calcolo e generare rapporti contenenti i dati di una o più visualizzazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Overviews](../profiling/overviews-performance-tools.md)  (Panoramiche)  
 [Procedura dettagliata: Identificazione dei problemi di prestazioni](../profiling/walkthrough-identifying-performance-problems.md)