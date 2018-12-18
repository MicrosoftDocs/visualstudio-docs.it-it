---
title: errori di FxCopCmd
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3928eb62baa16296ab009118c4e3b075e7dd3268
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="fxcopcmd-tool-errors"></a>Errori di FxCopCmd strumento

FxCopCmd non considera tutti gli errori irreversibili. Se FxCopCmd dispone di informazioni sufficienti per eseguire un'analisi parziale, esegue l'analisi e segnala gli errori che si sono verificati. Il codice di errore è un intero a 32 bit, contiene una combinazione bit per bit di valori numerici che corrispondono agli errori.

Nella tabella seguente vengono descritti i codici di errore restituiti da FxCopCmd:

|Error|Valore numerico|
|-----------|-------------------|
|Senza errori|0x0|
|Errore di analisi|0x1|
|Eccezioni alle regole|0x2|
|Errore di caricamento progetto|0x4|
|Errore di caricamento assembly|0x8|
|Errore durante il caricamento della libreria regola|0x10|
|Errore durante il caricamento report importazione|0x20|
|Errore di output|0x40|
|Errore di opzione della riga di comando|0x80|
|Errore di inizializzazione|0x100|
|Errore di riferimento ad assembly|0x200|
|BuildBreakingMessage|0x400|
|Errore sconosciuto|0x1000000|

**Errore di analisi** viene restituito per gli errori irreversibili. Indica che l'analisi non riuscita. Quando applicabile, il codice di errore contiene anche la causa dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:

- L'analisi potrebbe non essere eseguita a causa di input insufficienti.

- L'analisi ha generato un'eccezione non gestita da FxCopCmd.

- Il file di progetto specificato non è stato trovato o è danneggiato.

- Non è stata specificata l'opzione di output o il file non è stato scritto.

> [!NOTE]
> Codice restituito di FxCopCmd **Assembly fa riferimento all'errore** 0x200 da se stessa è un avviso anziché un errore. Questo codice restituito indica che mancano i riferimenti indiretti, ma che FxCopCmd è stato in grado di gestirle. L'avviso indica che è possibile che alcuni dei risultati dell'analisi potrebbero essere stata compromessa. Considerare **Assembly fa riferimento all'errore** come un errore quando viene combinato con qualsiasi altro codice restituito.

## <a name="see-also"></a>Vedere anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)