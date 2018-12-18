---
title: R Tools per Visual Studio | Microsoft Docs
description: "R Tools per Visual Studio (RTVS) è un'estensione gratuita, open source che offre diverse funzionalità di linguaggio, inclusi IntelliSense, debug e aree di lavoro remote."
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: hero-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 7e5fd1c6f2e2d33fe3841923f1b25728ad002f6e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="working-with-r-in-visual-studio"></a>Utilizzo di R in Visual Studio

R è un linguaggio estremamente estendibile, nonché un ambiente per l'elaborazione statistica e la grafica. Viene distribuito gratuitamente con la GNU General Public License, può contare su un forte supporto della community ed è noto per la possibilità di creare tracciati di alta qualità, inclusi formule e simboli matematici. Per altre informazioni su R, visitare il sito [r-project.org](https://www.r-project.org/about.html) e vedere [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introduzione a R).

R Tools per Visual Studio (RTVS) è un'estensione [open-source](https://github.com/microsoft/RTVS) gratuita per Visual Studio 2017 e Visual Studio 2015 Update 3 (o versione successiva) rilasciato con licenza MIT. Un secondo componente open-source denominato [RHost](https://github.com/microsoft/R-Host), che esegue il collegamento ai file binari dell'interprete R, viene rilasciato con la GNU Public License V2.

> [!Note]
> Gli strumenti RTVS sono attualmente supportati solo in Visual Studio in Windows e non in Visual Studio per Mac.

Per sperimentare R in Visual Studio:

- [Installare R Tools](installing-r-tools-for-visual-studio.md).
- Seguire le istruzioni riportate nell'[Introduzione](getting-started-with-r.md), nonché quelle fornite negli articoli [Esempi](getting-started-samples.md) e [Informazioni di supporto](getting-started-help.md).

Usare i collegamenti seguenti per saperne di più sulle funzionalità correlate a R, nonché sulle funzionalità generali di Visual Studio.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio | 
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](r-projects-in-visual-studio.md) | È possibile organizzare e gestire i file correlati in una pratica struttura e sfruttare gli utili modelli per elementi quali il codice R, la documentazione R e R Markdown, nonché per le query SQL e le stored procedure. È inoltre possibile sfruttare la funzionalità di [gestione pacchetti](r-package-manager-in-visual-studio.md) e l'[integrazione con SQL Server](integrating-sql-server-with-r.md).  | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Area di lavoro](r-workspaces-in-visual-studio.md) | RTVS supporta l'associazione ad aree di lavoro locali e remote, consentendo all'utente di sviluppare localmente codice R con set di dati di dimensioni ridotte e quindi di eseguire facilmente tale codice su computer più potenti basati su cloud con set di dati molto più grandi. | N/D |
| [Opzioni di R Tools](options-for-r-tools-in-visual-studio.md) | Consentono di controllare i diversi aspetti di RTVS. | [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md) |
| [Modifica avanzata, IntelliSense e frammenti di codice](editing-r-code-in-visual-studio.md) | Sono inclusi colorazione della sintassi, [IntelliSense](r-intellisense.md) in tutto il codice e in tutte le librerie, formattazione del codice, supporto per la firma, accesso alle definizioni, opzione per trovare tutti i riferimenti, [frammenti di codice](code-snippets-for-r.md) e altro ancora. | [Writing Code in the Code and Text Editor](../ide/writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'Editor di testo e del codice) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | I documenti R Markdown consentono di condividere i risultati dei dati, con codice R integrato all'interno di blocchi di codice markdown. | N/D |
| [Finestra interattiva](interactive-repl-for-r-in-visual-studio.md) | Fornisce un'esperienza completa di REPL per R con la possibilità di eseguire facilmente il codice in un file di origine nella finestra interattiva. | N/D |
| [Visualizzazione dei dati](visualizing-data-with-r-in-visual-studio.md) | La creazione di tracciati è parte integrante dell'esperienza R e RTVS supporta diverse finestre dei tracciati indipendenti, ciascuna delle quali con la propria cronologia e la possibilità di spostare tracciati da una finestra all'altra. I tracciati possono essere salvati in bitmap e file PDF oppure copiati negli Appunti come bitmap o metafile.  | N/D |
| [Variable Explorer](variable-explorer.md) | Consente di esaminare le variabili in ambiti globali o specifici del pacchetto, con la possibilità di visualizzare tabelle ordinabili ed eseguire l'esportazione in CSV. | N/D |
| [Debug con funzionalità complete](debugging-r-in-visual-studio.md) | Include l'integrazione con la finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |

Vedere anche [Domande frequenti](faq.md).

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) per una panoramica di R Tools per Visual Studio (12 m 36s). Vedere anche [altri video su R Tools](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Inviateci i vostri commenti!

1. **Problemi GitHub**: il modo migliore per contattare il team RTVS consiste nel [segnalare un problema in GitHub](https://github.com/Microsoft/RTVS/issues) oppure usare il menu **R Tools > Feedback**.

1. **Invia smile/Invia faccia imbronciata**: il menu **R Tools > Feedback** è un modo rapido per inviare commenti e suggerimenti e allegare file di log RTVS per facilitare la diagnosi del problema. I log vengono scritti in `%temp%/RTVSlogs.zip`, nel caso li si voglia inviare separatamente. La registrazione è disabilitata se si è scelto di disattivare la telemetria di Visual Studio durante l'installazione oppure usando il comando di menu **Guida > Feedback > Impostazioni**.

1. **Messaggio di posta elettronica**: è possibile inviare commenti e suggerimenti direttamente al team all'indirizzo *rtvsuserfeedback (at) microsoft.com*.
