---
title: OpenCV
description: Personalizzazione di esempio mediante devinit per il repository OpenCV/OpenCV.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: dd8a17635b70d0f9f49852d09d8f1b9a6864e26e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809097"
---
# <a name="opencv"></a>OpenCV

Questo esempio illustra le personalizzazioni necessarie per eseguire il provisioning automatico di [OpenCV](https://github.com/opencv/opencv) con [spazi dei codebase GitHub] https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.js

Contenuto del [_.devinit.jssu_](devinit-json.md) file. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js

Contenuto del _.devcontainer.js_ nel file nella radice del repository.

```json
{
  "postCreateCommand": "devinit init"
}
```