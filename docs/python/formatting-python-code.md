---
title: Formattazione del codice Python in Visual Studio | Microsoft Docs
description: Come riformattare automaticamente codice Python in Visual Studio inclusi spaziatura, istruzioni, ritorno a capo e commenti.
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: e68fff14ea51816ae45a29410d09cb6633689534
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="formatting-python-code"></a>Formattazione del codice Python

Visual Studio consente di riformattare rapidamente il codice in base a opzioni di formattazione preconfigurate.

- Per formattare una selezione, selezionare **Modifica > Avanzate > Formatta selezione** o premere CTRL+E,F.
- Per formattare l'intero file, selezionare **Modifica > Avanzate > Formatta documento** o premere CTRL+E,D.

Le opzioni vengono impostate mediante **Strumenti > Opzioni > Editor di testo > Python > Formattazione** e le relative schede annidate e per impostazione predefinita corrispondono a un superset della [guida di stile PEP 8](http://www.python.org/dev/peps/pep-0008/). La scheda **Generale** determina quando viene applicata la formattazione. Le impostazioni delle altre tre schede sono descritte in questo argomento.

Il [supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md) aggiunge anche l'utile comando [Riempi paragrafo di commento](#fill-comment-paragraph-command) al menu **Modifica > Avanzate** come descritto di seguito.

## <a name="spacing"></a>Spacing (Spaziatura)

La scheda **Spacing** (Spaziatura) consente di controllare la posizione in cui inserire o rimuovere gli spazi attorno a costrutti di linguaggio. Esistono tre possibili valori per ogni opzione:

- Selezionato con segno di spunta: assicura che la spaziatura venga applicata.
- Deselezionato: rimuove qualsiasi spaziatura.
- Indeterminato: mantiene la formattazione originale.

Le tabelle seguenti includono esempi per le varie opzioni:

| Opzione Class Definitions (Definizioni di classe) | Selezionato con segno di spunta | Deselezionato |
| --- | --- | --- | 
| Insert space between a class declaration's name and bases list (Inserisci spazio tra il nome della dichiarazione di classe e l'elenco di basi) | `class X (object): pass` | `class X(object): pass` | 
| Insert space within bases list parentheses (Inserisci spazio tra le parentesi dell'elenco di basi) | `class X( object ): pass` | `class X(object): pass` |
| Insert space within empty bases list parentheses (Inserisci spazio tra le parentesi dell'elenco di basi vuoto) | `class X( ): pass` | `class X(): pass` |

<br/>

| Opzione Function Definitions (Definizioni di funzioni) | Selezionato con segno di spunta | Deselezionato |
| --- | --- | --- |
| Insert space between a function declaration's name and parameter list (Inserisci spazio tra il nome della dichiarazione di funzione e l'elenco di parametri) | `def X (): pass` | `def X(): pass` | 
| Insert space within parameter list parentheses (Inserisci spazio tra le parentesi dell'elenco di parametri) | `def X( a, b ): pass` | `def X(a, b): pass` |
| Insert space within empty parameter list parentheses (Inserisci spazio tra le parentesi dell'elenco di parametri vuoto) | `def X( ): pass` | `def X(): pass` |
| Insert spaces around '=' in default parameter values (Inserisci spazi intorno a '=' nei valori di parametri predefiniti) | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Insert space before and after return annotation operators (Inserisci spazio prima e dopo gli operatori di annotazione di restituzione) | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opzione Operators (Operatori) | Selezionato con segno di spunta | Deselezionato |
| --- | --- | --- |
| Insert spaces around binary operators (Inserisci spazi intorno agli operatori binari) | `a + b` | `a+b` |
| Insert spaces around assignments (Inserisci spazi intorno alle assegnazioni) | `a = b` | `a=b` |

<br/>

| Opzione Expression spacing (Spaziatura espressioni) | Selezionato con segno di spunta | Deselezionato |
| --- | --- | --- |
| Insert space between a function call's name and argument list (Inserisci spazio tra il nome della chiamata di funzione e l'elenco di argomenti) | `X ()` | `X()` |
| Inserisci spazio tra le parentesi dell'elenco di argomenti vuoto | `X( )` | `X()` |
| Inserisci spazio tra le parentesi dell'elenco di argomenti | `X( a, b )` | `X(a, b)` |
| Insert space within parentheses of expression (Inserisci spazio tra le parentesi delle espressioni) | `( a )` | `(a)` |
| Insert space within empty tuple parentheses (Inserisci spazio tra parentesi tuple vuote) | `( )` | `()` |
| Insert space within tuple parentheses (Inserisci spazio tra parentesi tuple) | `( a, b )` | `(a, b)` |
| Inserisci spazio tra parentesi quadre vuote | `[ ]` | `[]` |
| Insert spaces within square brackets of lists (Inserisci spazi tra parentesi quadre di elenchi) | `[ a, b ]` | `[a, b]` |
| Inserisci spazio prima della parentesi quadra di apertura | `x [i]` | `x[i]` |
| Inserisci uno spazio tra parentesi quadre | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Istruzioni

Le opzioni relative alle **istruzioni** consentono di controllare la riscrittura automatica di varie istruzioni in altri formati Python.

| Opzione | Prima della formattazione | Dopo la formattazione |
| --- | --- | --- |
| Place imported modules on new line (Inserisci moduli importati in una nuova riga) | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Remove unnecessary semicolons (Rimuovi punti e virgola non necessari) | `x = 42;` | `x = 42` |
| Place multiple statements on new lines (Inserisci più istruzioni in nuove righe) | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Wrapping (Ritorno a capo)

**Wrapping** consente di impostare la **larghezza massima dei commenti**, che per impostazione predefinita è 80. Se viene impostata l'opzione **Esegui il wrapping dei commenti troppo lunghi**, Visual Studio riformatta i commenti in modo che non superino la larghezza massima.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Comando Fill Comment Paragraph (Riempi paragrafo commenti)

Il comando **Modifica > Avanzate > Riempi paragrafo di commento** (CTRL+E, P) ridefinisce il flusso e la formattazione del testo dei commenti, riunendo le righe brevi e suddividendo quelle lunghe.

Ad esempio:

```python
# foo
# bar
# baz
```

diventa:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

diventa:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```