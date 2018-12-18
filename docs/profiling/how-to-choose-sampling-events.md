---
title: 'Procedura: Scegliere eventi di campionamento | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da44be7f972a75e143e00346bf4a39d0bdf65c27
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-choose-sampling-events"></a>Procedura: Scegliere eventi di campionamento
Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raccolgono dati relativi alle prestazioni a un intervallo specificato come numero di cicli del processore usati dal processo profilato. Il numero predefinito di cicli in un intervallo è 10.000.000, pari a circa 0,01 secondi in un computer da 1 GHz. È possibile modificare il numero di cicli in un intervallo, nonché l'evento di campionamento. Sono disponibili gli eventi di campionamento seguenti:  
  
-   Cicli di clock per i problemi legati alla CPU.  
  
-   Errori di pagina per i problemi relativi alla memoria.  
  
-   Chiamate di sistema per i problemi associati all'I/O.  
  
-   Contatore di prestazioni, ovvero contatori CPU per problemi di prestazioni ridotte.  
  
> [!IMPORTANT]
>  Se si raccolgono dati di memoria .NET (allocazioni e/o durate degli oggetti) usando il metodo di campionamento, tutti gli eventi di campionamento specificati dall'utente vengono ignorati e si usano le allocazioni di memoria e/o gli eventi di Garbage Collection appropriati per raccogliere i dati.  
  
### <a name="to-select-a-sample-event"></a>Per selezionare un evento di campionamento  
  
1.  In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic sulle proprietà di **Campionamento**.  
  
3.  Dall'elenco a discesa **Evento di campionamento** selezionare l'evento di campionamento da usare per profilare l'applicazione.  
  
    > [!NOTE]
    >  L'opzione **Contatori di prestazioni disponibili** è abilitata solo se si seleziona **Contatore di prestazioni** dall'elenco a discesa **Evento di campionamento**.  
  
4.  Se si seleziona **Contatore di prestazioni**, selezionare un contatore CPU specifico dal controllo di visualizzazione albero **Contatori di prestazioni disponibili**.  
  
    -   I contatori inclusi nel nodo **Eventi portabili** sono disponibili in tutti i tipi di processori.  
  
    -   I contatori inclusi nel nodo **Eventi piattaforma** sono specifici del processore del computer in uso e potrebbero non essere disponibili in altri tipi di processori.  
  
5.  Quando si seleziona un evento di campionamento, nella casella di testo **Intervallo di campionamento** viene visualizzato un valore predefinito per l'intervallo di campionamento. Se necessario, è possibile immettere il valore desiderato nella casella di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)   
 [Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)