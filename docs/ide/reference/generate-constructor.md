---
title: Generare un costruttore in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8ab26fd6ccc8359c2699154ae6fa5821040ce9ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generare un costruttore in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice per un nuovo costruttore in una classe.

**Quando:** si introduce un nuovo costruttore e si vuole dichiararlo in modo corretto, automaticamente, oppure si vuole modificare un costruttore esistente.

**Perché:** si potrebbe dichiarare il costruttore prima di usarlo, tuttavia questa funzionalità consente di generarlo automaticamente, con i parametri appropriati. Inoltre, la modifica di un costruttore esistente richiede l'aggiornamento di tutti i siti di chiamata, a meno che non si usi questa funzionalità per aggiornarli automaticamente.

**Procedura:** esistono diversi modi per generare un costruttore:

   - [Generare un costruttore e selezionare i membri](#pick)
   - [Generare un costruttore dai campi selezionati](#selection)
   - [Generare un costruttore da un nuovo utilizzo](#usage)
   - [Aggiungere un parametro a un costruttore esistente](#addparameter)
   - [Creare e inizializzare un campo/una proprietà dal parametro di un costruttore](#create)

## <a id = "pick"></a> Generare un costruttore e selezionare i membri (solo C#)

1. Posizionare il cursore in qualsiasi riga vuota in una classe:

   ![Cursore in una riga vuota](media/constructor1-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga vuota nella classe.

   ![Anteprima della generazione di un costruttore](media/constructor1-preview-cs.png)

1. Scegliere **Genera il costruttore** dal menu a discesa.

   Verrà visualizzata la finestra di dialogo **Seleziona membri**.

1. Selezionare i membri da includere come parametri del costruttore. È possibile ordinarli tramite le frecce su e giù. Scegliere **OK**.

   ![Finestra di dialogo Seleziona membri](media/constructor1-dialog-cs.png)

   > [!TIP]
   > È possibile selezionare la casella di controllo **Aggiungi i controlli Null** per generare automaticamente i controlli Null per i parametri del costruttore.

   Il costruttore viene creato con i parametri specificati.

   ![Risultato della generazione del costruttore](media/constructor1-result-cs.png)

## <a id="selection"></a> Generare un costruttore dai campi selezionati (solo C#)

1. Evidenziare i membri che si desidera includere nel costruttore generato:

   ![Evidenziare i membri](media/constructor2-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la selezione.

     ![Anteprima della generazione di un costruttore](media/constructor2-preview-cs.png)

1. Scegliere **Genera il costruttore 'NomeTipo(...)'** dal menu a discesa.

   Il costruttore viene creato con i parametri selezionati.

   ![Risultato della generazione del costruttore](media/constructor2-result-cs.png)

## <a id="usage"></a> Generare un costruttore da un nuovo utilizzo (C# e Visual Basic)

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa. La sottolineatura rossa indica una chiamata a un costruttore che non esiste ancora.

   - C#:

    ![Codice evidenziato C#](media/constructor-highlight-cs.png)

   - Visual Basic:

    ![Codice evidenziato VB](media/constructor-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Anteprima della generazione di un costruttore](media/constructor-preview-cs.png)

1. Scegliere **Genera il costruttore in '*NomeTipo*'** dal menu a discesa.

   > [!TIP]
   > Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.

   Il costruttore viene creato con gli eventuali parametri dedotti dal relativo utilizzo.

   - C#:

      ![Risultato della generazione del metodo C#](media/constructor-result-cs.png)

   - Visual Basic:

      ![Risultato della generazione del metodo VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> Aggiungere un parametro a un costruttore esistente (solo C#)

1. Aggiungere un parametro a una chiamata di un costruttore esistente.

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato usato un costruttore che non esiste ancora.

    ![Evidenziazione per generare un costruttore](media/constructor4-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Anteprima della generazione di un costruttore](media/constructor4-preview-cs.png)

1. Scegliere **Aggiungi il parametro a 'NomeTipo(...)'** dal menu a discesa.

   Il parametro viene aggiunto al costruttore, con il tipo dedotto dal relativo utilizzo.

   ![Risultato della generazione del costruttore](media/constructor4-result-cs.png)

## <a id="create"></a> Creare e inizializzare un campo o una proprietà dal parametro di un costruttore (solo C#)

1. Trovare un costruttore esistente e aggiungere un parametro:

   ![Evidenziazione per generare un costruttore](media/constructor5-highlight-cs.png)

1. Posizionare il cursore all'interno del parametro appena aggiunto.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
     - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
     - Fare clic sul pulsante ![lampadina](media/bulb-cs.png) visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con il parametro aggiunto.

   ![Anteprima della generazione di un costruttore](media/constructor5-preview-cs.png)

1. Scegliere **Crea e inizializza la proprietà** o **Crea e inizializza il campo** dal menu a discesa.

   Il campo o la proprietà viene dichiarato e denominato automaticamente in base ai tipi. Viene anche aggiunta una riga di codice per inizializzare il campo o la proprietà nel corpo del costruttore.

   ![Risultato della generazione del costruttore](media/constructor5-result-cs.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)