---
title: Grafica API e le statistiche di memoria | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48c8ed3c8c2ebffc57ac46e987dbc37950cba0fd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-api-and-memory-statistics"></a>Grafica API e le statistiche di memoria
<!-- VERSIONLESS -->
Visual Studio 2017 e maggiore supporto delle statistiche di API grafica e strumenti le statistiche di memoria.  Questi due strumenti consentono di visualizzare diverse parti di informazioni su utilizzo delle API di Direct3D, così come il consumo di memoria GPU di varie risorse.

## <a name="graphics-api-statistics"></a>Statistiche di API grafica
Le statistiche di API grafica in Visual Studio Graphics Diagnostics consente di visualizzare tutte le chiamate Direct3D che sono state apportate e il conteggio di ogni chiamata.  Per visualizzare la finestra, selezionare il **Vista > API statistiche** voce di menu.

![Statistiche di API](media/gfx_diag_api_statistics.png)

Questo strumento può essere utile in individuazione chiamate DirectX che non è possibile comprendere si apportano chiamate o che si sta rendendo troppo spesso.

È possibile fare doppio clic nella finestra per copiare tutti i dati in formato CSV, che possono essere incollati in simile di Excel per un'ulteriore analisi.

## <a name="memory-statistics"></a>Statistiche di memoria
Questo strumento verrà visualizzata la quantità di memoria è l'allocazione dei driver di grafica per le risorse create in un frame.  Per visualizzare questa finestra, selezionare il **Vista > le statistiche di memoria** voce di menu.

![Statistiche di memoria](media/gfx_diag_memory_statistics.png)

Il **GPU allocazione** colonna Visualizza la quantità di memoria utilizzata dall'evento visualizzato nella **evento** colonna.  È inoltre possibile selezionare l'icona di espressioni di controllo ![icona](media/gfx_watch.png) per visualizzare il [risorse cronologia](graphics-event-list.md#resource-history) per l'evento selezionato.

Come con lo strumento di statistiche di API, è possibile fare doppio clic nella finestra per copiare tutti i dati in formato CSV, che possono essere incollati in simile di Excel per un'ulteriore analisi.

## <a name="see-also"></a>Vedere anche  
[Diagnostica della grafica (debug grafica DirectX)](visual-studio-graphics-diagnostics.md)   
[Cronologia di risorse](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->