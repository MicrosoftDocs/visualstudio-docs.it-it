---
title: Creare un'installazione offline di Visual Studio | Microsoft Docs
description: Informazioni dettagliate sull'installazione offline di Visual Studio.
ms.custom: 
ms.date: 01/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9badba3247846ce63b79d48da7482ff0c58b693
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Creare un'installazione offline di Visual Studio 2017

Il programma di installazione di Visual Studio 2017 è stato progettato per funzionare correttamente in computer e reti diversi, in condizioni di qualsiasi tipo.

- Il nuovo modello basato sul carico di lavoro consente di scaricare un minor numero di componenti rispetto alle precedenti versioni di Visual Studio: l'installazione più piccola richiede solo 300 MB.
- Anziché un file "ISO" o un file zip generico ora vengono scaricati solo i pacchetti necessari per il computer. Ad esempio i file a 64 bit vengono scaricati solo se sono necessari.
- Durante il processo di installazione, vengono provate tre diverse tecnologie di download (WebClient, BITS e WinInet) per ridurre al minimo le interferenze con software proxy e anti-virus;
- I file necessari per l'installazione di Visual Studio vengono distribuiti in una rete di distribuzione globale e possono quindi essere recuperati da un server locale.

È consigliabile provare il nuovo [programma di installazione Web di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;, che garantisce risultati molto soddisfacenti.

 > [!div class="button"]
 > [Scarica Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Se si vuole eseguire l'installazione offline perché la connessione Internet non è disponibile o non è affidabile, vedere [Installare Visual Studio 2017 in ambienti di rete con larghezza di banda ridotta o non affidabili](../install/install-vs-inconsistent-quality-network.md). È possibile usare la riga di comando per creare una cache locale dei file necessari per completare l'installazione offline. Questo processo sostituisce i file ISO disponibili per le versioni precedenti.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio 2017 in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).
