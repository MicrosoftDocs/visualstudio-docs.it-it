---
title: Utilizzo di Python, passaggio 6, utilizzo di Git | Microsoft Docs
description: Passaggio 6 di un'esercitazione di base per l'utilizzo di Python all'interno di Visual Studio, dedicato alle funzionalità correlate a Git di Visual Studio.
ms.custom: mvc
ms.date: 01/16/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ec8534e7fd3121510a05e201e8bdea2e9a7fce1c
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="step-6-working-with-git"></a>Passaggio 6: Uso di Git

**Passaggio precedente: [ Installazione dei pacchetti e gestione degli ambienti Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio offre l'integrazione diretta con repository Git locali e repository remoti di servizi come GitHub e Visual Studio Team Services. L'integrazione include la clonazione di un repository, le modifiche di esecuzione del commit e la gestione dei rami.

Questo articolo offre una panoramica di base sulla creazione di un repository Git locale per un progetto esistente e consente di acquisire familiarità con alcune delle funzionalità di Visual Studio correlate a Git.

1. Con un progetto aperto in Visual Studio, ad esempio il progetto del [passaggio precedente](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), fare clic col pulsante destro del mouse sulla soluzione e scegliere **Aggiungi soluzione al controllo del codice sorgente**. Visual Studio crea un repository Git locale che contiene il codice del progetto.

1. Quando Visual Studio rileva che il progetto viene gestito in un repository Git, lungo l'angolo inferiore destro della finestra di Visual Studio vengono visualizzati controlli relativi a Git. I controlli visualizzano le esecuzioni di commit in sospeso, le modifiche, il nome del repository e il ramo. Passare il mouse sui controlli per visualizzare le informazioni aggiuntive.

    ![Le informazioni aggiuntive vengono visualizzate quando si posiziona un controllo Git nella finestra di Visual Studio](media/working-with-git-01.png)

1. Quando si crea un nuovo repository o si seleziona uno dei controlli Git, Visual Studio apre la finestra **Team Explorer**. È possibile aprire la finestra in qualsiasi momento con il comando di menu **Visualizza > Team Explorer**. La finestra ha tre riquadri principali ed è possibile passare dall'uno all'altro tramite l'elenco a discesa nell'intestazione **Team Explorer**. Quando si seleziona il controllo Push (l'icona con la freccia verso l'alto), viene visualizzato anche il riquadro **Sincronizza**, che rende disponibili le operazioni di pubblicazione:

    ![Team Explorer in Visual Studio dopo la creazione di un repository locale](media/working-with-git-02.png)

1. Selezionare **Modifiche** (o il controllo Git con l'icona della matita) per esaminare le modifiche non sottoposte a commit ed eseguirne il commit nel momento desiderato.

    ![Team Explorer in Visual Studio per la visualizzazione di modifiche non sottoposte a commit](media/working-with-git-03.png)

    Fare doppio clic su un file nell'elenco **Modifiche** per aprire la visualizzazione delle differenze per il file:

    ![Visualizzazione delle differenze per le modifiche in un file](media/working-with-git-05.png)

1. Selezionare **Rami** (o il controllo Git con un nome di ramo) per esaminare i rami ed eseguire operazioni di unione e riassegnazione:

    ![Team Explorer in Visual Studio per la visualizzazione dei rami](media/working-with-git-04.png)

1. Selezionando il controllo Git con il nome del repository ("CosineWave" nell'immagine precedente), **Team Explorer** visualizza l'interfaccia **Connetti**, con cui è possibile passare rapidamente a un altro repository.

1. Quando si usa un repository locale, le modifiche sottoposte a commit passano direttamente al repository. In caso di connessione a un repository remoto, selezionare l'intestazione a discesa in **Team Explorer**, scegliere **Sincronizza** per passare alla sezione **Sincronizzazione** e utilizzare i comandi pull e fetch presentati in tale sezione.

## <a name="going-deeper"></a>Approfondimenti

Per una breve panoramica sulla creazione di un progetto da un repository Git remoto, vedere [Guida introduttiva: clonare un repository di codice Python in Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Per un'esercitazione molto più completa, comprendente la gestione dei conflitti di unione, la revisione di codice con richieste pull, la riassegnazione e il cherry-pick delle modifiche tra rami, vedere [Getting Started with Git and VSTS](/vsts/git/gitquickstart?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json&view=vsts&tabs=visual-studio) (Introduzione a Git e a VSTS).

## <a name="tutorial-review"></a>Revisione dell'esercitazione

È stata completata questa esercitazione di Python in Visual Studio. In questa esercitazione si è appreso come:

- Creare progetti e visualizzare il contenuto di un progetto.
- Usare l'editor di codice ed eseguire un progetto.
- Usare la finestra interattiva per sviluppare il nuovo codice e copiare facilmente il codice nell'editor.
- Eseguire un programma nel debugger di Visual Studio.
- Installare pacchetti e gestire gli ambienti Python
- Usare il codice in un repository Git

Da qui è possibile esaminare i concetti e le guide sulle procedure, inclusi gli articoli seguenti:

- [Creazione di un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md)
- [Pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilatura](profiling-python-code-in-visual-studio.md)
- [Testing unità](unit-testing-python-in-visual-studio.md)
