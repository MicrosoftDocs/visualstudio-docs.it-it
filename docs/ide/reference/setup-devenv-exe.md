---
title: Opzione /setup (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

L'opzione /setup impone a Visual Studio l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i pacchetti VSPackage disponibili.

## <a name="syntax"></a>Sintassi

```
devenv /setup
```

## <a name="remarks"></a>Note

Questa opzione non accetta argomenti. Il comando `devenv /setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'opzione `/setup` non causa l'avvio di Visual Studio.

Per poter usare le opzioni `devenv` e [devenv](../../ide/reference/setup-devenv-exe.md) è necessario eseguire [devenv](../../ide/reference/installvstemplates-devenv-exe.md) come amministratore.

## <a name="example"></a>Esempio

Questo esempio illustra l'ultimo passaggio dell'installazione di una versione di Visual Studio che include pacchetti VSPackage.

```
devenv /setup
```

## <a name="see-also"></a>Vedere anche

[Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)