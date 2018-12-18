---
title: Come gestire gli ambienti e gli interpreti Python | Microsoft Docs
description: Come usare la finestra Ambienti Python in Visual Studio per gestire gli ambienti globali e virtuali, configurare gli ambienti personalizzati, installare gli interpreti Python, installare pacchetti, impostare percorsi di ricerca e gestire gli ambienti per i progetti di Visual Studio.
ms.custom: ''
ms.date: 03/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a1bf9c9c016a71c816ed8cc40b675c520e9c9397
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="managing-python-environments-in-visual-studio"></a>Gestione di ambienti Python in Visual Studio

Un *ambiente* Python è un contesto in cui eseguire il codice Python e include gli ambienti globale, virtuale e Conda. Un ambiente è costituito da un interprete, una libreria (in genere quella standard Python) e un set di pacchetti installati. Questi componenti nel loro insieme determinano la sintassi e i costrutti di linguaggio validi, le funzionalità accessibili del sistema operativo e i pacchetti che è possibile usare.

In Visual Studio in Windows, la finestra [Ambienti Python](#managing-python-environments-in-visual-studio), descritta in questo articolo, è la posizione in cui si gestiscono questi ambienti e se ne seleziona uno come predefinito per i nuovi progetti. Per ogni progetto, è anche possibile selezionare un ambiente specifico anziché usare quello predefinito.

**Nota**: se non si ha familiarità con Python in Visual Studio, vedere gli articoli seguenti per raccogliere le informazioni di base necessarie:

- [Uso di Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installazione del supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md)

Si noti anche che non è possibile gestire gli ambienti per il codice Python aperto solo come cartella tramite il comando **File > Apri > Cartella**. In alternativa, [creare un progetto Python da codice esistente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) per sfruttare le funzionalità dell'ambiente di Visual Studio.

Per installare i pacchetti in un ambiente, fare riferimento alla [scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Tipi di ambienti

### <a name="global-environments"></a>Ambienti globali

Ogni installazione di Python (ad esempio Python 2.7, Python 3.6, Anaconda 4.4.0 e così via, vedere [Selezione e installazione di interpreti Python](installing-python-interpreters.md)) mantiene il proprio ambiente globale. Ogni ambiente è costituito dall'interprete Python specifico e dalla relativa libreria standard, oltre a un set di pacchetti preinstallati. L'installazione di un pacchetto in un ambiente globale lo rende disponibile per tutti i progetti che usano tale ambiente. Se l'ambiente si trova in un'area protetta del file system, ad esempio in `c:\program files`, per l'installazione dei pacchetti sono richiesti privilegi di amministratore.

Gli ambienti globali sono disponibili per tutti i progetti nel computer. In Visual Studio si seleziona un ambiente globale come predefinito e tale ambiente viene usato per tutti i progetti a meno che non se ne scelga in modo specifico un altro per un progetto. Per altre informazioni, vedere [Selezione di un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Ambienti virtuali

Dal momento che i pacchetti installati in un ambiente globale sono disponibili per tutti i progetti che usano tale ambiente, possono verificarsi conflitti quando due progetti richiedono pacchetti non compatibili o versioni diverse dello stesso pacchetto. Gli ambienti virtuali consentono di evitare questi conflitti usando l'interprete e la libreria standard da un ambiente globale, ma mantenendo gli archivi dei pacchetti in cartelle isolate.

In Visual Studio è possibile creare un ambiente virtuale per un progetto specifico, che viene archiviato in una sottocartella del progetto. Visual Studio offre un comando che consente di generare un file `requirements.txt` dall'ambiente virtuale, rendendo più semplice ricreare l'ambiente in altri computer. Per altre informazioni, vedere [Uso di ambienti virtuali](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Ambienti Conda

Un ambiente Conda è un ambiente creato con lo strumento `conda`. Gli ambienti Conda vengono in genere archiviati nella cartella `envs` all'interno di un'installazione di Anaconda e pertanto hanno un funzionamento simile a quello degli ambienti globali. Ad esempio, l'installazione di un nuovo pacchetto in un ambiente Conda lo rende disponibile per tutti i progetti che usano tale ambiente.

Visual Studio, al momento, non rileva automaticamente gli ambienti Conda, ma è possibile specificarli manualmente. Vedere [Manually identifying an existing environment](#manually-identifying-an-existing-environment) (Identificazione manuale di un ambiente esistente).

## <a name="the-python-environments-window"></a>Finestra Ambienti Python

Gli ambienti rilevati da Visual Studio vengono visualizzati nella finestra **Ambienti Python**. Per aprire la finestra, usare uno dei metodi seguenti:

- Selezionare il comando di menu **Visualizza > Altre finestre > Ambienti Python**.
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in Esplora soluzioni e scegliere **Visualizza tutti gli ambienti Python**:

    ![Comando Visualizza tutti gli ambienti Python in Esplora soluzioni](media/environments-view-all.png)

In entrambi i casi, la finestra **Ambienti Python** viene visualizzata come una scheda di pari livello in Esplora soluzioni:

![Finestra Ambienti Python](media/environments-default-view.png)

L'immagine precedente mostra che Visual Studio ha rilevato due installazioni di Python 3.6 (a 32 bit) insieme ad Anaconda 5.0.0.

L'ambiente predefinito in grassetto è Python 3.6 (in questo caso parte di un'installazione di Anaconda), usato da Visual Studio per tutti i nuovi progetti. I comandi nella parte inferiore della finestra si applicano all'interprete selezionato di Python 3.6, che come si può vedere corrisponde all'installazione specifica in `C:\Python36-32`. Se non è visualizzato un ambiente previsto, vedere [Identificazione manuale di un ambiente esistente](#manually-identifying-an-existing-environment).

A destra di ogni ambiente elencato è disponibile un controllo che consente di aprire una finestra interattiva per tale ambiente. È possibile che venga visualizzato un altro controllo che aggiorna il database di IntelliSense per quell'ambiente (vedere [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md#intellisense-tab) per informazioni dettagliate sul database).

Sotto l'elenco degli ambienti è disponibile un selettore a discesa per le opzioni **Panoramica**, **Pacchetti** e **IntelliSense** descritte in [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md). Se si allarga a sufficienza la finestra **Ambienti Python**, inoltre, queste opzioni vengono visualizzate come schede, un layout che può risultare più comodo:

![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

> [!Note]
> Anche se Visual Studio rispetta l'opzione dei pacchetti dei siti di sistema, non consente di modificarla da Visual Studio.

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sugli ambienti Python in Visual Studio (2m 35s).|

### <a name="what-if-no-environments-appear"></a>Se non viene visualizzato alcun ambiente

Se non viene visualizzato alcun ambiente, significa che Visual Studio non è riuscito a rilevare installazioni di Python nelle posizioni standard. È possibile, ad esempio, avere installato Visual Studio 2017 con tutte le opzioni per l'interprete deselezionate nelle opzioni del programma di installazione per il carico di lavoro di Python. Analogamente, è possibile che sia installato Visual Studio 2015 o versione precedente, ma che non sia stato installato manualmente un interprete. Vedere [Installazione degli interpreti Python](installing-python-interpreters.md).

Se si è certi di disporre di un interprete Python nel computer in uso, ma Visual Studio (qualsiasi versione) non lo rileva, usare il comando **+ Personalizzato** per specificarne il percorso manualmente. Vedere la sezione successiva, [Identificazione manuale di un ambiente esistente](#manually-identifying-an-existing-environment).

> [!Tip]
> Visual Studio rileva gli aggiornamenti per un interprete esistente, ad esempio l'aggiornamento di Python 2.7.11 a 2.7.14 tramite i programmi di installazione da python.org. Durante il processo di installazione, l'ambiente precedente scompare dall'elenco **Ambienti Python** prima che venga visualizzato l'aggiornamento nella posizione prevista.
>
> Tuttavia, se si sposta manualmente un interprete e il relativo ambiente tramite il file system, Visual Studio non conosce il nuovo percorso. Per altre informazioni, vedere [Spostamento di un interprete](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Identificazione manuale di un ambiente esistente

Usare questa procedura per identificare un ambiente installato in un percorso non standard, inclusi gli ambienti Conda:

1. Selezionare **+ Personalizzato** nella finestra **Ambienti Python**. Verrà aperta la scheda **Configura**:

    ![Visualizzazione predefinita per un nuovo ambiente personalizzato](media/environments-custom-1.png)

1. Immettere un nome per l'ambiente nel campo **Descrizione**.

1. Immettere o selezionare (tramite **...***) il percorso dell'interprete nel campo **Percorso di prefisso**.

1. Se Visual Studio rileva un interprete Python nel percorso specificato, ad esempio il percorso illustrato di seguito per un ambiente Conda, viene abilitato il comando **Rilevamento automatico**. Selezionando **Rilevamento automatico* vengono compilati i restanti campi. È anche possibile compilare manualmente questi campi.

    ![Abilitazione del comando Rilevamento automatico](media/environments-custom-2.png)

    ![Completamento dei campi di ambiente dopo l'uso di Rilevamento automatico](media/environments-custom-3.png)

1. Quando i campi contengono i valori desiderati, selezionare **Applica** per salvare la configurazione. È ora possibile usare l'ambiente come qualsiasi altro all'interno di Visual Studio.

1. Se è necessario rimuovere un ambiente identificato manualmente, selezionare il comando **Rimuovi** nella scheda **Configura**. Gli ambienti rilevati automaticamente non offrono questa opzione. Per altre informazioni, vedere [Scheda Configura](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Vedere anche

- [Installazione degli interpreti Python](installing-python-interpreters.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Uso di requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)