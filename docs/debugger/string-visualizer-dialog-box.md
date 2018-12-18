---
title: Visualizzare le stringhe in un visualizzatore di stringhe | Documenti Microsoft
ms.custom: 
ms.date: 07/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 801618c900f11a562b42e610c56dfa7855dfaf39
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visualizza le stringhe in un visualizzatore di stringhe in Visual Studio
Durante il debug, è possibile aprire un visualizzatore di stringhe per le stringhe di visualizzazione che sono troppo lungo da visualizzare in una finestra del debugger o suggerimento dati. In molti scenari, il Visualizzatore consente di identificare le stringhe di formato non valido.

I visualizzatori standard stringa predefinite includono JSON, XML, HTML e testo normale. Per alcuni altri tipi, ad esempio oggetti WPF visualizzati nel debugger di windows come il **Auto** finestra, è anche possibile aprire i visualizzatori.

## <a name="open-a-string-visualizer"></a>Aprire un visualizzatore di stringhe

Per visualizzare un testo normale, la stringa JSON, XML o HTML, fare clic sull'icona di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") durante il passaggio del mouse su una variabile che contiene un valore stringa. È necessario che sia sospesa nel debugger per visualizzare l'icona di lente di ingrandimento.

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Dati di stringa di visualizzazione

Il **espressione** campo nel Visualizzatore di stringa viene visualizzata la variabile corrente o l'espressione al passaggio del mouse nel debugger.

Il **valore** campo Mostra il valore stringa. Il Visualizzatore di testo Mostra il testo normale.

Un valore vuoto **valore** indica che il visualizzatore specifico sia in grado di riconoscere il tipo di stringa. Ad esempio, il visualizzatore XML mostra un valore vuoto **valore** per una stringa di testo (con nessun tag XML) o un formato JSON stringa formattata. Se si desidera visualizzare una stringa non riconoscibile in un visualizzatore, è possibile usare il Visualizzatore di testo.

### <a name="view-json-string-data"></a>Visualizza i dati di stringa JSON

Una stringa JSON in formato corretto sarà simile alla figura riportata di seguito nel Visualizzatore di JSON. JSON in formato non corretto può visualizzare un'icona di errore (o vuoto se non riconosciuto).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore stringhe JSON")

### <a name="view-xml-string-data"></a>Dati di stringa di visualizzazione XML

Una stringa XML ben formata sarà simile alla figura riportata di seguito nel visualizzatore XML. XML non valido potrebbe essere visualizzato senza il tag XML (o vuoto se non riconosciuto).

![Visualizzatore di stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore stringhe XML")

### <a name="view-html-string-data"></a>Dati di stringa di visualizzazione HTML

Una stringa HTML ben formata è simile alla visualizzazione che è possibile visualizzare se la stringa viene eseguito il rendering in un browser, come illustrato nella figura seguente. Codice HTML non corretto può essere visualizzato come testo normale.

![Visualizzatore di stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "visualizzatore HTML di stringhe")

## <a name="see-also"></a>Vedere anche  
 [Creazione di visualizzatori personalizzati (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)