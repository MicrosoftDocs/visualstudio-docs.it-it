---
title: Progetti di esempio per R Tools per Visual Studio | Microsoft Docs
description: Indice di una raccolta di esempi per iniziare con R e Visual Studio.
ms.custom: ''
ms.date: 01/24/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 6d09999f8dd0e53dc8ae3ae61537eb182eaeb6d4
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Progetti di esempio di R Tools per Visual Studio

Questa raccolta di esempi funge da introduzione a R, R Tools per Visual Studio (RTVS) e Microsoft R Server:

1. Scaricare il [file degli esempi con estensione zip](https://github.com/Microsoft/RTVS-docs/archive/master.zip) ed estrarne il contenuto in una cartella di propria scelta.
1. Aprire `examples/Examples.sln`. Si noteranno due cartelle nel progetto:

    - *A First Look at R* (Panoramica di R) offre un'introduzione semplice per chi non ha dimestichezza con R.
    - *MRS and Machine Learning* (Microsoft R Server e apprendimento automatico) offre esempi di come usare R e Microsoft R Server per l'apprendimento automatico.

## <a name="a-first-look-at-r"></a>A First Look at R

Questo esempio offre un'introduzione approfondita a R tramite la serie di commenti esaustivi in due file di origine. Per usufruire al meglio di questo esempio, posizionare il cursore nella parte superiore del file e premere Ctrl + Invio per inviare il codice riga per riga alla finestra **R interattivo**. Il completamento delle righe di installazione dei pacchetti potrebbe richiedere uno o due minuti.

- `1-Getting Started with R.R` illustra molte nozioni fondamentali di R compresi l'uso di pacchetti, il caricamento e l'analisi dei dati e il tracciamento.

    ![Output dell'esempio 1-Getting Started with R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` introduce il pacchetto di grafica ggplot2 noto per i tracciati visivamente gradevoli e la sintassi semplice. In questo esempio vengono visualizzati dati sui terremoti alle Figi.

    ![Output dell'esempio 2-Introduction to ggplot2.R](media/samples-ggplot-output.png)

## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server e apprendimento automatico

Questa raccolta di esempi illustra come usare R per creare modelli di apprendimento automatico e come sfruttare le funzionalità di [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r). Installare MRS per eseguire gli script il cui titolo contiene `MRS` e dove indicato.

Come per tutti gli esempi, aprire il file, posizionare il cursore nella parte superiore e quindi eseguire il codice riga per riga con Ctrl + Invio. Anche i file markdown in ogni cartella contengono dettagli aggiuntivi.

- `Benchmarks` esegue diversi calcoli paralleli a elevato utilizzo di algebra lineare per visualizzare il miglioramento delle prestazioni che è possibile realizzare tramite l'uso di Microsoft R Open e delle librerie Intel Math Kernel Library (MKL). Con dati simulati, i benchmark confrontano in modo specifico i calcoli di matrice per un thread rispetto ad altri due.

    ![Tracciato di esempio Benchmark](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crea un modello di previsione della domanda per noleggi di biciclette basato su un set di dati cronologico, usando Microsoft R Server. 

- `Data_Exploration` contiene tre script:

  - `Import Data from URL.R` illustra come caricare in R un file di dati identificato da URL.
  - `Import Data from URL to xdf.R` illustra come caricare in Microsoft R Server un file di dati identificato da URL come xdf. (Richiede MRS).
  - `Using ggplot2.R` è un'estensione dell'esempio `A First Look at R/2-Introduction to ggplot2.R`, con una panoramica più estesa della funzionalità di ggplot2, tra cui il tracciamento 3D interattivo.

      ![Output dell'uso dell'esempio ggplot2.R](media/samples-3d-interactive.png)

- `Datasets` include tre file `.csv` usati da altri esempi
- `Flight_Delays_Prediction_with_R` e `Flight_Delays_Prediction_with_MRS` illustrano come prevedere i ritardi dei voli con R, l'apprendimento automatico e lo storico delle prestazioni nei tempi stabiliti, nonché i dati meteorologici. 
- `Machine learning` contiene tre esempi per apprendere a prevedere i ritardi dei voli e i prezzi delle abitazioni e del noleggio di biciclette. Insieme questi esempi illustrano l'applicazione di R e MRS a problemi concreti. Illustra anche come usare diversi modelli comuni di apprendimento automatico e distribuirli come un servizio Web di Azure tramite un'area di lavoro di [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` è un confronto in sei parti che illustra similitudini e differenze di R, Microsoft R Open e Microsoft R Server con comandi, sintassi, costrutti e prestazioni.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>I punti salienti di Microsoft R Open e Microsoft R Server.

[Microsoft R Open](http://aka.ms/rtvs-r-open), la distribuzione Microsoft di R, è diverso da [CRAN R](https://cran.r-project.org/) in due aspetti principali:

1. [Migliori prestazioni di calcolo](https://mran.revolutionanalytics.com/rro/#intelmkl1) quando usato con le librerie [Intel MKL](https://software.intel.com/intel-mkl), disponibili per il download gratuito da Microsoft per l'uso con Microsoft R Open.

1. [Toolkit di R riproducibile](https://mran.revolutionanalytics.com/rro/#reproducibility) assicura che le librerie usate per compilare il programma R siano sempre disponibili per altri utenti che vogliano riprodurre il lavoro.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) è un'estensione di R che consente di gestire più dati e più velocemente. Offre due funzionalità potenti per R:

1. Set di dati più grande senza limitazioni di RAM. MRS può elaborare dati in caso di memoria insufficiente da un'ampia gamma di origini tra cui cluster di Hadoop, database e data warehouse.

1. Elaborazione parallela, multi-core. MRS può distribuire in modo efficiente i calcoli in tutte le risorse di calcolo disponibili. Nella workstation personale o in un cluster remoto MRS ottiene una risposta velocemente.

Il confronto seguente illustra come MRS e MRO con MKL abbiano prestazioni di calcolo decisamente migliori relativamente ad alcuni calcoli di matrice rispetto a R e MRO senza MKL. Per questo calcolo vengono usati dati simulati:

![Confronto tra MRS e MRO con MKL e R e MRO senza MKL](media/samples-speed-comparison.png)

Per un confronto tecnico di R con MRO e MRS, vedere [la discussione dettagliata di Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sull'argomento.

Nella figura seguente viene quindi confrontato il tempo trascorso in secondi usato per la creazione di modelli di regressione logistica per stimare ritardi dei voli di più di 15 minuti.  Il tempo trascorso usato in CRAN R aumenta notevolmente all'aumento di un numero ridotto di righe, mentre MRS aumenta solo di circa due volte. Per informazioni dettagliate su questo benchmark, vedere l'esempio `Benchmarks/rxGlm_benchmark.R`.

![Benchmark rxGlm](media/samples-rxGLM-benchmark.png)
