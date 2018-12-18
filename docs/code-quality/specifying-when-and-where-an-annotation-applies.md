---
title: Specificare dove e quando applicare un'annotazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eaca3429ccc1defe51ee849bf46146931390a571
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Specificare dove e quando applicare un'annotazione
Quando un'annotazione è condizionale, potrebbe essere necessario altre annotazioni per specificare che per l'analizzatore.  Ad esempio, se una funzione dispone di una variabile che può essere sincrona o asincrona, la funzione si comporta come segue: nel caso sincrono sempre andrà a buon fine, ma nel caso asincrono viene segnalato un errore se il tentativo non riesce immediatamente. Quando la funzione viene chiamata in modo sincrono, controllando il valore di risultato non fornisce alcun valore per l'analizzatore di codice, poiché potrebbe non avere restituito.  Tuttavia, quando la funzione viene chiamata in modo asincrono e il risultato della funzione non è selezionato, può verificarsi un errore grave. Questo esempio viene illustrata una situazione in cui è possibile utilizzare il `_When_` annotazione, descritto più avanti in questo articolo, abilitare il controllo.  
  
## <a name="structural-annotations"></a>Annotazioni strutturali  
 Per controllare dove e quando applicano le annotazioni, utilizzare le seguenti annotazioni strutturale.  
  
|Annotazione|Descrizione|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr`è un'espressione che restituisce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato in precondizione se l'annotazione viene interpretata in precondizione, e nella postcondizione se l'annotazione nella postcondizione.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`è un'espressione che restituisce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato in precondizione se l'annotazione viene interpretata in precondizione, e nella postcondizione se l'annotazione nella postcondizione.<br /><br /> `iter`è il nome di una variabile con ambito limitato all'annotazione (comprende `anno-list`). `iter`è un tipo implicito `long`. Le variabili denominate in modo identico in qualsiasi ambito contenitore sono nascosti dalla valutazione.<br /><br /> `elem-count`è un'espressione che restituisce un valore intero.|  
|`_Group_(anno-list)`|Le annotazioni in `anno-list` vengono tutti considerati qualsiasi qualificatore che si applica all'annotazione di gruppo applicati a ciascuna annotazione.|  
|`_When_(expr, anno-list)`|`expr`è un'espressione che può essere convertita in `bool`. Quando è diverso da zero (`true`), le annotazioni vengono specificate in `anno-list` sono considerati applicabile.<br /><br /> Per impostazione predefinita, per ciascuna annotazione in `anno-list`, `expr` viene interpretato come utilizza i valori di input se l'annotazione è una precondizione, come con i valori di output se l'annotazione è una postcondizione. Per ignorare l'impostazione predefinita, è possibile utilizzare il `_Old_` intrinseco quando si valuta una post-condizione di per indicare che i valori di input devono essere utilizzati. **Nota:** diverse annotazioni potrebbero essere abilitate come conseguenza mediante `_When_` se un valore modificabile, ad esempio, `*pLength`: è complessa, poiché è risultato valutato del `expr` in precondizione può differire dal relativo valutata generare postcondizione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Esempi e procedure consigliate](../code-quality/best-practices-and-examples-sal.md)