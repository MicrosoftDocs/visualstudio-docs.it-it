---
title: Generare una classe o un tipo
description: Informazioni su come usare il menu azioni rapide e refactoring per generare immediatamente il codice per una classe o un tipo.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 094dac3cea088bcede1ae251eec73c9741f6de6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897991"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generare una classe o un tipo in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice per una classe o un tipo.

**Quando:** si introduce una nuova classe o un nuovo tipo e si vuole dichiararlo in modo corretto, automaticamente.

**Perché:** si potrebbe dichiarare la classe o il tipo prima dell'uso, tuttavia questa funzionalità genera la classe o il tipo automaticamente.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa. La sottolineatura rossa indica una classe che non esiste ancora.

   - C#:

       ![Codice evidenziato C#](media/class-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/class-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina di errore](media/error-bulb.png) visualizzata.
      - Fare clic sull'icona ![lampadina di errore](media/error-bulb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

      ![Anteprima della generazione della classe](media/class-preview-cs.png)

3. Selezionare una delle opzioni dal menu a discesa:

   - Genera l'elemento classe '*NomeTipo*' nel nuovo file&mdash;Crea una classe denominata *NomeTipo* in un file denominato *NomeTipo*.cs/.vb
   - Genera la classe '*typeName*' &mdash; Crea una classe denominata *typeName* nel file corrente.
   - Genera la classe annidata '*typeName*' &mdash; Crea una classe denominata *typeName* annidata all'interno della classe corrente.
   - Genera nuovo tipo&mdash;Crea una nuova classe o un nuovo struct con tutte le proprietà specificate.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

4. Se si seleziona l'opzione **Genera nuovo tipo**, viene visualizzata la finestra di dialogo **Genera tipo**. Configurare l'accessibilità, il tipo e la posizione del nuovo tipo.

   ![Genera tipo](media/class-newtype-cs.png)

   Selezione | Descrizione
   --- | ---
   Access | Impostare il tipo per l'accesso *Predefinito*, *Interno* o *Pubblico*.
   Tipo | Può essere impostato come *classe* o *struct*.
   Nome | Questo non può essere modificato e sarà il nome già digitato.
   Project | Se sono presenti più progetti nella soluzione, è possibile scegliere il progetto in cui aggiungere la classe/lo struct.
   File Name | È possibile creare un nuovo file oppure è possibile aggiungere il tipo a un file esistente.

Vengono creati la classe o lo struct. Per C# viene creato anche un costruttore.

- C#

   ![Risultato della generazione della classe C#](media/class-result-cs.png)

- Visual Basic

   ![Risultato della generazione della classe VB](media/class-result-vb.png)

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
