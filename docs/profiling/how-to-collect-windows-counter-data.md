---
title: 'Procedura: Raccogliere i dati dei contatori Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 842ce89c687c1f39bc013a7b1eb2c4b330a86f47
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-collect-windows-counter-data"></a>Procedura: Raccogliere i dati dei contatori Windows

I contatori Windows sono contatori di prestazioni del sistema che possono essere raccolti a intervalli prestabiliti durante la profilatura. Nella visualizzazione Contrassegni del rapporto degli strumenti di profilatura è presente una riga con etichetta **AutoMark** per ogni intervallo della raccolta. La riga contiene colonne che descrivono i valori dei contatori di prestazioni inclusi nell'intervallo specificato. Per limitare l'analisi a un periodo di tempo compreso tra due contrassegni particolari, selezionare i contrassegni, fare clic con il pulsante destro del mouse e quindi scegliere **Filtra per** ->  **Contrassegni** dal menu di scelta rapida.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

## <a name="to-collect-windows-counter-data"></a>Per raccogliere i dati dei contatori Windows

1. In Esplora prestazioni fare clic con il pulsante destro del mouse sulla sessione per cui si vogliono configurare i contatori Windows e scegliere **Proprietà**.

2. In **Pagine delle proprietà** fare clic su **Contatori Windows**.

3. Selezionare la casella di controllo **Raccogliere contatori Windows**.

4. Nella casella di testo **lntervallo di raccolta (msec)** digitare un intervallo di tempo.

5. Selezionare una categoria dall'elenco a discesa **Categoria contatori**.

6. Selezionare un'istanza dall'elenco a discesa **Istanza**.

7. Selezionare i contatori da usare quando si profila l'applicazione.

8. Fare clic su **Applica**.

## <a name="see-also"></a>Vedere anche

[Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
[Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)  
[Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)