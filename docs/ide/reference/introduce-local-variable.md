---
title: Introdurre una variabile locale in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 997220d3b1a7305f84f61ee5fd4c205d1157f1b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introdurre una variabile locale in Visual Studiio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente una variabile locale per sostituire un'espressione esistente.

**Quando:** si dispone di codice che potrebbe essere facilmente riutilizzato in un secondo momento se fosse in una variabile locale.

**Perché:** è possibile copiare e incollare il codice più volte per usarlo in varie posizioni, ma sarebbe preferibile eseguire l'operazione una sola volta, archiviare il risultato in una variabile locale e usare poi la variabile locale.

## <a name="how-to"></a>Procedura

1. Evidenziare l'espressione che si vuole assegnare a una nuova variabile locale.

   - C#:

    ![Codice evidenziato C#](media/local-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato VB](media/local-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima di Introduce l'elemento locale](media/local-preview-cs.png)

1. Scegliere **Introduce la variabile locale per tutte le occorrenze di '*espressione*'** dal menu a discesa.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

   La variabile locale viene creata con il tipo dedotto dal relativo utilizzo. Assegnare alla nuova variabile locale un nuovo nome.

   - C#:

      ![Risultato di implementazione dell'interfaccia C#](media/local-result-cs.png)

   - Visual Basic:

      ![Risultato di implementazione dell'interfaccia VB](media/local-result-vb.png)

   > [!NOTE]
   > È possibile usare l'opzione di menu **....tutte le occorrenze di...** per sostituire ogni istanza dell'espressione selezionata e non solo quella evidenziata in modo specifico.

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
