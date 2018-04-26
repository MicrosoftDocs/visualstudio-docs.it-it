---
title: Utilizzo di sequenze di escape in modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b8e92a4bbd149d96b6db710daf32dc72024d57da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilizzo di sequenze di escape in modelli di testo
Nei modelli di testo per generare il tag di modello di testo e (nel codice c# solo), è possibile utilizzare le sequenze di escape di caratteri di escape di controllo e tra virgolette.

 Per stampare i tag di apertura e chiusura di un blocco di codice standard per il file di output, escape i tag come indicato di seguito:

```
\<# ... \#>
```

 È possibile eseguire la stessa con gli altri tag blocco direttiva e il codice del modello di testo.

 Se un blocco di testo include stringhe utilizzate per eseguire l'escape di tag di modello di testo, è possibile utilizzare le sequenze di escape seguenti:

-   Se un tag di modello di testo è preceduto da un numero pari di escape (\\) il modello di caratteri parser verrà metà dei caratteri di escape e includere la sequenza come un tag di modello di testo. Ad esempio, se sono presenti quattro caratteri di escape nel modello di testo, verrà due "\\" caratteri nel file generato.

-   Se il tag di modello di testo è preceduto da un numero dispari di escape (\\) caratteri, il parser del modello includerà metà del "\\" caratteri più il tag stesso (\<# o #>). Il tag non viene considerato come un tag di modello di testo.

-   Se un carattere di escape (\\) carattere viene visualizzato altrove in qualsiasi sequenza diverso da in cui viene eseguito l'escape un carattere di controllo o una virgoletta (solo in c#), verrà restituito il carattere direttamente.

## <a name="see-also"></a>Vedere anche

- [Procedura: Generare modelli da modelli usando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)