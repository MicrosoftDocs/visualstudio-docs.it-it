---
title: Disabilitare o spostare la cache dei pacchetti
description: Informazioni sula procedura di disabilitazione, abilitazione o spostamento della cache dei pacchetti per distribuzioni di Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f38757931cb22e9072571d96b015f37882dd500
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114795"
---
# <a name="disable-or-move-the-package-cache"></a>Disabilitare o spostare la cache dei pacchetti

La cache dei pacchetti fornisce un'origine di pacchetti installati nel caso in cui sia necessario ripristinare Visual Studio o altri prodotti correlati e non si disponga di una connessione a Internet. Con alcune unità o configurazioni di sistema, tuttavia, è possibile che non si voglia tenere nel sistema tutti questi pacchetti.
Il programma di installazione li scarica solo se necessario e quindi, per risparmiare o recuperare spazio su disco, è possibile disabilitare o spostare la cache dei pacchetti.

## <a name="disable-the-package-cache"></a>Disabilitare la cache dei pacchetti

Prima di installare, modificare o ripristinare Visual Studio o altri prodotti con il nuovo programma di installazione, è possibile avviare il programma di installazione con l'opzione `--nocache`.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Qualsiasi operazione eseguita su un prodotto rimuoverà tutti i pacchetti esistenti per il prodotto ed eviterà di dover salvare i pacchetti dopo averli installati. Se si modifica o si ripristina Visual Studio e i pacchetti sono necessari, verranno automaticamente scaricati e rimossi dopo l'installazione.

Se si vuole abilitare nuovamente la cache, passare invece `--cache`. Verranno memorizzati nella cache solo i pacchetti necessari. Pertanto, se devono essere ripristinati tutti i pacchetti, prima di disconnettere Visual Studio dalla rete è necessario ripristinarlo.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

È possibile anche impostare i  [criteri del Registro di sistema](set-defaults-for-enterprise-deployments.md)`KeepDownloadedPayloads` per disabilitare la cache prima di installare, modificare o ripristinare Visual Studio.

## <a name="move-the-package-cache"></a>Spostare la cache dei pacchetti

Una configurazione di sistema comune prevede Windows installato in un'unità SSD con un disco rigido più grande (o più dischi rigidi) riservato per le esigenze di sviluppo, ad esempio per codice sorgente, file binari del programma e altro ancora. Se si preferisce lavorare offline è invece possibile spostare la cache dei pacchetti.

Attualmente è possibile eseguire questa operazione solo se si impostano i  [criteri del Registro di sistema](set-defaults-for-enterprise-deployments.md)`CachePath` prima di installare, modificare o ripristinare Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Impostare i valori predefiniti per le distribuzioni aziendali](set-defaults-for-enterprise-deployments.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
