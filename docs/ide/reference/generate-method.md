---
title: Generare un metodo in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c06aa8820635c876c05c6ac73c7de4c3c6581aa2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944739"
---
# <a name="generate-a-method-in-visual-studio"></a>Generare un metodo in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di aggiungere immediatamente un metodo a una classe.

**Quando:** si introduce un nuovo metodo e si vuole dichiararlo in modo corretto, automaticamente.

**Perché:** si potrebbero dichiarare il metodo e i parametri prima dell'uso, tuttavia questa funzionalità genera la dichiarazione automaticamente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa. La sottolineatura rossa indica un metodo che non esiste ancora.

   - C#:

    ![Codice evidenziato C#](media/method-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato VB](media/method-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Anteprima della generazione del metodo](media/method-preview-cs.png)

1. Selezionare **Genera metodo** dal menu a discesa.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

   Il metodo viene creato con gli eventuali parametri dedotti dal relativo utilizzo.

   - C#:

      ![Risultato della generazione del metodo C#](media/method-result-cs.png)

   - Visual Basic:

      ![Risultato della generazione del metodo VB](media/method-result-vb.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)