---
title: Introduzione a R in Visual Studio | Microsoft Docs
description: Procedura dettagliata per l'uso di R in Visual Studio, tra cui la creazione del progetto, la finestra interattiva, la modifica del codice e il debug.
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 202fd9d7d644eabf9962d68f83d3daa0ab854005
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="getting-started-with-r-tools-for-visual-studio"></a>Introduzione a R Tools per Visual Studio

Dopo aver installato R Tools per Visual Studio (RTVS), da [How to install R Tools for Visual Studio](installing-r-tools-for-visual-studio.md) (Procedura: Installare R Tools per Visual Studio), è possibile farsi rapidamente un'idea dell'esperienza offerta da tali strumenti. 

## <a name="create-an-r-project"></a>Creare un progetto R

1. Avviare Visual Studio.
1. Scegliere **File > Nuovo > Progetto** (CTRL+MAIUSC+N)
1. Selezionare "Progetto R" in **Modelli > R**, assegnare un nome e un percorso al progetto e selezionare **OK**:

   ![Finestra di dialogo Nuovo progetto per R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

1. Dopo che il progetto è stato creato, sono visualizzate le finestre seguenti:

    - A destra in Esplora soluzioni di Visual Studio viene visualizzato il progetto all'interno di una *soluzione*. Le soluzioni possono contenere un numero qualsiasi di progetti di tipi diversi. Per altri dettagli, vedere [Creating R projects in Visual Studio](r-projects-in-visual-studio.md) (Creazione di progetti R in Visual Studio).
    - In alto a sinistra viene visualizzato un nuovo file di R (`script.R`) in cui è possibile modificare il codice sorgente con tutte le funzionalità di modifica di Visual Studio.
    - In basso a sinistra viene visualizzata la finestra **R interattivo** in cui è possibile sviluppare e testare il codice in modo interattivo.

> [!Note]
> È possibile usare la finestra **R interattivo** senza che vi siano progetti aperti e anche quando è stato caricato un tipo di progetto diverso. È sufficiente selezionare in qualsiasi momento **R Tools > Windows > R interattivo**.

## <a name="explore-the-interactive-window-and-intellisense"></a>Esplorare la finestra interattiva e IntelliSense

1. Accertarsi che la finestra interattiva funzioni digitando `3 + 4` e quindi scegliendo INVIO per visualizzare il risultato:

    ![Finestra R interattivo in Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Immettere un codice un po' più complicato, `ds <- c(1.5, 6.7, 8.9) * 1:12`, e immettere `ds` per visualizzare il risultato:

    ![Altro esempio interattivo per R in Visual Studio](media/getting-started-03-interactive2.png)

1. Digitare `mean(ds)`. Si noti tuttavia che non appena si digita `m` o `me`, Visual Studio IntelliSense visualizza alcune opzioni di completamento automatico. Quando viene selezionato il completamento che si vuole scegliere nell'elenco, premere TAB per inserirlo. È possibile modificare la selezione con il mouse o i tasti di direzione.

    ![Visualizzazione di IntelliSense quando si immette codice](media/getting-started-04-intellisense1.png)

1. Dopo aver completato `mean`, digitare la parentesi aperta `(`. Si noterà che IntelliSense visualizza la Guida in linea per la funzione:

    ![IntelliSense visualizza la Guida in linea per una funzione](media/getting-started-05-intellisense2.png)

1. Completare la riga `mean(ds)` e premere INVIO per visualizzare il risultato (`[1] 39.51667`).

1. La finestra interattiva è integrata con la Guida, quindi se si immette `?mean`, viene visualizzata la Guida per tale funzione nella finestra **Guida di R** in Visual Studio. Per i dettagli, vedere [Guida di R Tools per Visual Studio](getting-started-help.md).

    ![Finestra Guida di R in Visual Studio](media/getting-started-06-help.png)

1. Alcuni comandi, ad esempio `plot(1:100)`, aprono una nuova finestra in Visual Studio quando non è possibile visualizzare l'output direttamente nella finestra interattiva:

    ![Visualizzazione di un tracciato in Visual Studio](media/getting-started-07-plot-window.png)

La finestra interattiva consente anche di rivedere la cronologia, caricare e salvare le aree di lavoro, collegarsi a un debugger e interagire con i file di codice sorgente anziché usare operazioni di copia e incolla. Per altri dettagli, vedere [Uso della finestra R interattivo](interactive-repl-for-r-in-visual-studio.md).

## <a name="experience-code-editing-features"></a>Scoprire le funzionalità di modifica del codice

L'uso anche per poco tempo della finestra interattiva consente di entrare in contatto con funzionalità di modifica di base, come IntelliSense, che possono essere usate anche nell'editor di codice. Se si immette lo stesso codice usato in precedenza, si notano gli stessi prompt di completamento automatico e di IntelliSense, ma non lo stesso output.

Se si scrive il codice in un file `.R`, è possibile visualizzare tutto il codice in una sola volta ed è quindi più facile apportare piccole modifiche e visualizzarne il risultato eseguendo rapidamente il codice nella finestra interattiva. È anche possibile avere quanti file si voglia in un solo progetto. Quando il codice si trova in un file è anche possibile eseguirlo un'istruzione per volta nel debugger, come illustrato più avanti in questo articolo. Queste funzionalità sono utili quando si sviluppano algoritmi di calcolo e si scrive codice per modificare uno o più set di dati, soprattutto se si vogliono esaminare tutti i risultati intermedi.

Ad esempio, la procedura seguente crea un breve codice per esplorare i [teoremi centrali del limite](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). Questo esempio è stato adattato da *R Cookbook* di Paul Teetor.

1. Nell'editor `script.R` immettere il codice seguente:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Per visualizzare rapidamente i risultati, selezionare tutto il codice, premendo CTRL + A, e premere CTRL + INVIO o fare clic con il pulsante destro del mouse e scegliere **Esegui in finestra interattiva**. Tutto il codice selezionato viene eseguito nella finestra interattiva come se fosse stato digitato direttamente. Il risultato viene poi visualizzato in una finestra dei tracciati:

    ![Visualizzazione di un tracciato in Visual Studio](media/getting-started-08-plot1.png)

1. Per una singola riga è sufficiente premere CTRL + INVIO in qualsiasi momento per eseguire la riga nella finestra interattiva.

> [!Tip]
> È consigliabile imparare a eseguire le modifiche e premere CTRL + INVIO, oppure selezionare tutto con CTRL + A e quindi premere CRTRL + INVIO per eseguire il codice rapidamente. Questa procedura è molto più efficiente rispetto all'uso del mouse per le stesse operazioni.
> 
> È anche possibile trascinare e rilasciare la finestra del tracciato fuori dalla cornice di Visual Studio e posizionarlo in qualsiasi punto dello schermo. È quindi possibile ridimensionare la finestra dei tracciati alle dimensioni volute e quindi salvarla in un'immagine o in un file con estensione pdf.

1. Aggiungere altre righe di codice da includere in un secondo tracciato:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Premere nuovamente CTRL + A e CTRL + INVIO per eseguire il codice, con il risultato seguente:

    ![Doppio tracciato aggiornato in Visual Studio](media/getting-started-09-plot2.png)

1. Il problema è che la scala verticale viene determinata dal primo tracciato, quindi il secondo (con `lines`) non vi rientra. Per risolvere questo problema, è necessario impostare il parametro `ylim` della chiamata di `plot`, ma per eseguire questa operazione correttamente è necessario aggiungere codice per calcolare il valore verticale massimo. Eseguire questa operazione riga per riga nella finestra interattiva non è pratico, perché richiede di modificare il codice per usare `samp.means` prima di chiamare `plot`. In un file di codice tuttavia, è possibile apportare facilmente le modifiche appropriate:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Selezionare ancora CTRL + A e CTRL + INVIO per visualizzare il risultato:

    ![Doppio tracciato aggiornato in Visual Studio, ridimensionato correttamente](media/getting-started-10-plot3.png)

Nell'editor è possibile eseguire altre operazioni. Per informazioni dettagliate, vedere [Editing R code in Visual Studio](editing-r-code-in-visual-studio.md) (Modifica di codice R in Visual Studio), [IntelliSense](r-intellisense.md), e [Code snippets](code-snippets-for-r.md) (Frammenti di codice).

## <a name="debugging-your-code"></a>Debug del codice

Uno dei principali vantaggi di Visual Studio è l'interfaccia utente di debug. RTVS si basa su queste fondamenta solide e aggiunge un'interfaccia utente innovativa, come ad esempio [Esplora variabili e il visualizzatore di tabelle di dati](variable-explorer.md). In questo caso, vedremo solo brevemente il debug.

1. Per iniziare, reimpostare l'area di lavoro corrente per cancellare tutto quanto fatto finora tramite il comando di menu **R Tools > Sessione > Reimposta**. Per impostazione predefinita, tutte le operazioni eseguite nella finestra interattiva vengono aggiunte alla sessione corrente, che viene usata anche dal debugger. Reimpostando la sessione, si garantisce che la sessione di debug venga avviata senza dati preesistenti. Il comando **Reimposta**, tuttavia, non ha alcun effetto sul file di origine `script.R`, poiché questo viene gestito e salvato fuori dell'area di lavoro.

1. Con il file `script.R` creato nella sezione precedente, impostare un punto di interruzione sulla riga che inizia con `pop <-` posizionando il cursore sulla riga e premendo F9 o selezionando il comando di menu **Debug > Imposta/Rimuovi punto di interruzione**. In alternativa, fare semplicemente clic sul margine sinistro (rilegatura) della riga, laddove viene visualizzato il punto di interruzione rosso:

    ![Impostazione di un punto di interruzione nell'editor](media/getting-started-11-debug1.png)

1. Avviare il debugger con il codice in `script.R` selezionando il pulsante **Source startup file** (File di avvio di origine) sulla barra degli strumenti, selezionando le voci di menu **Debug > Source startup file** (File di avvio di origine), o premendo F5. Si avvia la modalità di debug di Visual Studio e inizia l'esecuzione del codice. L'esecuzione del codice si interrompe, tuttavia, nel punto in cui è stato impostato il punto di interruzione:

    ![Arresto in corrispondenza del punto di interruzione nel debugger di Visual Studio](media/getting-started-12-debug2.png)

1. Durante il debug, Visual Studio offre la possibilità di eseguire il codice riga per riga. È anche possibile eseguire funzioni, oltrepassarle o uscire da esse tornando nel contesto di chiamata. Queste funzionalità, insieme ad altre, sono disponibili nel menu **Debug**, nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse, e nella barra degli strumenti Debug:

    ![Barra degli strumenti Debug in Visual Studio](media/getting-started-13-debug3.png)

1. Quando l'esecuzione si arresta in corrispondenza del punto di interruzione, è possibile esaminare i valori delle variabili. Individuare la finestra **Auto** in Visual Studio e selezionare la scheda nella parte inferiore denominata **Variabili locali**. La finestra **Variabili locali** visualizza le variabili locali nel punto corrente all'interno del programma. Se il programma è stato interrotto in corrispondenza del punto di interruzione impostato in precedenza, si nota che la variabile `pop` non è ancora definita. A questo punto usare il comando **Debug > Esegui istruzione/routine** (F10). Verrà visualizzato il valore per `pop`:

    ![Finestra Variabili locali in Visual Studio](media/getting-started-14-debug4.png)

1. Per esaminare le variabili in ambiti diversi, tra cui l'ambito globale e gli ambiti pacchetto, usare [Esplora variabili](variable-explorer.md). Esplora variabili offre anche la possibilità di passare a una visualizzazione tabulare con colonne ordinabili e di esportare i dati in un file con estensione csv.

    ![Visualizzazione estesa di Esplora variabili](media/variable-explorer-expanded-results.png)

1. È possibile continuare l'esecuzione del programma riga per riga oppure selezionare **Continua** (F5) per completare l'esecuzione fino alla fine, o fino al punto di interruzione successivo.

Per informazioni più approfondite, vedere [Debugging in R Visual Studio](debugging-r-in-visual-studio.md) (Debug in R Visual Studio) e [Variable Explorer](variable-explorer.md) (Esplora variabili).

## <a name="next-steps"></a>Passaggi successivi

In questa procedura dettagliata sono state illustrate le nozioni di base dei progetti di R, usando la finestra interattiva, la modifica del codice e il debug in Visual Studio. Per passare all'esplorazione di altre funzionalità, vedere gli articoli seguenti, nonché quelli illustrati nel sommario:

- [Progetti di esempio per R Tools per Visual Studio](getting-started-samples.md)
- [Modifica di codice R in Visual Studio](editing-r-code-in-visual-studio.md)
- [Debug](debugging-r-in-visual-studio.md)
- [Workspaces](r-workspaces-in-visual-studio.md) (Aree di lavoro)
- [Visualizzazione di dati](visualizing-data-with-r-in-visual-studio.md)
