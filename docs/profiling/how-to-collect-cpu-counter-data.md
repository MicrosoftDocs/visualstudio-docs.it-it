---
title: Raccogliere i dati dei contatori CPU | Microsoft Docs
description: Informazioni su come usare i contatori di eventi CPU (hardware) per raccogliere dati sulle prestazioni specifici dell'hardware. Questo articolo elenca i vari tipi di eventi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a085f732263e0d2eb3d7e1f211c54fac46fbc6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876901"
---
# <a name="how-to-collect-cpu-counter-data"></a>Procedura: Raccogliere i dati dei contatori CPU

Un contatore di eventi CPU viene usato per raccogliere i dati relativi alle prestazioni dell'hardware. Questo articolo illustra come raccogliere i dati del contatore degli eventi quando si usa il metodo di profilatura della strumentazione.

Si verificano due tipi di eventi del contatore CPU:

- Eventi portabili: eventi della CPU che possono essere raccolti indipendentemente dal tipo di CPU.

- Eventi piattaforma: eventi della CPU associati a un particolare tipo di CPU.

Gli eventi portabili includono eventi generali, ad esempio le istruzioni ritirate e i cicli non interrotti, eventi del buffer della CPU, eventi di diramazione ed eventi della cache L2. I contatori degli eventi piattaforma disponibili sono determinati dal produttore del processore.

Le categorie di eventi possono essere condivise tra contatori portabili e di piattaforma. Ad esempio, le categorie di dati seguenti sono spesso comuni a entrambi i tipi:

- Eventi memoria.

- Eventi front-end.

- Eventi di diramazione.

Nel profiler è possibile raccogliere i dati del contatore di prestazioni in due modi:

- Raccogliere i dati da uno o più contatori quando si esegue la profilatura tramite strumentazione.

- Specificare un evento di contatore come intervallo di campionamento quando si esegue la profilatura mediante campionamento. Per altre informazioni, vedere [procedura: scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Per raccogliere i dati dei contatori di prestazioni CPU quando si esegue la profilatura tramite strumentazione

1. In **Pagine delle proprietà** per la sessione di prestazioni fare clic su **Contatori CPU**.

2. Selezionare la casella di controllo **Raccogli contatori CPU**.

3. Espandere l'albero **Contatori di prestazioni disponibili** fino a individuare gli eventi di campionamento da raccogliere.

4. Per ogni evento di cui si vogliono raccogliere i dati, selezionare l'evento e quindi fare clic sulla freccia DESTRA per aggiungere l'evento all'elenco **Contatori selezionati**.

    > [!NOTE]
    > L'opzione **Contatori di prestazioni disponibili** è abilitata solo se si seleziona la casella di controllo **Raccogli contatori CPU**.

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni](../profiling/configuring-performance-sessions.md) 
 di prestazioni Proprietà della sessione di [prestazioni](../profiling/performance-session-properties.md) 
 Contatori CPU e [Windows](../profiling/cpu-and-windows-counters.md) 
 [Procedura: scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)
