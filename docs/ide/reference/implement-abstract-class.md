---
title: Implementare una classe astratta in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: ecb86d6870e4a9d67e5994e33098a7d964d24410
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementare una classe astratta in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice necessario per implementare una classe astratta.

**Quando:** si vuole ereditare da una classe astratta.

**Perché:** è possibile implementare manualmente tutti i membri astratti, uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica l'ereditarietà da una classe astratta, ma che non sono stati implementati tutti i membri obbligatori.

   - C#:

    ![Codice evidenziato C#](media/abstract-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato VB](media/abstract-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima dell'implementazione della classe](media/abstract-preview-cs.png)

1. Scegliere **Implementa classe astratta** dal menu a discesa.

   > [!TIP]
   > - Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.
   > - Usare i collegamenti **Documento**, **Progetto** e **Soluzione** nella parte inferiore della finestra di anteprima per creare le firme dei metodi appropriate per più classi che ereditano dalla classe astratta.

   Le firme dei metodi astratti vengono create e sono pronte per l'implementazione.

   - C#:

      ![Risultato dell'implementazione della classe C#](media/abstract-result-cs.png)

   - Visual Basic:

      ![Risultato dell'implementazione della classe VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
