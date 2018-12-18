---
title: Refactoring con estrazione di un'interfaccia in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7abdc017c4d57e17685671539a4b053e6241b424
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extract-an-interface-refactoring"></a>Refactoring con estrazione di un'interfaccia

Questo refactoring si applica a:

- C#

- Visual Basic

**Novità:** consente di creare un'interfaccia usando membri esistenti da una classe, uno struct o un'interfaccia.

**Quando:** sono disponibili più classi, struct o interfacce con metodi che potrebbero essere resi comuni e usati da altre classi, altri struct o altre interfacce.

**Perché:** le interfacce sono costrutti ideali per le progettazioni orientate agli oggetti. Si supponga di avere classi per vari animali (Cane, Gatto, Uccello) che potrebbero contenere tutte metodi comuni, come Mangiare, Bere, Dormire. L'uso di un'interfaccia come IAnimali consentirebbe alle classi Cane, Gatto e Uccello di avere una "firma" comune per questi metodi.

## <a name="how-to"></a>Procedura

1. Evidenziare il nome della classe su cui eseguire l'azione oppure posizionare semplicemente il cursore del testo in un punto nel nome della classe.

   - C#:

    ![Codice evidenziato - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato - Visual Basic](media/extractinterface-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+R** e quindi **CTRL+I**. Si noti che i tasti di scelta rapida possono essere diversi a seconda del profilo selezionato.
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.
   - **Mouse**
     - Selezionare **Modifica > Refactoring - Estrai interfaccia**.
     - Fare clic con il pulsante destro del mouse sul nome della classe, scegliere il menu **Azioni rapide e refactoring** e selezionare **Estrai interfaccia** dal popup della finestra di anteprima.

1. Nella finestra di dialogo **Estrai interfaccia** visualizzata immettere le informazioni richieste:

   ![Estrai interfaccia](media/extractinterface-dialog-cs.png)

   | Campo | Descrizione |
   | --- | --- |
   | **Nome nuova interfaccia** | Nome dell'interfaccia da creare. Il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Nome nuovo file** | Nome del file che verrà generato e conterrà l'interfaccia. Come per l'interfaccia, il nome predefinito è *NomeClasse*, dove *NomeClasse* è il nome della classe selezionata in precedenza. |
   | **Seleziona i membri pubblici per l'interfaccia** | Elementi da estrarre nell'interfaccia. È possibile selezionarne il numero desiderato. |

1. Scegliere **OK**.

   L'interfaccia viene creata nel file con il nome specificato. Inoltre, la classe selezionata implementa tale interfaccia.

   - C#:

    ![Classe risultante - C#](media/extractinterface-class-cs.png)
    ![Interfaccia risultante - C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

    ![Classe risultante - Visual Basic](media/extractinterface-class-vb.png)
    ![Interfaccia risultante - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)