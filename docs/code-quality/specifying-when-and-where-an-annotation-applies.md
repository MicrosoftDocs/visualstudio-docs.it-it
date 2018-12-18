---
title: Specificare dove e quando applicare un'annotazione
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 288d422de6d4e4c0f372820d838d0173c990f2a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Specificare dove e quando applicare un'annotazione
Quando un'annotazione è condizionale, potrebbe essere necessario altre annotazioni per specificare che per l'analizzatore.  Ad esempio, se una funzione dispone di una variabile che può essere sincrona o asincrona, la funzione si comporta come segue: nel caso sincrono sempre andrà a buon fine, ma nel caso asincrono viene segnalato un errore se il tentativo non riesce immediatamente. Quando la funzione viene chiamata in modo sincrono, controllando il valore di risultato non fornisce alcun valore per l'analizzatore di codice, poiché potrebbe non avere restituito.  Tuttavia, quando la funzione viene chiamata in modo asincrono e il risultato della funzione non è selezionato, può verificarsi un errore grave. Questo esempio viene illustrata una situazione in cui è possibile utilizzare il `_When_` annotazione, descritto più avanti in questo articolo, abilitare il controllo.

## <a name="structural-annotations"></a>Annotazioni strutturali
 Per controllare dove e quando applicano le annotazioni, utilizzare le seguenti annotazioni strutturale.

|Annotazione|Descrizione|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` è un'espressione che produce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato in precondizione se l'annotazione viene interpretata in precondizione, e nella postcondizione se l'annotazione nella postcondizione.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` è un'espressione che produce un lvalue. Le annotazioni in `anno-list` vengono applicati all'oggetto denominato da `expr`. Per ciascuna annotazione in `anno-list`, `expr` viene interpretato in precondizione se l'annotazione viene interpretata in precondizione, e nella postcondizione se l'annotazione nella postcondizione.<br /><br /> `iter` è il nome di una variabile con ambito limitato all'annotazione (comprende `anno-list`). `iter` è un tipo implicito `long`. Le variabili denominate in modo identico in qualsiasi ambito contenitore sono nascosti dalla valutazione.<br /><br /> `elem-count` è un'espressione che restituisce un numero intero.|
|`_Group_(anno-list)`|Le annotazioni in `anno-list` vengono tutti considerati qualsiasi qualificatore che si applica all'annotazione di gruppo applicati a ciascuna annotazione.|
|`_When_(expr, anno-list)`|`expr` è un'espressione che può essere convertita in `bool`. Quando è diverso da zero (`true`), le annotazioni vengono specificate in `anno-list` sono considerati applicabile.<br /><br /> Per impostazione predefinita, per ciascuna annotazione in `anno-list`, `expr` viene interpretato come utilizza i valori di input se l'annotazione è una precondizione, come con i valori di output se l'annotazione è una postcondizione. Per ignorare l'impostazione predefinita, è possibile utilizzare il `_Old_` intrinseco quando si valuta una post-condizione di per indicare che i valori di input devono essere utilizzati. **Nota:** diverse annotazioni potrebbero essere abilitate come conseguenza utilizzando `_When_` se un valore modificabile, ad esempio, `*pLength`: è coinvolto in quanto risultato valutato del `expr` nella precondizione differiscano dalle relative valutata comportare postcondizione.|

## <a name="see-also"></a>Vedere anche
 [Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [comprensione SAL](../code-quality/understanding-sal.md) [annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md) [annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md) [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md) [annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md) [funzioni intrinseche](../code-quality/intrinsic-functions.md) [suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)