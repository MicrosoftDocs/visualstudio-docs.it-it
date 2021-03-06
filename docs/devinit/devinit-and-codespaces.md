---
title: devinit e GitHub Codespaces
description: Informazioni su come personalizzare un codespace per Visual Studio usando devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c98c00e0b62d3a2a755790b07621d717abcb41c1
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672221"
---
# <a name="devinit-and-github-codespaces"></a>devinit e GitHub Codespaces

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

devinit è un ottimo complemento per gli spazi codebase di [GitHub](https://github.com/features/codespaces) e il devinit può essere usato per ottenere un'installazione di codespace, in modo che i collaboratori possano creare, eseguire ed eseguire il debug immediatamente.

> [!IMPORTANT]
> Prima di integrare la devinit con lo spazio codespace, prima di tutto è necessario assicurarsi di disporre di un `.devinit.json` file che definisce le dipendenze. Per ulteriori informazioni su come creare un `.devinit.json` , leggere la [documentazione](getting-started-with-devinit.md)introduttiva.

All'interno di un codespace GitHub, l'applicazione viene compilata ed eseguita nel cloud. Nel cloud significa che l'applicazione non ha accesso alle risorse locali nei computer. Sono inclusi gli strumenti o i programmi installati localmente. Se l'applicazione richiede l'installazione o la configurazione di dipendenze a livello di sistema, è necessario eseguire questa operazione in ogni codespace. Il modo più semplice per ottenere questo risultato consiste nell'usare un `.devinit.json` file.

Per assicurarsi che venga creato un codespace con le dipendenze necessarie per l'applicazione, è necessario `devinit` eseguire quando viene creato lo spazio dei codespace. Questa operazione può essere eseguita chiamando `devinit init` dall'oggetto `postCreateCommand` definito in un `.devcontainer.json` file inserito nella radice del repository. Le stringhe in `postCreateCommand` vengono eseguite nella shell predefinita, dopo la clonazione del repository nello spazio dei valori. Per altre informazioni, vedere `postCreateCommand` la [documentazione di personalizzazione](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)di GitHub codespaces. Per aggiungere il `devinit` comando, è possibile aggiungere `devinit init` a `postCreateCommand` come illustrato negli esempi seguenti.

È anche possibile eseguire `devinit init -f <path to .devinit.json>` dal terminale integrato di Visual Studio dopo essersi connessi al codespace.

## <a name="examples"></a>Esempio

In entrambi gli esempi riportati di seguito il `.devinit.json` si trova nella radice del repository insieme a `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>Con un .devcontainer.jssu file

In questo esempio il `.devcontainer.json` file seguente viene inserito nella radice del repository insieme al `.devinit.json` file. I file possono essere inseriti anche in una `.devcontainer` Directory.

```json
{
  "postCreateCommand": "devinit init"
}
```

Quando `.devinit.json` si trova in un'altra directory, è possibile usare il flag-f.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Per ulteriori esempi di utilizzo di devinit, vedere la [documentazione](sample-all-tool.md) di e in GitHub nell' [esempio .net core](https://github.com/microsoft/devinit-example-dotnet-core) e [Node.js](https://github.com/microsoft/devinit-example-nodejs) repository di esempio.

### <a name="as-commands"></a>Come comandi

In questo esempio, `.devcontainer.json` il file seguente viene inserito nella radice del repository e `devinit run` viene chiamato direttamente dalla riga di comando per eseguire un singolo strumento.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Da un prompt dei terminali

Quando la directory di lavoro corrente contiene un `.devinit.json` file.

```console
devinit init
```

Quando `.devinit.json` si trova in un'altra directory.

```console
devinit init -f path/to/.devinit.json
```
