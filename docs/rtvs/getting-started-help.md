---
title: Finestra della Guida per R
description: La Guida di R è integrata direttamente nella finestra interattiva in Visual Studio tramite il comando .
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 551f929e4d42b208dd222f052b27720edb273761
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885768"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Guida di R Tools per Visual Studio

La Guida di R è integrata direttamente nella finestra interattiva in Visual Studio. Quando si usa il comando `?`, ad esempio `?mtcars`, viene visualizzata la Guida dalla documentazione di R in una finestra di Visual Studio:

![Finestra della Guida in Visual Studio](media/help-window.png)

> [!Tip]
> La finestra della Guida, come tutte le finestre di Visual Studio, può essere disposta e ancorata a seconda delle proprie preferenze. Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Per aprire i risultati della Guida in un browser, selezionare il menu opzioni di **R Tools**  >   e impostare la proprietà **Guida di R browser** su `External` . Vedere [R Tools for Visual Studio options](options-for-r-tools-in-visual-studio.md) (Opzioni di R Tools per Visual Studio).

Per eseguire ricerche nella Guida, usare il comando `??` seguito dal termine di ricerca. Se il termine di ricerca contiene spazi, usare le virgolette:

```R
??"Motor Trend"
```

![Risultati della ricerca nella Guida](media/help-search1.png)

La finestra della Guida ha anche un campo di immissione per la ricerca tramite il quale è possibile eseguire altre ricerche direttamente nella documentazione di R:

![Risultati della ricerca nella Guida tramite il campo di immissione](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Ricerca nella Guida integrata

Gli sviluppatori spesso cercano nella documentazione di R informazioni sui nomi di funzione, i set di dati e altri elementi. R Tools per Visual Studio (RTVS) semplifica il processo grazie all'integrazione delle ricerche nella Guida direttamente nell'editor e nelle finestre interattive.

- La pressione di **F1** durante un'operazione di completamento automatico genera un elenco di risultati della Guida corrispondenti alla sottostringa.
- Fare clic con il pulsante destro del mouse su un termine di ricerca, ad esempio una funzione, e selezionare il comando **Help on** (Guida su) per aprire la Guida per tale funzione. È anche possibile richiamare **Help on** (Guida su) per qualsiasi selezione.

    ![Richiamare la Guida mediante il menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse](media/help-right-click.png)

> [!Tip]
> Per aprire la guida integrata in un browser, selezionare **R Tools**  >  **options** e impostare il **Web browser F1** su `External` . Vedere [R Tools for Visual Studio options](options-for-r-tools-in-visual-studio.md) (Opzioni di R Tools per Visual Studio).

## <a name="integrated-stackoverflow-search"></a>Ricerca di StackOverflow integrata

Oltre a eseguire ricerche nella documentazione di R, gli sviluppatori spesso cercano anche in StackOverflow durante la scrittura del codice. RTVS semplifica anche tale processo. Fare clic con il pulsante destro del mouse su un termine o una selezione, selezionare il comando **Cerca nel Web** (**CTRL**+**F1**). Visual Studio apre una finestra con i risultati della ricerca nell'ambito di StackOverflow:

![Risultati della ricerca nel Web in Visual Studio](media/help-web-search-results.png)

È possibile modificare la stringa di ambito accodata, `R site:stackoverflow` , tramite l'opzione **R Tools**  >  **Opzioni** della  >  **stringa di ricerca Web F1** :

![Modifica dell'opzione Stringa di ricerca sul Web F1](media/options-dialog.png)

Se si preferisce visualizzare i risultati in un browser, modificare l'opzione **Web browser F1** come descritto in [Opzioni](options-for-r-tools-in-visual-studio.md).