---
title: R Markdown
description: Come creare documenti R Markdown in Visual Studio per generare report, presentazioni e dashboard di alta qualità.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4e74966e71a7d440aed918e8aa609eeb8e68c355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851881"
---
# <a name="create-r-markdown-documents"></a>Creare documenti R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) è un formato di documento che trasforma l'analisi in R in documenti, report, presentazioni e dashboard di alta qualità.

R Tools per Visual Studio (RTVS) offre un modello di elemento R Markdown, il supporto dell'editor (tra cui IntelliSense per il codice R all'interno dell'editor), funzionalità di generazione di file e anteprima dinamica.

## <a name="using-r-markdown"></a>Uso di R Markdown

1. Chiudere Visual Studio.
1. (Una sola volta) Installare `pandoc` da [pandoc.org](https://pandoc.org/installing.html).
1. Riavviare Visual Studio, che deve rilevare l'installazione di pandoc.
1. Installare i pacchetti `knitr` e `rmarkdown`. È possibile eseguire questa operazione dalla [finestra interattiva](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Creare un nuovo file di R markdown usando il comando di menu **file**  >  **nuovo**  >  **file** e selezionando **R**  >  **R markdown** dall'elenco. Nel contesto di un progetto fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Aggiungi R Markdown** oppure scegliere **Aggiungi** > **Nuovo elemento** e selezionare **R Markdown** nell'elenco.

1. Il contenuto predefinito del nuovo file è il seguente:

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>Anteprime

Visual Studio 2017 versione 15.5 e versioni successive forniscono automaticamente l'anteprima dinamica per R Markdown. Per attivare la sincronizzazione automatica tra l'editor e l'anteprima, selezionare **R Tools**  >  **Markdown**  >  **Automatic Sync** (**CTRL** + **MAIUSC** + **Y**). Se non si usa la sincronizzazione automatica, è possibile aggiornare l'anteprima usando **R Tools**  >  **Markdown**  >  **reload R markdown Preview**.

È anche possibile visualizzare in anteprima il file in formato HTML, PDF e Microsoft Word. A tale scopo, fare clic con il pulsante destro del mouse nell'editor e scegliere uno dei comandi **Anteprima**. Gli stessi comandi sono disponibili anche nel menu **R Tools**  >  **Markdown** . (Nelle versioni precedenti di Visual Studio questi comandi sono disponibili in **R Tools**  >  Menu **pubblica** .)

![Anteprima dinamica di R Markdown e altri comandi di menu Anteprima](media/rmarkdown-live-preview.png)
