---
title: Versioni di debug delle funzioni di allocazione Heap | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
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
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63642402f6e98e42b2d4954a6065f61fb61159b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versioni di debug di funzioni di allocazione heap
La libreria di runtime del linguaggio C contiene speciali versioni di debug delle funzioni di allocazione heap. Queste funzioni presentano lo stesso nome delle corrispondenti versioni di rilascio, con l'unica differenza del suffisso _dbg. Questo argomento illustra le differenze tra la versione di rilascio di una funzione CRT e la versione _dbg, utilizzando `malloc` e `_malloc_dbg` come esempi.  
  
 Quando [debug](/cpp/c-runtime-library/debug) è definito, CRT associa tutti [malloc](/cpp/c-runtime-library/reference/malloc) le chiamate a [malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Pertanto non è necessario riscrivere il codice utilizzando `_malloc_dbg` anziché `malloc` per sfruttarne i vantaggi durante il debug.  
  
 È tuttavia possibile chiamare `_malloc_dbg` esplicitamente. La chiamata esplicita di `_malloc_dbg` presenta alcuni vantaggi supplementari:  
  
-   Registrazione delle allocazioni del tipo `_CLIENT_BLOCK`.  
  
-   Memorizzazione del file sorgente e del numero di riga nel punto in cui ha avuto luogo la richiesta di allocazione.  
  
 Se non si desidera convertire la `malloc` le chiamate a `_malloc_dbg`, è possibile ottenere le informazioni sul file di origine definendo [CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), che comporta la mappa per il preprocessore direttamente tutte le chiamate a `malloc` a `_malloc_dbg` anziché di un wrapper `malloc`.  
  
 Per registrare i tipi separati di allocazioni in blocchi client, è necessario chiamare `_malloc_dbg` direttamente e impostare il parametro `blockType` su `_CLIENT_BLOCK`.  
  
 Se non è definito debug, le chiamate a `malloc` non vengono disturbate, le chiamate a `_malloc_dbg` vengono risolte in `malloc`, la definizione di [CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) viene ignorato e l'origine di informazioni sui file che riguardano il richiesta di allocazione non è disponibile. Dal momento che `malloc` non presenta alcun parametro del tipo di blocco, le richieste di tipi `_CLIENT_BLOCK` vengono gestite come allocazioni standard.  
  
## <a name="see-also"></a>Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)