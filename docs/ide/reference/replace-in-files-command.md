---
title: Comando Sostituisci nei file
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565474"
---
# <a name="replace-in-files-command"></a>Comando Sostituisci nei file
Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argomenti
`findwhat`

Richiesto. Testo da cercare.

`replacewith`

Richiesto. Il testo di sostituzione per il testo corrispondente.

## <a name="switches"></a>Opzioni
/all o /a

Parametro facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.

/case o /c

Parametro facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

/ext: `extensions`

Parametro facoltativo. Specifica l'estensione dei file nei quali eseguire la ricerca.

/keep o /k

Parametro facoltativo. Indica che tutti i file modificati vengono lasciati aperti.

/lookin: `searchpath`

Parametro facoltativo. Directory in cui eseguire la ricerca. Se il percorso contiene spazi, racchiudere l'intero percorso tra virgolette.

/options o /t

Parametro facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

/regex o /r

Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

/reset o /e

Parametro facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

/stop

Parametro facoltativo. Se è in corso un'operazione di ricerca, la interrompe. Quando viene specificato `/stop` la sostituzione ignora tutti gli altri argomenti. Ad esempio, per interrompere la sostituzione corrente immettere quanto segue:

```
>Edit.ReplaceinFiles /stop
```

/sub o /s

Parametro facoltativo. Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento /lookin:`searchpath`.

/text2 o /2

Parametro facoltativo. Visualizza i risultati della sostituzione nella finestra **Risultati ricerca 2**.

/wild o /l

Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

/word o /w

Parametro facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
In questo esempio `btnCancel` viene cercato e sostituito con `btnReset` in tutti i file CLS presenti nella cartella "my visual studio projects" e le informazioni relative alle sostituzioni vengono visualizzate nella finestra **Risultati ricerca 2**.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Vedere anche

- [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)
- [Sostituisci nei file](../../ide/replace-in-files.md)
- [Command Window](../../ide/reference/command-window.md) (Finestra di comando)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
