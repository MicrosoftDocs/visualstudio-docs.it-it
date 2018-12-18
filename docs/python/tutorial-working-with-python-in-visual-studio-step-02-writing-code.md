---
title: Utilizzo di Python in Visual Studio, Passaggio 2, Scrittura ed esecuzione del codice | Microsoft Docs
description: "Passaggio 2 di un'esercitazione di base per l'utilizzo di Python all'interno di Visual Studio, su come modificare ed eseguire un semplice programma Hello World, seguito da codice più interessante che illustra le funzionalità di modifica e IntelliSense di Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: d1ca877c08e336fb9b62e037f94fadcbb9380f29
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="step-2-writing-and-running-code"></a>Passaggio 2: Scrittura ed esecuzione del codice

**Passaggio precedente: [Creazione di un nuovo progetto Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Anche se Esplora soluzioni si trova nell'area di gestione dei file di progetto, la finestra *editor* si trova in genere dove si lavora con i *contenuti* dei file, come il codice sorgente. L'editor è sensibile al contesto del tipo di file che si sta modificando, anche per quanto riguarda il linguaggio di programmazione (in base all'estensione del file) e offre le funzionalità appropriate per tale linguaggio, come la colorazione della sintassi e il completamento automatico tramite IntelliSense.

1. Dopo aver creato un nuovo progetto "Python Application" (Applicazione Python), nell'editor di Visual Studio viene aperto un file vuoto predefinito denominato `PythonApplication1.py`.

1. Nell'editor iniziare a digitare `print("Hello, Visual Studio")`. Si noti che IntelliSense di Visual Studio visualizza le opzioni di completamento automatico durante la digitazione. L'opzione con contorno nell'elenco a discesa è il completamento predefinito usato quando si preme TAB. Il completamento è utile soprattutto in presenza di istruzioni o identificatori più lunghi.

    ![Popup di completamento automatico IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. In IntelliSense vengono mostrate informazioni diverse a seconda dell'istruzione usata, della funzione chiamata e così via. Con la funzione `print`, digitare `(` dopo `print` per indicare che una chiamata di funzione consente di visualizzare informazioni complete sull'uso di tale funzione. Il popup IntelliSense visualizza anche l'argomento corrente in grassetto (**valore** come illustrato di seguito):

    ![Popup di completamento automatico IntelliSense per una funzione](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Completare l'istruzione in modo che corrisponda alla seguente:

    ```python
    print("Hello, Visual Studio")
    ```

1. Si noti la colorazione della sintassi che consente di distinguere l'istruzione `print` dall'argomento `"Hello Visual Studio"`. Inoltre, eliminare temporaneamente l'ultimo elemento `"` nella stringa. Si noti come Visual Studio visualizza una sottolineatura rossa per il codice che contiene errori di sintassi. Quindi sostituire `"` per correggere il codice.

    ![Colorazione della sintassi ed evidenziazione degli errori di IntelliSense](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Poiché l'ambiente di sviluppo è molto personale, Visual Studio offre un controllo completo sull'aspetto e sul comportamento di Visual Studio. Selezionare il comando del menu **Strumenti > Opzioni** ed esplorare le impostazioni nelle schede **Ambiente** e **Editor di testo**. Per impostazione predefinita viene visualizzato solo un numero limitato di opzioni. Per visualizzare tutte le opzioni per ogni linguaggio di programmazione, selezionare **Mostra tutte le impostazioni** nella parte inferiore della finestra di dialogo. 

1. Successivamente a questo punto eseguire il codice già scritto premendo Ctrl+F5 o selezionando la voce del menu **Debug > Avvia senza eseguire debug**. Se sono ancora presenti errori nel codice Visual Studio genera degli avvisi.

1. Quando si esegue il programma, viene visualizzata una finestra di console con i risultati, come se fosse stato eseguito un interprete Python con `PythonApplication1.py` dalla riga di comando. Premere un tasto per chiudere la finestra e tornare all'editor di Visual Studio.

    ![Output per la prima esecuzione del programma](media/vs-getting-started-python-07-output.png)

1. Oltre ai completamenti per istruzioni e funzioni, IntelliSense offre completamenti per le istruzioni `import` e `from` di Python. I completamenti delle istruzioni consentono di individuare facilmente i moduli disponibili nell'ambiente e i membri disponibili in ogni modulo. Nell'editor eliminare la riga `print` e iniziare a digitare `import `. Quando si preme la barra spaziatrice, viene visualizzato un elenco dei moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione import](media/vs-getting-started-python-08-import1.png)

1. Completare la riga digitando o selezionando `sys`.

1. Nella riga successiva digitare `from` per visualizzare nuovamente un elenco di moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione from](media/vs-getting-started-python-09-import2.png)

1. Selezionare o digitare `math`, quindi continuare a digitare uno spazio e `import` per visualizzare i membri del modulo:

    ![IntellSense che mostra i membri del modulo](media/vs-getting-started-python-10-import3.png)

1. Completare l'importazione dei membri `sin`, `cos` e `radians`, osservando i completamenti automatici disponibili per ogni membro. Al termine, il codice dovrebbe essere simile al seguente:

    ```python
    import sys
    from math import sin, cos, radians
    ```

    > [!Tip]
    > I completamenti si basano su sottostringhe durante la digitazione, cercando corrispondenze per parti di parole, lettere all'inizio delle parole e anche caratteri saltati. Per altri dettagli, vedere [Modifica del codice - Completamenti](editing-python-code-in-visual-studio.md#completions).

1. Aggiungere altro codice per visualizzare i valori di coseno per 360 gradi:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Eseguire ancora il programma premendo Ctrl+F5 o scegliendo **Debug > Avvia senza eseguire debug**. Al termine, chiudere la finestra di output.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Uso della finestra interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="going-deeper"></a>Approfondimenti

- [Modifica di codice R in Visual Studio](editing-python-code-in-visual-studio.md)
- [Formattazione del codice](formatting-python-code.md)
- [Refactoring del codice](refactoring-python-code.md)
- [Uso di PyLint](linting-python-code.md)
