---
title: Generare una classe o un tipo in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 77b6feef7556950d121e462cb1e8e81e8c4bfe7f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generare una classe o un tipo in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice per una classe o un tipo.

**Quando:** si introduce una nuova classe o un nuovo tipo e si vuole dichiararlo in modo corretto, automaticamente.

**Perché:** si potrebbe dichiarare la classe o il tipo prima dell'uso, tuttavia questa funzionalità genera la classe o il tipo automaticamente.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa. La sottolineatura rossa indica una classe che non esiste ancora.

   - C#:

    ![Codice evidenziato C#](media/class-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato VB](media/class-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Anteprima della generazione della classe](media/class-preview-cs.png)

1. Selezionare una delle opzioni dal menu a discesa:

   - Genera l'elemento classe '*NomeTipo*' nel nuovo file&mdash;Crea una classe denominata *NomeTipo* in un file denominato *NomeTipo*.cs/.vb
   - Genera l'elemento classe '*NomeTipo*'&mdash;Crea una classe denominata *NomeTipo* nel file corrente.
   - Genera l'elemento classe '*NomeTipo*' annidato&mdash;Crea una classe denominata *NomeTipo* annidata nella classe corrente.
   - Genera nuovo tipo&mdash;Crea una nuova classe o un nuovo struct con tutte le proprietà specificate.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

1. Se si seleziona l'opzione **Genera nuovo tipo** verrà visualizzata la finestra di dialogo **Genera tipo**. Configurare l'accessibilità, il tipo e la posizione del nuovo tipo.

   ![Genera tipo](media/class-newtype-cs.png)

   Selection | Descrizione
   --- | ---
   Accedi a | Impostare il tipo per l'accesso *Predefinito*, *Interno* o *Pubblico*.
   Kind | Può essere impostato come *classe* o *struct*.
   nome | Questo non può essere modificato e sarà il nome già digitato.
   Progetto | Se sono presenti più progetti nella soluzione, è possibile scegliere il progetto in cui aggiungere la classe/lo struct.
   Nome file | È possibile creare un nuovo file oppure è possibile aggiungere il tipo a un file esistente.

Vengono creati la classe o lo struct. Per C# viene creato anche un costruttore.

- C#

   ![Risultato della generazione della classe C#](media/class-result-cs.png)

- Visual Basic

   ![Risultato della generazione della classe VB](media/class-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)