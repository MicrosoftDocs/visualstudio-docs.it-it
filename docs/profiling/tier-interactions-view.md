---
title: Visualizzazione Interazioni tra livelli | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.tierinteraction
helpviewer_keywords: Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a42e748e45d7db0606d585d774be254a7358d6b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="tier-interactions-view"></a>Visualizzazione Interazioni tra livelli
La profilatura delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione nelle funzioni di applicazioni multilivello che comunicano con i database tramite [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. I dati vengono raccolti solo per le chiamate di funzione sincrone.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 La visualizzazione Interazioni mostra i dati di interazione tra livelli in due riquadri:  
  
-   Il riquadro master è un albero gerarchico. La riga di primo livello contiene i dati aggregati relativi alle connessioni di database di una pagina [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o di un processo. I nodi figlio contengono i dati aggregati delle connessioni di database dell'elemento padre.  
  
-   Quando si fa clic su un nodo delle chiamate al database nel riquadro master, i dati per l'istanza della chiamata al database vengono visualizzati nel riquadro dei dettagli.  
  
 Il tempo viene visualizzato come numero di millisecondi o numero di tick del clock della CPU. Per modificare l'unità di tempo visualizzato, fare clic sul menu **Strumenti**, fare clic su **Opzioni** e quindi scegliere una delle opzioni **Mostra i valori di durata in**.  
  
## <a name="master-pane"></a>Riquadro master  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Name**|- Per una riga di primo livello, nome del processo o della pagina Web profilata.<br />- Per una riga di connessione di database, nome del server che ospita il database.|  
|**Database**|Nome del database (solo righe di connessione di database).|  
|**Conteggio**|Numero totale di richieste generate dal processo, dalla pagina Web o dalla connessione di database.|  
|**Tempo totale trascorso**|Tempo totale impiegato per l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione di database.|  
|**Tempo massimo trascorso**|Tempo massimo impiegato per l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione di database.|  
|**Tempo minimo trascorso**|Tempo minimo impiegato per l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione di database.|  
|**Tempo medio trascorso**|Tempo medio impiegato per l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione di database.|  
  
## <a name="database-connection-details-pane"></a>Riquadro Dettagli connessione database  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Testo del comando**|Query SQL della richiesta.|  
|**Conteggio query**|Numero di volte in cui è stata eseguita la query.|  
|**Tempo totale trascorso**|Tempo totale impiegato per l'esecuzione delle istanze della query.|  
|**Tempo massimo trascorso**|Tempo massimo impiegato per l'esecuzione di un'istanza della query.|  
|**Tempo minimo trascorso**|Tempo minimo impiegato per l'esecuzione di un'istanza della query.|  
|**Tempo medio trascorso**|Tempo medio impiegato per l'esecuzione di un'istanza della query.|