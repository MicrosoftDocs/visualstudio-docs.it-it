---
title: Rinominare un file in modo che corrisponda a un tipo in Visual Studio | Microsoft Docs
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
ms.openlocfilehash: accc8e0934ca18eb72cec03de4a53bb070fedef2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refactoring con sincronizzazione di un tipo con un nome di file o un nome di file con un tipo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rinominare un tipo in modo che corrisponda al nome del file oppure di rinominare un file in modo che corrisponda al tipo che contiene.

**Quando:** è stato rinominato un file o un tipo e non è ancora stato aggiornato il file o il nome corrispondente.

**Perché:** se si inserisce un tipo in un file con un nome diverso o viceversa, risulta difficile trovare ciò che si sta cercando. Rinominando il tipo o il file, il codice diventa più leggibile e la navigazione più semplice.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore del testo all'interno del nome del tipo da sincronizzare:

   - C#:

    ![Codice evidenziato - C#](media/synctype-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato - Visual Basic](media/synctype-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rinomina file in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rinomina tipo in _NomeFile_** dal popup della finestra di anteprima, dove *NomeFile* è il nome del file corrente.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Rinomina file in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.
     - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Rinomina tipo in _NomeFile_** dal popup della finestra di anteprima, dove *NomeFile* è il nome del file corrente.

   Il tipo o il file viene rinominato.

   - C#: nell'esempio seguente il file **MyClass.cs** è stato rinominato in **MyNewClass.cs** in modo che corrisponda al nome del tipo.

      ![Risultato inline C#](media/synctype-result-cs.png)

   - Visual Basic: nell'esempio seguente il file **Employee.vb** è stato rinominato in **Person.vb** in modo che corrisponda al nome del tipo.

      ![Risultato inline Visual Basic](media/synctype-result-vb.png)

> ![NOTA] Questo refactoring non è ancora disponibile per i progetti .NET Standard e .NET Core.

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)
