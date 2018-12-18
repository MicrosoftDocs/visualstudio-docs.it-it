---
title: Ottimizzare le prestazioni di Visual Studio | Microsoft Docs
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 403bbfff74cfe969a26e12aeb1f4b54ef0473195
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="optimize-visual-studio-performance"></a>Ottimizzare le prestazioni di Visual Studio

Visual Studio è progettato per essere avviato nel modo più rapido ed efficiente possibile. Tuttavia, alcune estensioni di Visual Studio e le finestre degli strumenti possono influenzare negativamente i tempi di avvio quando vengono caricate. È possibile controllare il comportamento delle estensioni e delle finestre degli strumenti lente nella finestra di dialogo **Gestisci prestazioni di Visual Studio**. Per suggerimenti generali su come migliorare le prestazioni, vedere [Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Comportamento di avvio

Per evitare l'allungamento del tempo di avvio, Visual Studio 2017 carica le estensioni usando un approccio _su richiesta_. Con questo comportamento le estensioni non vengono aperte immediatamente dopo l'avvio di Visual Studio, ma all'occorrenza. Inoltre, poiché le finestre degli strumenti lasciate aperte in una sessione precedente di Visual Studio possono rallentare l'avvio, esse vengono aperte in un modo più intelligente per evitare di compromettere il tempo di avvio.

Se Visual Studio rileva un avvio lento, viene visualizzato un messaggio popup che comunica quale estensione o finestra degli strumenti provoca il rallentamento. Il messaggio include un collegamento alla finestra di dialogo **Gestisci prestazioni di Visual Studio**. È possibile accedere a questa finestra di dialogo anche scegliendo **Guida**, **Gestisci prestazioni di Visual Studio** dalla barra dei menu.

![Popup di Gestisci prestazioni di Visual Studio con il messaggio 'È stato notato che l'estensione ... rallenta Visual Studio'](../ide/media/vside_perfdialog_popup.png)

La finestra di dialogo elenca le estensioni e le finestre degli strumenti che compromettono le prestazioni di avvio. È possibile modificare le impostazioni delle estensioni e delle finestre degli strumenti per migliorare le prestazioni di avvio.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a>Per modificare le impostazioni delle estensioni per migliorare l'avvio, il caricamento della soluzione e le prestazioni di digitazione

1. Aprire la finestra di dialogo **Gestisci prestazioni di Visual Studio** scegliendo **Guida**, **Gestisci prestazioni di Visual Studio** dalla barra dei menu.

    Se un'estensione sta rallentando l'avvio di Visual Studio, il caricamento della soluzione o la digitazione, l'estensione viene visualizzata nella finestra di dialogo **Gestisci prestazioni di Visual Studio** quando si sceglie **Estensioni**, **Avvio** (oppure **Carico della soluzione** o **Digitazione**).

    ![Gestisci prestazioni di Visual Studio - visualizzazione delle estensioni](../ide/media/vside_perfdialog_extensions.png)

2. Scegliere l'estensione che si vuole disabilitare, quindi scegliere il pulsante **Disabilita**.

È sempre possibile riabilitare l'estensione per le sessioni future mediante il Gestore estensioni o la finestra di dialogo Gestisci prestazioni di Visual Studio.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a>Per modificare le impostazioni delle finestre degli strumenti per migliorare i tempi di avvio

1. Aprire la finestra di dialogo **Gestisci prestazioni di Visual Studio** scegliendo **Guida**, **Gestisci prestazioni di Visual Studio** dalla barra dei menu.

    Se una finestra degli strumenti rallenta l'avvio di Visual Studio, la finestra viene visualizzata nella finestra di dialogo **Gestisci prestazioni di Visual Studio** quando si sceglie **Finestre degli strumenti**, **Avvio**.

2. Scegliere la finestra degli strumenti della quale si vuole modificare il comportamento.

3. Scegliere una delle tre opzioni seguenti:

    - **Usa comportamento predefinito:** comportamento predefinito della finestra degli strumenti. Mantenere selezionata questa opzione non migliorerà le prestazioni di avvio.

    - **Non visualizzare la finestra all'avvio:** la finestra degli strumenti specificata viene sempre chiusa all'apertura di Visual Studio, anche se è stata lasciata aperta in una sessione precedente. È possibile aprire la finestra degli strumenti dal menu appropriato quando necessario.

    - **Nascondi automaticamente la finestra all'avvio:** se una finestra degli strumenti è stata lasciata aperta in una sessione precedente, questa opzione consente di comprimere il gruppo della finestra degli strumenti all'avvio per evitarne l'inizializzazione. Questa opzione è una scelta ottimale se si usa spesso una finestra degli strumenti. La finestra degli strumenti rimane disponibile senza compromettere il tempo di avvio di Visual Studio.

    ![Gestisci prestazioni di Visual Studio - visualizzazione delle finestre degli strumenti](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> In alcune versioni precedenti di Visual Studio 2017 è presente una funzionalità denominata **caricamento leggero soluzioni**. Questa funzionalità non è più disponibile in Visual Studio 2017 versione 15.5 e versioni successive. In Visual Studio 2017 versione 15.5 e versioni successive le soluzioni di grandi dimensioni contenenti codice gestito vengono caricate molto più velocemente che in passato, anche senza il caricamento leggero soluzioni.

## <a name="see-also"></a>Vedere anche

- [Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
