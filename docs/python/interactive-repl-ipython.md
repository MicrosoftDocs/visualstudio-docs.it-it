---
title: REPL IPython (finestra interattiva) | Microsoft Docs
description: Utilizzo della finestra interattiva di Visual Studio in modalità IPython per un ambiente di sviluppo interattivo intuitivo e semplice da usare con funzionalità di elaborazione parallela interattiva.
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 76f34e28e35af00ed6352177a00f669b351058d1
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="using-ipython-in-the-interactive-window"></a>Uso di IPython nella finestra interattiva

La finestra interattiva di Visual Studio in modalità IPython costituisce un ambiente di sviluppo interattivo avanzato e al contempo intuitiva avanzato e semplice da usare che include funzionalità di elaborazione parallela interattiva. Questo articolo illustra l'uso di IPython nella finestra interattiva di Visual Studio, in cui sono anche disponibili tutte le funzionalità della [finestra interattiva](python-interactive-repl-in-visual-studio.md) normale.

Per questa procedura dettagliata è necessario aver installato l'ambiente [Anaconda](https://www.continuum.io), che include IPython e le librerie necessarie.

> [!Note]
> IronPython non supporta IPython, anche se è possibile selezionarlo nel modulo delle opzioni interattive. Per altre informazioni, vedere la pagina relativa alla [richiesta di funzionalità](https://github.com/Microsoft/PTVS/issues/84).

1. Aprire Visual Studio, passare alla finestra Ambienti Python (**Visualizza > Altre finestre > Ambienti Python**) e selezionare l'ambiente Python visualizzato all'avvio di IPython.

1. Osservare la scheda **Pacchetti** (o **pip**) e verificare che siano elencati `IPython` e `matplotlib`. In caso contrario, installarli qui.

1. Selezionare la scheda **Panoramica** e quindi **Usa la modalità interattiva IPython.** In Visual Studio 2015 selezionare **Configure interactive options** (Configura opzioni interattive) per aprire la finestra di dialogo **Opzioni** e quindi impostare **Modalità interattiva** su IPython e selezionare **OK**.

1. Selezionare **Apri finestra interattiva** per visualizzare la finestra interattiva in modalità IPython. Potrebbe essere necessario reimpostare la finestra se è stata modificata solo la modalità interattiva. Potrebbe anche essere necessario premere INVIO se viene visualizzato solo un prompt >>>.

    ![Finestra interattiva in modalità IPython](media/ipython-repl-03.png)

1. Immettere il codice seguente:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Dopo aver immesso l'ultima riga, verrà visualizzato un grafico inline, che è possibile ridimensionare trascinando nell'angolo inferiore destro se si desidera.

    ![Grafico inline nella finestra interattiva](media/ipython-repl-04.png)

1. Invece di digitare in REPL, è possibile scrivere codice nell'editor, selezionarlo, fare clic con il pulsante destro del mouse e scegliere il comando **Invia a Interactive** o premere CTRL+INVIO. Provare a incollare il codice seguente in un nuovo file nell'editor, selezionandolo con CTRL+A e quindi inviandolo alla finestra interattiva. Si noti che Visual Studio invia il codice alla finestra in un unico blocco per evitare che vengano visualizzati grafici intermedi o parziali. Si noti anche che, se non è aperto un progetto di Python con un altro ambiente selezionato, Visual Studio apre una finestra interattiva per qualsiasi ambiente sia selezionato come predefinito nella finestra **Ambienti Python**.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Invio di codice dall'editor alla finestra interattiva](media/ipython-repl-05.png)

1. Per visualizzare i grafici all'esterno della finestra interattiva, eseguire il codice invece di usare il comando **Debug > Avvia senza eseguire debug**.

In IPython sono disponibili molte altre funzionalità utili, ad esempio l'escape alla shell di sistema, la sostituzione delle variabili, l'acquisizione di output e così via. Per altre informazioni, vedere la [documentazione di IPython](http://ipython.org/documentation.html).

## <a name="related-articles"></a>Articoli correlati

- Per usare Jupyter facilmente e senza installazione, provare la versione gratuita del [servizio ospitato Azure Notebooks](https://notebooks.azure.com/) che consente di mantenere e condividere i blocchi appunti con altri utenti.

- È anche possibile eseguire Jupyter (precedentemente noto come IPython) nella propria macchina virtuale Windows o Linux in Azure. Per informazioni dettagliate, vedere [Creazione di una macchina virtuale di Azure, installazione di Jupyter ed esecuzione di Jupyter Notebook in Azure](/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).
