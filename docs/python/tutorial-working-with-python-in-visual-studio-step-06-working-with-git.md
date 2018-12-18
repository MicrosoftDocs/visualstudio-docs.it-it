---
title: Utilizzo di Python in Visual Studio, Passaggio 6, Uso di Git | Microsoft Docs
description: "Passaggio 6 di un'esercitazione di base per l'utilizzo di Python all'interno di Visual Studio, dedicato alle funzionalità correlate a Git di Visual Studio."
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
ms.openlocfilehash: eb39d8807deb0c08b12b04128365c584d9bd8251
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="step-6-working-with-git"></a>Passaggio 6: Uso di Git

**Passaggio precedente: [ Installazione dei pacchetti e gestione degli ambienti Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio offre l'integrazione diretta con repository Git locali e che si trovano su servizi come GitHub e Visual Studio Team Services. L'integrazione include la clonazione di un repository, le modifiche di esecuzione del commit e la gestione dei rami.

Questo argomento descrive la creazione di un repository Git locale per un progetto esistente. Per una panoramica sulla creazione di un progetto da un repository Git remoto, vedere [Guida introduttiva: clonare un repository di un codice Python in Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

1. Con un progetto aperto in Visual Studio, ad esempio il progetto del [passaggio precedente](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), fare clic col pulsante destro del mouse sulla soluzione e scegliere **Aggiungi soluzione al controllo del codice sorgente**. Visual Studio crea un repository Git locale che contiene il codice del progetto e visualizza i controlli correlati Git che vengono visualizzati anche nella parte inferiore della finestra di Visual Studio. I controlli visualizzano le esecuzioni di commit in sospeso, le modifiche, il nome del repository e il ramo. Passare il mouse sui controlli per visualizzare le informazioni aggiuntive.

  ![Le informazioni aggiuntive vengono visualizzate quando si posiziona un controllo Git nella finestra di Visual Studio](media/working-with-git-01.png)

1. La finestra **Team Explorer** viene visualizzata anche con varie opzioni di Git selezionando l'intestazione del repository. Il riquadro **Sincronizzazione**, visualizzato quando si seleziona l'intestazione **Push**, specifica le opzioni per la pubblicazione in un repository remoto.

  ![Team Explorer in Visual Studio dopo la creazione di un repository locale](media/working-with-git-02.png)

1. Selezionare **Modifiche** per esaminare le modifiche non sottoposte a commit per eseguirne il commit nel momento desiderato.

  ![Team Explorer in Visual Studio per la visualizzazione di modifiche non sottoposte a commit](media/working-with-git-03.png)

1. Selezionare **Rami** per esaminare i rami ed eseguire le operazioni di unione e riassegnazione:

  ![Team Explorer in Visual Studio per la visualizzazione dei rami](media/working-with-git-04.png)

1. Quando si usa un repository locale, le modifiche sottoposte a commit passano direttamente al repository. Se si è connessi a un repository remoto, selezionare l'intestazione, scegliere **Sincronizza** per passare alla sezione **Sincronizzazione** e utilizzare i comandi presentati in tale sezione.

## <a name="going-deeper"></a>Approfondimenti

Per le esercitazioni sugli approfondimenti sull'uso di Git, vedere [Condividere il codice con Visual Studio 2017 e VSTS Git](/vsts/git/share-your-code-in-git-vs-2017)

## <a name="tutorial-review"></a>Revisione dell'esercitazione

È stata completata questa esercitazione di Python in Visual Studio. In questa esercitazione si è appreso come:

- Creare progetti e visualizzare il contenuto di un progetto.
- Usare l'editor di codice ed eseguire un progetto.
- Usare la finestra interattiva per sviluppare il nuovo codice e copiare facilmente il codice nell'editor.
- Eseguire un programma nel debugger di Visual Studio.
- Installare pacchetti e gestire gli ambienti Python
- Usare il codice in un repository Git

Da qui è possibile esaminare i concetti e le guide sulle procedure, incluse le seguenti:

- [Creazione di un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md)
- [Pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilatura](profiling-python-code-in-visual-studio.md)
- [Testing unità](unit-testing-python-in-visual-studio.md)
