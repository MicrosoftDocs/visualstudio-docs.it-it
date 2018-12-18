---
title: Opzione /setup (devenv.exe) | Microsoft Docs
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eee6e30a7489f5097cb17a19513c2a423187c827
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

L'opzione /setup impone a Visual Studio l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i pacchetti VSPackage disponibili.

## <a name="syntax"></a>Sintassi

```shell
devenv /setup
```

## <a name="remarks"></a>Note

Questa opzione non accetta argomenti. Il comando `devenv /setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'opzione `/setup` non causa l'avvio di Visual Studio.

> [!NOTE]
> Per poter usare l'opzione `/setup`, è necessario eseguire `devenv` come amministratore.

## <a name="example"></a>Esempio

Questo esempio illustra l'ultimo passaggio dell'installazione di una versione di Visual Studio che include pacchetti VSPackage.

```shell
devenv /setup
```

## <a name="see-also"></a>Vedere anche

[Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)