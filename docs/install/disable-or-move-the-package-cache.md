---
title: Disabilitare o spostare la cache dei pacchetti | Microsoft Docs
description: Disabilitare, abilitare o spostare la cache dei pacchetti per distribuzioni di Visual Studio.
ms.date: 04/14/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7027413936cc7f907b4ec70304317c71c5ceb2da
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="disable-or-move-the-package-cache"></a>Disabilitare o spostare la cache dei pacchetti

La cache dei pacchetti fornisce un'origine di pacchetti installati nel caso in cui sia necessario ripristinare Visual Studio o altri prodotti correlati e non si disponga di una connessione a Internet. Con alcune unità o configurazioni di sistema, tuttavia, è possibile che non si voglia tenere nel sistema tutti questi pacchetti.
Il programma di installazione li scaricherà solo se necessario e, quindi, per risparmiare o recuperare spazio su disco, è possibile disabilitare o spostare la cache dei pacchetti.

## <a name="disable-the-package-cache"></a>Disabilitare la cache dei pacchetti

Prima di installare, modificare o ripristinare Visual Studio o altri prodotti con il nuovo programma di installazione, è possibile avviare il programma di installazione con l'opzione `--nocache`.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Qualsiasi operazione eseguita su un prodotto rimuoverà tutti i pacchetti esistenti per il prodotto ed eviterà di dover salvare i pacchetti dopo averli installati. Se si modifica o si ripristina Visual Studio e i pacchetti sono necessari, verranno automaticamente scaricati e rimossi dopo l'installazione.

Se si vuole abilitare nuovamente la cache, passare invece `--cache`. Verranno memorizzati nella cache solo i pacchetti necessari; pertanto, se devono essere ripristinati tutti i pacchetti, prima di disconnettere Visual Studio dalla rete, è necessario ripristinarlo.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

È possibile anche impostare i [criteri del Registro di sistema](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` per disabilitare la cache prima di installare, modificare o ripristinare Visual Studio.

## <a name="move-the-package-cache"></a>Spostare la cache dei pacchetti

Una configurazione di sistema comune prevede Windows installato in un'unità SSD con un disco rigido più grande (o più dischi rigidi) riservato per le esigenze di sviluppo, ad esempio per codice sorgente, file binari del programma e altro ancora. Se invece si preferisce lavorare offline, è possibile spostare la cache dei pacchetti.

Attualmente, è possibile eseguire questa operazione solo se si impostano i [criteri del Registro di sistema](set-defaults-for-enterprise-deployments.md) `CachePath` prima di installare, modificare o ripristinare Visual Studio.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

 * [Installare Visual Studio](install-visual-studio.md)
 * [Impostare i valori predefiniti per le distribuzioni aziendali](set-defaults-for-enterprise-deployments.md)
 * [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
