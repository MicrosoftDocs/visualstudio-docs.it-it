---
title: wsl-install
description: strumento devinit WSL-install.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4dff121d7866918d5c30986dc9bd4c3cab039ac5
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672425"
---
# <a name="wsl-install"></a>wsl-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `wsl-install` strumento viene usato per installare le distribuzioni di Linux per il [sottosistema Windows per Linux](/windows/wsl/) (WSL).

> [!IMPORTANT]
> Lo `wsl-install` strumento richiede che WSL 2 sia già abilitato in Windows. Se per qualche motivo WSL 2 non è abilitato, è possibile seguire la [documentazione di installazione di WSL](https://docs.microsoft.com/windows/wsl/install-win10). È anche possibile usare lo strumento [WindowsFeature-Enable](tool-windowsfeature-enable.md) per abilitare le funzionalità di Windows necessarie.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                             |
| [**input**](#input)                              | string | Sì      | Distro da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.     |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.  |

### <a name="input"></a>Input

URI del pacchetto di distribuzione dell'applicazione AppX ( `.appx` ) che contiene la distribuzione da distribuire. L'URI deve puntare a un `.appx` archivio che contiene un singolo oggetto `install.tar.gz` nella radice dell'archivio o all'interno di un `.appx` archivio interno. Esempi di distribuzioni supportate includono:

| Distribuzione                          | Uri                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> Le distribuzioni Linux ARM non sono attualmente supportate negli spazi di codespace di GitHub.

### <a name="additional-options"></a>Opzioni aggiuntive

Sono supportate più opzioni aggiuntive:

| Nome                      | Tipo      | Obbligatoria | valore                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-Version             | stringa    | No       | Versione di WSL da usare. Il valore predefinito è 2.                                                                                                                                  |
| --Post-creazione-comando     | stringa    | No       | Comando da eseguire all'interno della distribuzione di Linux una volta completata l'installazione. Il comando deve essere formattato come una singola parola o racchiuso tra virgolette. Il valore predefinito è no Command.  |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `wsl-install` strumento è l'errore come la `input` proprietà, la distro da installare, è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati alcuni esempi di come eseguire `wsl-install` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.jssu che installerà Ubuntu 20,04:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.jssu che installerà Ubuntu 20,04 ed eseguirà un comando post-creazione:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.jssu che installerà Ubuntu 20,04 ed eseguirà un comando post-creazione che configura i pacchetti elencati:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
