---
title: Usare _Analysis_assume per gli hint di analisi del codice
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1fec348108afdfe3cdac3325e0a1750b55332db4
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271647"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Procedura: specificare informazioni aggiuntive sul codice utilizzando _Analysis_assume

È possibile fornire suggerimenti allo strumento di analisi del codice per CC++ /code che consente il processo di analisi e la riduzione degli avvisi. Per fornire informazioni aggiuntive, utilizzare la funzione seguente:

`_Analysis_assume(`  `expr`  `)`

`expr`: qualsiasi espressione che si presuppone restituisca true.

Lo strumento di analisi del codice presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui viene visualizzata la funzione e rimanga true fino a quando l'espressione non viene modificata, ad esempio per assegnazione a una variabile.

> [!NOTE]
> `_Analysis_assume` non influisca sull'ottimizzazione del codice. Al di fuori dello strumento di analisi del codice, `_Analysis_assume` viene definito come no-op.

## <a name="example"></a>Esempio

Il codice seguente usa `_Analysis_assume` per correggere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Vedere anche

- [__assume](/cpp/intrinsics/assume)
