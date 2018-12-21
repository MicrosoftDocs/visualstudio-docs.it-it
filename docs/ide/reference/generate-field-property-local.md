---
title: Generare un campo, una proprietà, una variabile locale
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d3cd886e4ed08bbe4dbeea1b177dc4dd22502d99
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064034"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generare un campo, una proprietà o una variabile locale in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice per un campo, una proprietà o un elemento locale non dichiarato in precedenza.

**Quando:** si introduce un nuovo campo, proprietà o elemento locale durante la digitazione e si vuole dichiararlo in modo corretto, automaticamente.

**Perché:** si potrebbe dichiarare il campo, la proprietà o l'elemento locale prima dell'uso, tuttavia questa funzionalità genera la dichiarazione e il tipo automaticamente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa. La sottolineatura rossa indica un campo, una variabile locale o una proprietà che non esiste ancora.

   - C#:

       ![Codice evidenziato C#](media/field-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/field-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
      - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

      ![Anteprima della generazione di campo/proprietà/elemento locale](media/field-preview-cs.png)

3. Selezionare una delle opzioni di generazione dal menu a discesa.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

   Il campo, la proprietà o la variabile locale verrà creato con il tipo dedotto dal relativo utilizzo.

   - C#:

       ![Risultato della generazione del metodo C#](media/field-result-cs.png)

   - Visual Basic:

       ![Risultato della generazione del metodo VB](media/field-result-vb.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)