---
title: Lint del codice con R Tools per Visual Studio | Microsoft Docs
description: Come utilizzare il supporto di lint predefinito per R di Visual Studio, incluse le opzioni di lint.
ms.custom: 
ms.date: 01/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 30f508fbaa6de816f8b0adb336fea66b82f992a6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Lint del codice R in Visual Studio

Il termine lint indica un processo che analizza il codice per individuare potenziali errori, problemi di formattazione e altri elementi superflui nel codice, come spazi vuoti spuri. Il processo di lint favorisce anche il rispetto di determinate convenzioni per la scrittura del codice, ad esempio la denominazione degli identificatori, molto utili all'interno di team o in altre situazioni di sviluppo in collaborazione.

R Tools for Visual Studio (RTVS) offre funzionalità di lint incorporate per R, con un comportamento controllabile tramite un'ampia gamma di opzioni descritte in questo articolo. Queste opzioni sono disponibili in **Strumenti > Opzioni > Editor di testo > R > Lint**.

Il lint è disabilitato per impostazione predefinita. Per abilitare il lint, impostare l'opzione **Tutto > Abilita lint** su true.

Dopo l'abilitazione, il lint viene applicato nell'editor durante la digitazione. I problemi vengono segnalati tramite sottolineature ondulate verdi. Nella figura seguente, ad esempio, RTVS ha identificato sei problemi di lint, tra i quali l'uso di `=` invece di `<-` per un'assegnazione, la mancanza di spazio attorno agli argomenti della funzione, l'uso di identificatori con la notazione Pascal e con tutte maiuscole e l'uso di un punto e virgola. Posizionando il puntatore del mouse su un problema viene visualizzata una descrizione.

![Esempi di lint per il codice R](media/linting-01.png)

È spesso necessario modificare le opzioni di lint a seconda delle esigenze di un progetto o un file. Ad esempio, il codice di esempio da un corso online potrebbe usare `=` invece di `<-` insieme agli identificatori con convenzione per le maiuscole/minuscole Pascal. Per questo codice verrebbero visualizzati avvisi di lint frequenti, perché le opzioni di lint predefinite contrassegnano questa convenzione per le maiuscole/minuscole. Durante l'utilizzo di tale codice è quindi possibile semplicemente disabilitare le opzioni anziché dedicare a tempo a correggere ogni istanza.

## <a name="assignment-group"></a>Gruppo Assegnazione

| Opzione | Valore predefinito | Effetto del lint |
| --- | --- | --- |
| Imponi \<- | `True` | Identifica quando `<-` non viene usato per un'assegnazione. |

## <a name="naming-group"></a>Gruppo Denominazione

Queste opzioni consentono di contrassegnare gli identificatori che usano convenzioni di denominazione diverse:

| Opzione | Valore predefinito | Effetto del lint |
| --- | --- | --- |
| Contrassegna camelCase | `False` | Contrassegna gli identificatori che usano la notazione Camel. |
| Contrassegna nomi lunghi | `False` | Contrassegna gli identificatori con un nome con una lunghezza superiore all'impostazione "Lunghezza massima del nome". |
| Contrassegna più punti | `True` | Contrassegna gli identificatori che usano più punti. |
| Contrassegna PascalCase | `True` | Contrassegna gli identificatori che usano la notazione Pascal. |
| Contrassegna snake_case | `False` | Contrassegna gli identificatori che usano caratteri di sottolineatura. |
| Contrassegna MAIUSCOLE | `True` | Contrassegna gli identificatori che usano tutte maiuscole. |
| Lunghezza massima del nome | 32 | La lunghezza applicata con l'impostazione "Contrassegna nomi lunghi". |

## <a name="spacing-group"></a>Gruppo Spaziatura

Queste opzioni, impostate tutte su `True` per impostazione predefinita, determinano la posizione in cui il linter identifica i problemi di spaziatura: dopo i nomi di funzione, tra le virgole, tra gli operatori, le posizioni delle parentesi graffe aperte e chiuse, lo spazio prima di ( e lo spazio all'interno di ().

## <a name="statements-group"></a>Gruppo Istruzioni

| Opzione | Valore predefinito | Effetto del lint |
| --- | --- | --- |
| Selezione multipla | `True` | Identifica se più istruzioni sono sulla stessa riga. |
| Punti e virgola | `True` | Identifica l'uso di punti e virgola. |

## <a name="text-group"></a>Gruppo Testo

| Opzione | Valore predefinito | Effetto del lint |
| --- | --- | --- |
| Limite di lunghezza della riga | `False` | Specifica se il linter deve contrassegnare le righe con una lunghezza maggiore di quella specificata dall'opzione "Lunghezza massima della riga". |
| Lunghezza massima della riga | 80 | Imposta la lunghezza di riga applicata dall'opzione "Limite di lunghezza della riga". |

## <a name="whitespace-group"></a>Gruppo Spazio vuoto

Queste opzioni, impostate tutte su `True` per impostazione predefinita, determinano la posizione in cui il linter identifica i problemi di spazio vuoto: uso delle schede, uso di virgolette doppie, righe vuote finali e spazi vuoti finali.