---
title: -RunExit (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando RunExit devenv per compilare ed eseguire il progetto o la soluzione specificata, quindi chiudere l'IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 695996a6bde054d4e9ae79efdef1955ef93ef527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957881"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Compila ed esegue il progetto o la soluzione specificati e quindi chiude l'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argomenti

- *NomeSoluzione*

  Percorso completo e nome del file di soluzione.

- *Nome progetto*

  Percorso completo e nome del file di progetto.

- `/Out`*OutputFileName*

  facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Commenti

Compila ed esegue il progetto o la soluzione specificati in base alle impostazioni specificate per la configurazione della soluzione attiva. Questa opzione riduce a icona l'IDE durante l'esecuzione del progetto o della soluzione. Chiude l'IDE al termine dell'esecuzione del progetto o della soluzione.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/Out`.

## <a name="example"></a>Esempio

In questo esempio la soluzione `MySolution` viene eseguita nell'IDE ridotto a icona usando la configurazione distribuzione attiva e quindi l'IDE viene chiuso.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
