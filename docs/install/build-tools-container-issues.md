---
title: Problemi noti dei contenitori | Microsoft Docs
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6edcc59a2d726fbd76fee86b750f21dc468b727e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="known-issues-for-containers"></a>Problemi noti dei contenitori

Esistono alcuni problemi durante l'installazione di Visual Studio in un contenitore Docker.

## <a name="windows-container"></a>Contenitore di Windows

I problemi noti seguenti si verificano quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.

* Non è possibile installare Visual Studio in un contenitore basato sull'immagine microsoft/windowsservercore:10.0.14393.1593. Le immagini contrassegnate con versioni di Windows più recenti o precedenti dovrebbero funzionare.
* Non è possibile installare versioni di Windows SDK precedenti alla 10.0.14393. Alcuni pacchetti non vengono installati e i carichi di lavoro che dipendono da tali pacchetti non funzioneranno.
* È necessario passare `-m 2GB` (o più) durante la compilazione dell'immagine. Alcuni carichi di lavoro richiedono più memoria rispetto al valore predefinito di 1 GB durante l'installazione.
* È necessario configurare Docker per l'uso si dischi più grandi rispetto all'impostazione predefinita di 20 GB.
* È necessario passare `--norestart` nella riga di comando. Alla data di redazione di questo articolo, qualsiasi tentativo di riavviare un contenitore di Windows dall'interno del contenitore restituisce `ERROR_TOO_MANY_OPEN_FILES` all'host.

## <a name="build-tools-container"></a>Contenitore di Build Tools

Potrebbero verificarsi i seguenti problemi noti quando si usa un contenitore di Build Tools. Per scoprire se questi problemi sono stati corretti o se sono presenti altri problemi noti, visitare https://developercommunity.visualstudio.com.

* IntelliTrace potrebbe non funzionare in [alcuni scenari](https://github.com/Microsoft/vstest/issues/940) all'interno di un contenitore.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
