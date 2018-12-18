---
title: Azioni rapide | Microsoft Docs
ms.date: 03/28/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 941980eff8fc2474df9555b326278abdb9b26dac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quick-actions"></a>Azioni rapide

Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Sono disponibili azioni rapide per C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e i file di codice Visual Basic. Alcune azioni sono specifiche per un linguaggio e altre si applicano a tutti i linguaggi.

È possibile usare le azioni rapide per:

- Applicare una correzione del codice per la violazione di una regola dell'[analizzatore del codice](../code-quality/roslyn-analyzers-overview.md)
- [Eliminare](../code-quality/use-roslyn-analyzers.md) la violazione di una regola dell'analizzatore del codice
- Effettuare un refactoring (ad esempio [impostare come inline una variabile temporanea](../ide/reference/inline-temporary-variable.md))
- Generare codice (ad esempio [introdurre una variabile locale](../ide/reference/introduce-local-variable.md))

Le azioni rapide possono essere applicate tramite l'icona Lampadina ![Icona Lampadina piccola](media/vs2015_lightbulbsmall.png) o premendo **CTRL**+**.** quando il cursore si trova su una riga di codice per la quale è disponibile un'azione. La lampadina viene visualizzata se è presente una sottolineatura ondulata rossa e in Visual Studio è disponibile un suggerimento per correggere l'errore. Ad esempio, se è presente un errore indicato da una sottolineatura rossa ondulata, verrà visualizzata una lampadina quando sono disponibili correzioni per tale errore.

È possibile che fornitori terzi offrano diagnostiche e suggerimenti personalizzati per qualsiasi linguaggio, ad esempio includendoli in SDK: le lampadine di Visual Studio si illumineranno in base a tali regole.

## <a name="to-see-a-light-bulb"></a>Per visualizzare una lampadina

1. In molti casi le lampadine vengono visualizzate direttamente quando si posiziona il puntatore del mouse su un errore, oppure sul margine destro dell'editor quando si sposta il cursore su una riga che contiene un errore. Quando è presente una sottolineatura ondulata rossa, è possibile passarvi sopra con il puntatore del mouse per visualizzare la lampadina. È anche possibile fare in modo che la lampadina venga visualizzata quando si usa il mouse o la tastiera per spostarsi nel punto della riga in cui si verifica l'errore.

1. Premere **CTRL**+**.** in un punto qualsiasi della riga per richiamare la lampadina e passare direttamente all'elenco delle correzioni potenziali.

   ![Lampadina con passaggio del puntatore del mouse](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>Per visualizzare le potenziali correzioni

Fare clic sulla freccia GIÙ o sul collegamento Mostra correzioni potenziali per visualizzare un elenco delle azioni rapide eseguibili automaticamente dalla lampadina.

![Lampadina espansa](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Vedere anche

- [Generazione di codice in Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Azioni rapide comuni](../ide/common-quick-actions.md)
- [Stili di codice e azioni rapide](../ide/code-styles-and-quick-actions.md)
- [Scrittura e refactoring del codice (C++)](/cpp/ide/writing-and-refactoring-code-cpp)