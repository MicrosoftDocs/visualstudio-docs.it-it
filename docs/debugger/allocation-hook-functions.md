---
title: Funzioni Hook di allocazione | Documenti Microsoft
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe5ac5ec207bb52884c097d1562a85a3414ba7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hook-functions"></a>Funzioni hook di allocazione
Una funzione hook di allocazione, installata tramite [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), viene chiamato ogni volta che viene allocata, riallocata o liberata memoria. Questo tipo di funzione è utilizzabile per numerosi scopi differenti. È possibile usare le funzioni hook per verificare come un'applicazione gestisce situazioni di memoria insufficiente, ad esempio, oppure per esaminare schemi di allocazione o per registrare informazioni di allocazione da analizzare in seguito.  
  
> [!NOTE]
>  Tenere presente le restrizioni sull'utilizzo delle funzioni di libreria run-time C in una funzione hook di allocazione, descritto in [hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una funzione hook di allocazione dovrebbe avere un prototipo analogo al seguente:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Il puntatore passato a [CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) è di tipo **CRT_ALLOC_HOOK**, come definito in CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nAllocType* argomento indica quali allocazione operazione sta per essere eseguita (**HOOK_ALLOC**, **HOOK_REALLOC**, o **HOOK_FREE**). Nel caso di una liberazione o di una riallocazione, `pvData` conterrà un puntatore all'argomento utente del blocco che sarà liberato. Nel caso di un'allocazione, tuttavia, questo puntatore è nullo, poiché l'allocazione non ha ancora avuto luogo. I restanti argomenti contengono la dimensione dell'allocazione in questione, il tipo di blocco, il numero di richiesta sequenziale associato all'allocazione e un puntatore al nome file e al numero di riga in cui l'allocazione è stata effettuata, se tali informazioni sono disponibili. Dopo la funzione hook ha eseguito l'analisi e altre attività definite dall'autore, deve restituire **TRUE**, che indica che l'operazione di allocazione può continuare, o **FALSE**, a indicare che il operazione non riuscirà. Una semplice funzione hook di questo tipo può controllare la quantità di memoria allocata fino a quel momento e restituire **FALSE** se tale quantità eccede il limite di piccole dimensioni. L'applicazione sarà quindi soggetta agli errori di allocazione che in genere si verificano solo quando la memoria disponibile è molto scarsa. Funzioni hook più complesse possono tenere traccia degli schemi di allocazione, analizzare l'uso della memoria o informare del verificarsi di determinate situazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Hook di allocazione e allocazioni di memoria di runtime C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
