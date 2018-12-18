---
title: Effettuare il refactoring della firma di un metodo in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8358e14ccf9570207b3e52a552990fd2a3a80d49
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="change-a-method-signature-refactoring"></a>Refactoring con modifica della firma di un metodo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rimuovere o modificare l'ordine dei parametri di un metodo.

**Quando:** si vuole spostare o rimuovere un parametro di un metodo usato in varie posizioni.

**Motivo:** è possibile rimuovere e riordinare manualmente i parametri, per poi cercare tutte le chiamate al metodo e modificarle una alla volta, ma si tratta di un processo soggetto a errori.  Questo strumento di refactoring eseguirà l'attività automaticamente.

## <a name="how-to"></a>Procedura

1. Evidenziare o posizionare il cursore del testo all'interno del nome del metodo da modificare o un uno dei relativi utilizzi:

   - C#:

    ![Codice evidenziato C#](media/changesignature-highlight-cs.png)

   - VB:

    ![Codice evidenziato Visual Basic](media/changesignature-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+R** e quindi **CTRL+V**.  Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Cambia firma** dal popup della finestra di anteprima.
   - **Mouse**
     - Selezionare **Modifica > Refactoring > Rimuovi parametri**.
     - Selezionare **Modifica > Refactoring > Riordina parametri**.
     - Fare clic con il pulsante destro del mouse sul codice, scegliere il menu **Azioni rapide e refactoring** e selezionare **Cambia firma** dal popup della finestra di anteprima.

1. Nella finestra di dialogo **Modifica firma** visualizzata è possibile usare i pulsanti a destra per modificare la firma del metodo:

   ![Finestra di dialogo Cambia firma](media/changesignature-dialog-cs.png)

   | Button | Descrizione
   | ------ | ---
   | **Su/Giù** | Consente di spostare il parametro selezionato verso l'alto e verso il basso nell'elenco
   | **Rimuovi**  | Consente di rimuovere il parametro selezionato dall'elenco
   | **Recupera** | Consente di ripristinare il parametro selezionato e barrato nell'elenco

   > [!TIP]
   > Usare la casella di controllo **Anteprima modifiche riferimento** per [controllare il risultato in anteprima](../../ide/preview-changes.md) prima di eseguire il commit.

1. Al termine, fare clic sul pulsante **OK** per apportare le modifiche.

   - C#:

    ![Risultato della modifica della firma - C#](media/changesignature-result-cs.png)

   - Visual Basic:

    ![Risultato della modifica della firma - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)