---
title: Generare override dei metodi Equals e GetHashCode C# in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3768659ce6c4e52c9e4f6473207fc74513797f17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generare override dei metodi Equals e GetHashCode in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare override dei metodi **Equals** e **GetHashCode**.

**Quando:** generare questi override quando si dispone di un tipo che deve essere confrontato in base a uno o più campi, invece che in base alla posizione dell'oggetto in memoria.

**Perché?:**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Se si implementa un tipo riferimento, è consigliabile eseguire l'override del metodo **Equals**, se il tipo è simile a un tipo di base, ad esempio Point, String, BigNumber e così via.

- Eseguire l'override del metodo **GetHashCode** per consentire il funzionamento corretto di un tipo in una tabella hash. Leggere ulteriori informazioni sugli [operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella dichiarazione del tipo.

   ![Codice evidenziato](media/overrides-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la dichiarazione del tipo.

   ![Anteprima della generazione di override](media/overrides-preview-cs.png)

1. Scegliere **Genera Equals(oggetto)** o **Genera Equals e GetHashCode** dal menu a discesa.

1. Nella finestra di dialogo **Seleziona membri** selezionare i membri per cui si vogliono generare i metodi:

    ![Finestra di dialogo di generazione degli override](media/overrides-dialog-cs.png)

    > [!TIP]
    > È anche possibile scegliere di generare gli operatori da questa finestra di dialogo usando le caselle di controllo sotto l'elenco dei membri.

   Gli override per Equals e GetHashCode vengono generati con le implementazioni predefinite.

   ![Risultato della generazione del metodo](media/overrides-result-cs.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
