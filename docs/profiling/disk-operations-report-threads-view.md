---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c890ac9dbd3b542a400fc2a5b6db7ee2eb8f5db2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613856"
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
Nel rapporto delle operazioni su disco vengono descritte le operazioni I/O eseguite nei canali del disco.

 Per ogni accesso al disco che avviene per conto del processo sottoposto a profilatura nell'intervallo di tempo attualmente visibile, vengono segnalate le informazioni seguenti:

-   Nome e PID del processo che ha eseguito l'accesso al disco

-   ID del thread che ha eseguito l'accesso al disco

-   Nome del file al quale è stato eseguito l'accesso.

-   Numero di letture per ogni file

-   Numero di byte letti.

-   Latenza di lettura in millisecondi

-   Numero di operazioni di scrittura

-   Numero di byte scritti

-   Latenza di scrittura in millisecondi

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)