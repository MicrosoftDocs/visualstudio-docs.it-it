---
title: IntelliSense per codice R in Visual Studio | Microsoft Docs
description: Visual Studio IntelliSense visualizza informazioni sulle funzioni, i membri dell'oggetto, frammenti di codice e i completamenti durante la digitazione di codice R.
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: de74bd82efc3a0ecc07d31fc830ffabb1d45093c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense visualizza informazioni sulle funzioni che è possibile chiamare, sui membri di oggetti, sugli argomenti della funzione e sui [frammenti di codice](code-snippets-for-r.md) direttamente durante la scrittura del codice. Visualizza anche i possibili completamenti durante la digitazione e completa quando si preme TAB o INVIO (vedere le [opzioni dell'editor](editing-r-code-in-visual-studio.md#editor-options) nella scheda **Avanzate**). Intellisense è disponibile sia nell'editor che nella[ finestra interattiva](interactive-repl-for-r-in-visual-studio.md).

![Visualizzazione di una firma della funzione di IntelliSense](media/intellisense-function-signature.png)

Durante la digitazione di una funzione o di un'altra istruzione, IntelliSense offre menu di completamento automatico (con distinzione tra maiuscole e minuscole) filtrato in base ai valori che sono già stati immessi:

![Menu di completamento automatico di IntelliSense](media/intellisense-auto-complete-menu.png)

Premendo TAB (o INVIO o BARRA SPAZIATRICE a seconda delle opzioni impostate) è possibile inserire l'elemento selezionato nell'elenco a discesa. È possibile modificare la selezione con i tasti di direzione.

IntelliSense offre anche suggerimenti per i membri di oggetti R:

![Suggerimenti di IntelliSense per i membri di un oggetto](media/intellisense-auto-complete-r-objects.png)

Se si preme ESC, l'intero menu scompare. È possibile ripristinarlo premendo CTRL+BARRA SPAZIATRICE.

Se si digita il segno di `(` aperta per una chiamata di funzione viene inserito il segno di `)` chiusa e viene ripristinato il supporto per la firma come illustrato in precedenza:

![Supporto per la firma per una funzione di IntelliSense](media/intellisense-function-signature.png)

Premere nuovamente ESC per chiudere la finestra popup. È possibile ripristinarla per le firme della funzione premendo CTRL+MAIUSC+BARRA SPAZIATRICE.

> [!Tip]
> Se la guida del parametro nasconde il testo sottostante, premere e tenere premuto il tasto CTRL per rendere semitrasparente il testo della guida.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense per variabili e funzioni definite dall'utente

IntelliSense viene applicato anche per il completamento del parametro "name" di funzioni definite dall'utente nello stesso file:

![IntelliSense per funzioni definite dall'utente](media/intellisense-same-file-functions.png)

![Completamento parametri di IntelliSense per funzioni definite dall'utente](media/intellisense-parameter-completion.png)

IntelliSense viene applicato anche a variabili nello stesso file e nella sessione corrente:

![Completamento variabili di IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Nella finestra interattiva IntelliSense prende in considerazione solo i nomi nella sessione corrente di R e ignora i file nel progetto.

## <a name="code-suggestions"></a>Suggerimenti di codice

Quando al margine viene visualizzata una lampadina, detta smart tag, significa che Visual Studio sta suggerendo un collegamento per una delle azioni più usate. Ad esempio, passare il puntatore su una riga che contiene un'istruzione `library` nell'editor per visualizzare una lampadina. Selezionando la lampadina, verranno visualizzate le opzioni disponibili:

![Smart tag per R nell'editor](media/intellisense-smart-tags.png)
