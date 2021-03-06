---
title: Versioni di debug delle funzioni di allocazione heap | Microsoft Docs
description: Usare le versioni di debug delle funzioni di allocazione heap nella libreria di runtime del linguaggio C. Queste funzioni hanno gli stessi nomi delle versioni di rilascio con _dbg accodato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eedf9259f7bc62f32ca563d863a7fb686b8f6f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873119"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versioni di debug di funzioni di allocazione heap
La libreria di runtime del linguaggio C contiene speciali versioni di debug delle funzioni di allocazione heap. Queste funzioni presentano lo stesso nome delle corrispondenti versioni di rilascio, con l'unica differenza del suffisso _dbg. Questo argomento illustra le differenze tra la versione di rilascio di una funzione CRT e la versione _dbg, utilizzando `malloc` e `_malloc_dbg` come esempi.

 Quando viene definito [_DEBUG](/cpp/c-runtime-library/debug) , CRT esegue il mapping di tutte le chiamate a [malloc](/cpp/c-runtime-library/reference/malloc) a [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Pertanto non è necessario riscrivere il codice utilizzando `_malloc_dbg` anziché `malloc` per sfruttarne i vantaggi durante il debug.

 È tuttavia possibile chiamare `_malloc_dbg` esplicitamente. La chiamata esplicita di `_malloc_dbg` presenta alcuni vantaggi supplementari:

- Registrazione delle allocazioni del tipo `_CLIENT_BLOCK`.

- Memorizzazione del file sorgente e del numero di riga nel punto in cui ha avuto luogo la richiesta di allocazione.

  Se non si desidera convertire le `malloc` chiamate a `_malloc_dbg` , è possibile ottenere le informazioni sul file di origine definendo [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), che fa in modo che il preprocessore esegua direttamente il mapping di tutte le chiamate a `malloc` a `_malloc_dbg` anziché basarsi su un wrapper `malloc` .

  Per registrare i tipi separati di allocazioni in blocchi client, è necessario chiamare `_malloc_dbg` direttamente e impostare il parametro `blockType` su `_CLIENT_BLOCK`.

  Quando _DEBUG non è definito, le chiamate a `malloc` non vengono disturbate, `_malloc_dbg` le chiamate a vengono risolte in `malloc` , la definizione di [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) viene ignorata e le informazioni sul file di origine che riguardano la richiesta di allocazione non vengono fornite. Dal momento che `malloc` non presenta alcun parametro di tipo di blocco, le richieste di tipi `_CLIENT_BLOCK` vengono gestite come allocazioni standard.

## <a name="see-also"></a>Vedi anche

- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)