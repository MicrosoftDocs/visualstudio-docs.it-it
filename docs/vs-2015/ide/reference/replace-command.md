---
title: Comando Sostituisci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665620"
---
# <a name="replace-command"></a>Comando Sostituisci
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argomenti
 `findwhat` Obbligatorio. Testo da cercare.

 `replacewith` Obbligatorio. Il testo di sostituzione per il testo corrispondente.

## <a name="switches"></a>Opzioni
 /o/a facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.

 /case o /c Facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

 /doc o /d Facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /Hidden o/h facoltativo. Cerca il testo compresso e nascosto, come i metadati di un controllo DTC, un'area nascosta di un documento strutturato o un metodo o una classe compressi.

 /open or /o Facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /open or /o Facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

 /proc o /p Facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /regex o /r Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset o /e Facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

 /sel o /s Facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /up o/u Facoltativo. Esegue la ricerca dalla posizione corrente nel file verso la parte superiore del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione del file e procedono verso la fine del file.

 /wild o /l Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

 /word o /w Facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
 In questo esempio `btnSend` con `btnSubmit` tutti i documenti aperti.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Vedere anche
 [Ricerca e sostituzione della finestra di comando di testo](../../ide/finding-and-replacing-text.md) [finestra](../../ide/reference/command-window.md) di [dialogo Trova/comando](../../ide/find-command-box.md) di [Visual Studio comandi](../../ide/reference/visual-studio-commands.md) Visual Studio alias di [comando](../../ide/reference/visual-studio-command-aliases.md)
