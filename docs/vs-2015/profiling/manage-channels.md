---
title: Gestire i canali | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48507f8133466c7ab48ba2992434c751a8e32014
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540934"
---
# <a name="manage-channels"></a>Gestione dei canali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gestione di canali](https://docs.microsoft.com/visualstudio/profiling/manage-channels).  
  
Nella **visualizzazione Thread** del visualizzatore di concorrenza è possibile organizzare i canali per il processo in modo da poter esaminare modelli specifici. È possibile ordinare i canali, spostarli verso l'alto o verso il basso e nasconderli o visualizzarli.  
  
## <a name="sort-by"></a>Ordina per  
 Il controllo Ordina per può essere usato per ordinare i thread in base a diversi criteri, sulla base del livello di zoom corrente. Ciò è particolarmente utile quando si sta cercando un determinato modello. È possibile ordinare i thread secondo i criteri seguenti:  
  
|Criteri|Definizione|  
|--------------|----------------|  
|Ora di inizio|Ordina i thread in base all'ora di inizio. Si tratta dell'ordinamento predefinito.|  
|Ora di fine|Ordina i thread in base all'ora di fine.|  
|Esecuzione|Ordina i thread in base alla percentuale di tempo trascorso in fase di esecuzione.|  
|Sincronizzazione|Ordina i thread in base alla percentuale di tempo trascorso in fase di sincronizzazione.|  
|I/O|Ordina i thread in base alla percentuale di tempo trascorso in fase di I/O (lettura e scrittura di dati).|  
|Sleep|Ordina i thread in base alla percentuale di tempo trascorso in fase di sospensione.|  
|Paging|Ordina i thread in base alla percentuale di tempo trascorso in fase di paging.|  
|Precedenza|Ordina i thread in base alla percentuale di tempo trascorso in fase di precedenza.|  
|Elaborazione interfaccia utente|Ordina i thread in base alla percentuale di tempo trascorso in fase di elaborazione dell'interfaccia utente.|  
  
## <a name="move-selected-channel-up-or-down"></a>Spostare il canale selezionato verso l'alto o verso il basso  
 È possibile usare questi controlli per spostare un canale verso l'alto o verso il basso nell'elenco. Ad esempio, è possibile posizionare i canali correlati uno accanto all'altro in modo da poter esaminare un determinato modello o una relazione cross-thread.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Spostare il canale selezionato al primo o all'ultimo posto  
 È possibile spostare i canali selezionati al primo o all'ultimo posto dell'elenco in modo da poter esaminare un determinato modello o escludere alcuni canali quando si esaminano gli altri.  
  
## <a name="hide-selected-channels"></a>Nascondere i canali selezionati  
 Scegliere questo controllo quando si vogliono nascondere i canali. Ad esempio, se un thread è al 100% della sincronizzazione per la durata del processo gestito, è possibile nasconderlo mentre si analizzano altri thread.  
  
> [!NOTE]
>  Se un thread viene nascosto, verrà rimosso anche dal tempo di calcolo visualizzato nella legenda attiva e nei rapporti del profilo.  
  
## <a name="show-all-channels"></a>Mostra tutti i canali  
 Questo controllo è attivo quando uno o più canali vengono nascosti. Se si specifica questo controllo, tutti gli elementi nascosti vengono visualizzati e vengono inclusi nel calcolo del tempo.  
  
## <a name="move-markers-to-top"></a>Sposta i marcatori all'inizio  
 Se una traccia contiene eventi marcatori, è possibile usare questo comando per spostare i canali dei marcatori all'inizio della sequenza temporale. Viene comunque mantenuto il loro ordine relativo.  
  
## <a name="group-markers-by-thread"></a>Raggruppare i marcatori in base ai thread  
 Se una traccia contiene eventi marcatori, è possibile usare questo comando per raggruppare i canali dei marcatori sotto il thread che ha generato gli eventi marcatori.  I canali dei dischi vengono spostati all'inizio dell'elenco dei canali e i canali GPU vengono spostati alla fine.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo zoom (visualizzazione Thread)](../profiling/zoom-control-threads-view.md)   
 [Modalità misurazione attiva/non attiva](../profiling/measure-mode-on-off.md)   
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)



