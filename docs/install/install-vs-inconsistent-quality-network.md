---
title: Eseguire l'installazione in ambienti di rete con larghezza di banda ridotta o non affidabili | Microsoft Docs
description: Descrive il funzionamento del programma di installazione di Visual Studio in condizioni di rete non affidabili e illustra come scaricare i file di installazione prima di iniziare la procedura di installazione.
ms.date: 01/17/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a9a0263c79e1dd2c7d0aacc5f405185cad3c3e7
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installare Visual Studio 2017 in ambienti di rete con larghezza di banda ridotta o non affidabili

È consigliabile provare il nuovo &mdash;programma di installazione Web di Visual Studio, che garantisce risultati molto soddisfacenti nella maggior parte delle situazioni.

 > [!div class="button"]
 > [Scarica Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Tuttavia, se la connessione Internet non è disponibile o affidabile, è possibile usare la riga di comando per creare una cache locale dei file necessari per completare un'installazione offline. Ecco come fare.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio 2017 in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Passaggio 1: Scaricare il programma di avvio automatico di Visual Studio

Iniziare scaricando il programma di bootstrap relativo all'edizione di Visual Studio selezionata.

Il file di installazione o, per essere più specifici, il file di un programma di bootstrap, corrisponderà o sarà simile a uno dei file seguenti.

| Edizione                    | File                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Community di Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Passaggio 2: Creare una cache di installazione locale

Per completare questo passaggio è necessario avere una connessione Internet. Per creare un layout locale, aprire un prompt dei comandi e usare uno dei comandi degli esempi seguenti. Negli esempi seguenti si presuppone l'uso dell'edizione Community di Visual Studio: modificare il comando a seconda della propria edizione.

- Per lo sviluppo per Web .NET e desktop .NET, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Per lo sviluppo per desktop .NET e Office, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Per lo sviluppo per desktop C++, eseguire:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Per creare un layout locale completo con tutte le funzionalità (dato l'elevato numero di funzionalità, questa operazione richiederà molto tempo), eseguire:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Se si vuole installare una lingua diversa dall'inglese, nell'elenco in fondo alla pagina modificare `en-US` con impostazioni locali diverse. Usare l'[elenco di componenti e carichi di lavoro disponibili](workload-and-component-ids.md) per personalizzare ulteriormente la cache di installazione in base alle proprie esigenze.

> [!IMPORTANT]
> Un layout di Visual Studio 2017 completo richiede almeno 35 GB di spazio su disco e, pertanto, può essere necessario molto tempo per scaricarlo. Vedere [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) per informazioni su come creare un layout con i soli componenti da installare.

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Passaggio 3: Installare Visual Studio dalla cache locale

> [!TIP]
> Quando si esegue l'installazione da una cache locale, vengono usate le versioni locali di ogni file. Se, tuttavia, durante l'installazione si selezionano componenti non contenuti nella cache, si tenterà di scaricarli da Internet.

Per assicurarsi che vengano installati solo i file scaricati, usare le stesse opzioni della riga di comando usate per creare la cache di layout. Ad esempio, se è stata creata una cache di layout con il comando seguente:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Usare questo comando per eseguire l'installazione:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Se viene generato un errore che indica che una firma non è valida, è necessario installare i certificati aggiornati. Aprire la cartella dei certificati presente nella cache offline. Fare doppio clic su ognuno dei file di certificato e quindi seguire la procedura guidata di gestione dei certificati. Se viene richiesto di immettere una password, lasciare il campo vuoto.

## <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue

| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |
| cs-CZ | Ceco |
| de-DE | Tedesco |
| it-IT | Inglese |
| es-ES | Spagnolo |
| fr-FR | Francese |
| it-IT | Italiano |
| ja-JP | Giapponese |
| ko-KR | Coreano |
| pl-PL | Polacco |
| pt-BR | Portoghese (Brasile) |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Cinese semplificato |
| zh-TW | Cinese tradizionale |

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
