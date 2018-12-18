---
title: Azioni rapide | Microsoft Docs
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 259e033aa32caaca59f37d7dc77ac095b4709878
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="quick-actions"></a>Azioni rapide

Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Sono disponibili azioni rapide per C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e i file di codice Visual Basic. Alcune azioni sono specifiche per un linguaggio e altre si applicano a tutti i linguaggi.

Le azioni rapide possono essere applicate tramite l'icona Lampadina ![Icona Lampadina piccola](media/vs2015_lightbulbsmall.png) o premendo **CTRL**+**.** quando il cursore si trova sulla riga di codice appropriata. La lampadina viene visualizzata se è presente una sottolineatura ondulata rossa e in Visual Studio è disponibile un suggerimento per correggere l'errore. Ad esempio, se è presente un errore indicato da una sottolineatura rossa ondulata, verrà visualizzata una lampadina quando sono disponibili correzioni per tale errore.

Nel caso in cui terze parti forniscano diagnostiche e suggerimenti personalizzati, ad esempio includendoli in SDK, per un qualsiasi linguaggio, le lampadine di Visual Studio si illumineranno sulla base di tali regole.

## <a name="to-see-a-light-bulb"></a>Per visualizzare una lampadina

1. In molti casi le lampadine vengono visualizzate spontaneamente quando si posiziona il puntatore del mouse su un errore oppure sul margine destro dell'editor, quando si sposta il cursore su una riga che contiene un errore. Quando è presente una sottolineatura ondulata rossa, è possibile passarvi sopra con il puntatore del mouse per visualizzare la lampadina. È anche possibile fare in modo che la lampadina venga visualizzata quando si usa il mouse o la tastiera per spostarsi nel punto della riga in cui si verifica l'errore.

1. Premere **CTRL**+**.** in un punto qualsiasi della riga per richiamare la lampadina e passare direttamente all'elenco delle correzioni potenziali.

   ![Lampadina con passaggio del mouse](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Per visualizzare le potenziali correzioni

Fare clic sulla freccia GIÙ o sul collegamento Mostra correzioni potenziali per visualizzare un elenco delle azioni rapide eseguibili automaticamente dalla lampadina.

![Lampadina espansa](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="see-also"></a>Vedere anche

[Generazione di codice in Visual Studio](../ide/code-generation-in-visual-studio.md)  
[Azioni rapide comuni](../ide/common-quick-actions.md)  
[Stili di codice e azioni rapide](../ide/code-styles-and-quick-actions.md)  
[Scrittura e refactoring del codice (C++)](/cpp/ide/writing-and-refactoring-code-cpp)