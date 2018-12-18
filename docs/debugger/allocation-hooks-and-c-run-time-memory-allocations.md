---
title: Hook di allocazione e allocazioni di memoria di runtime C | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b123e0e03f33f54e6d4fe82313c9a017e3baafff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Hook di allocazione e allocazioni di memoria di runtime C
Una restrizione molto importante che riguarda le funzioni hook di allocazione è che esse devono esplicitamente ignorare i blocchi `_CRT_BLOCK` (le allocazioni di memoria effettuate internamente dalle funzioni dalla libreria di runtime del linguaggio C) se tali blocchi effettuano chiamate a funzioni della libreria di runtime del linguaggio C che allocano memoria interna. È possibile far sì che i blocchi `_CRT_BLOCK` vengano ignorati includendo, all'inizio della funzione hook di allocazione, un codice del seguente tipo:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Se la funzione hook di allocazione non ignora i blocchi `_CRT_BLOCK`, qualsiasi funzione della libreria di runtime del linguaggio C chiamata nella funzione hook rischia di intrappolare il programma in un ciclo senza termine. Ad esempio, `printf` crea un'allocazione interna. Se il codice hook chiama `printf`, l'allocazione risulta genererà la funzione hook chiamato nuovamente, verrà chiamato **printf** nuovamente, e così via fino a quando non causa un overflow dello stack. Se è necessario segnalare le operazioni di allocazione `_CRT_BLOCK`, un modo per ovviare a questa limitazione consiste nell'utilizzare funzioni API Windows, anziché funzioni di runtime del linguaggio C, per la formattazione e l'output. Dal momento che le API Windows non utilizzano l'heap della libreria di runtime del linguaggio C, esse non bloccheranno la funzione hook di allocazione in un ciclo senza termine.  
  
 Se si esaminano i file di origine della libreria run-time, si noterà che l'allocazione predefinita funzione hook, **CrtDefaultAllocHook** (che restituisce semplicemente **TRUE**), si trova in un file separato propri, DBGHOOK. C. Se si desidera l'hook di allocazione di essere chiamata anche per le allocazioni eseguite dal codice di avvio in fase di esecuzione che viene eseguito prima dell'applicazione **principale** funzione, è possibile sostituire questa funzione predefinita con uno proprio, anziché utilizzando [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
