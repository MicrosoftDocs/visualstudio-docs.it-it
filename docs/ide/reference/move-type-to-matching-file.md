---
title: Refactoring con spostamento di un tipo in un file corrispondente in Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4cabe20e6cf84b69bf711831d1a402f67fd908c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactoring con spostamento di un tipo in un file corrispondente

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di spostare il tipo selezionato in un file distinto con lo stesso nome.

**Quando:** sono presenti più classi, struct, interfacce e così via nello stesso file e si vuole separarli.

**Perché:** l'inserimento di più tipi nello stesso file può rendere difficile l'individuazione di questi tipi. Con lo spostamento dei tipi in file con lo stesso nome, il codice diventa più leggibile e la navigazione più semplice.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore del testo all'interno del nome del tipo da spostare:

   - C#:

    ![Codice evidenziato - C#](media/movetype-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato - Visual Basic](media/movetype-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sposta il tipo in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sposta il tipo in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.

   Il tipo viene spostato in un nuovo file con lo stesso nome, come parte della soluzione.

   - C#:

    ![Risultato inline - C#](media/movetype-result-cs.png)

   - Visual Basic:

    ![Risultato inline - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)