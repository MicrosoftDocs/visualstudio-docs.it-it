---
title: Funzioni intrinseche | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c25c76ba43c983a6029c8d50e183ccf839ef08bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="intrinsic-functions"></a>Funzioni intrinseche
Un'espressione in SAL può essere un'espressione C/C++ a condizione che sia un'espressione che non produca effetti collaterali, ad esempio ++, -- e le chiamate di funzione hanno effetti collaterali in questo contesto.  Tuttavia, SAL forniscono alcuni oggetti di tipo funzione e alcuni simboli riservati che possono essere utilizzate nelle espressioni di SAL. Queste sono denominate *funzioni intrinseche*.  
  
## <a name="general-purpose"></a>Utilizzo generico  
 Le seguenti annotazioni di funzioni intrinseche forniscono l'utilità generale per SAL.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_Curr_`|Sinonimo dell'oggetto attualmente annotato.  Quando viene utilizzata l'annotazione `_At_`, `_Curr_` è identica al primo parametro di `_At_`.  In caso contrario, è il parametro o l'intera funzione/valore restituito con cui l'annotazione è lessicalmente associata.|  
|`_Inexpressible_(expr)`|Esprime una situazione in cui la dimensione di un buffer è troppo complessa per essere rappresentata con un'espressione di annotazione, ad esempio quando viene calcolata esaminando un set di dati di input e successivamente contando i membri selezionati.|  
|`_Nullterm_length_(param)`|`param`è il numero di elementi nel buffer fino a, ma non con un carattere di terminazione null. Può essere applicato a un buffer di tipo non di aggregazione, non void.|  
|`_Old_(expr)`|Una volta valutato nella precondizione, `_Old_` restituisce il valore di input `expr`.  Una volta valutato nella post condizione, restituisce il valore `expr` come sarebbe stato valutato nella precondizione.|  
|`_Param_(n)`|Il `n`parametro a una funzione, il conteggio da 1 a `n`, e `n` è una valore letterale costante integrale. Se il parametro è denominato, questa annotazione è identica al parametro di accesso in base al nome. **Nota:** `n` possono fare riferimento ai parametri posizionali definiti dai puntini di sospensione o possono essere utilizzati in prototipi di funzione in cui i nomi non vengono utilizzati.|  
|`return`|Parola chiave riservata di C/C++ `return` può essere utilizzato in un'espressione SAL per indicare il valore restituito di una funzione.  Il valore è disponibile solo nello stato di post; è un errore di sintassi utilizzarlo in uno stato di pre.|  
  
## <a name="string-specific"></a>Stringa specifica  
 Le seguenti annotazioni di funzioni intrinseche abilitano la modifica delle stringhe. Tutte e quattro queste funzioni presentano lo stesso scopo: restituire il numero di elementi del tipo trovati prima di un terminatore null. Le differenze sono i tipi di dati negli elementi a cui fanno riferimento. Si noti che se si desidera specificare la lunghezza del buffer con terminazione null che non è composto da caratteri, utilizzare l'annotazione di `_Nullterm_length_(param)` dalla sezione precedente.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`è il numero di elementi nella stringa fino a ma non incluso un terminatore null. Questa annotazione è riservata per tipi di carattere della stringa.|  
|`strlen(param)`|`param`è il numero di elementi nella stringa fino a ma non incluso un terminatore null. Questa annotazione è riservata all'utilizzo in carattere matrici ed è simile alla funzione Runtime C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param`il numero di elementi nella stringa di backup a (escluso) è un carattere di terminazione null. Questa annotazione è riservata all'utilizzo in un carattere wide matrici ed è simile alla funzione Runtime C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Esempi e procedure consigliate](../code-quality/best-practices-and-examples-sal.md)