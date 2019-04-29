---
title: Avvisi di crittografia
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 669b7806e01772e6a871b6c6a9bf47907cf9a5a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816588"
---
# <a name="cryptography-warnings"></a>Avvisi di crittografia
Gli avvisi di crittografia supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia. Questi avvisi contribuiscono ad evitare che il programma presenti difetti nella sicurezza. Se si disabilita uno qualsiasi di questi avvisi, è opportuno indicarne chiaramente il motivo nel codice e informare il responsabile della sicurezza designato per il progetto di sviluppo.

|Regola|Descrizione|
|----------|-----------------|
|[CA5350: Non usare algoritmi di crittografia vulnerabili](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza o l'integrità dei dati che proteggono.        Questa regola si attiva quando vengono rilevati algoritmi TripleDES, SHA1 o RIPEMD160 nel codice.|
|[CA5351: non usare algoritmi di crittografia interrotti](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Gli algoritmi di crittografia violati non sono considerati sicuri e il loro uso è fortemente sconsigliato. Questa regola si attiva quando nel codice vengono rilevati l'algoritmo hash MD5 oppure gli algoritmi di crittografia DES o RC2.|