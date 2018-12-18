---
title: Esplora variabili in R Tools per Visual Studio | Microsoft Docs
description: Esplora variabili in Visual Studio mostra tutte le variabili con un ambito specifico nella sessione corrente di R.
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 41dab5fa99f4f725ef3aadc76b2b2441cb2c4abb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="variable-explorer"></a>Esplora variabili

La finestra **Esplora variabili**, che è possibile aprire tramite **R Tools > Finestre > Esplora variabili** (o CTRL+8 se si usa **R Tools > Impostazioni di Data Science**), mostra tutte le variabili di un ambito specifico nella sessione di R corrente. Se, ad esempio, dopo aver aperto Esplora variabili si immettono le righe seguenti nella [finestra interattiva](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

La finestra Esplora variabili viene visualizzata come segue:

![Finestra Esplora variabili in Visual Studio](media/variable-explorer-window.png)

Se nella sessione è stato definito un dataframe R più complesso, è possibile spostarsi all'interno dei dati. Dopo aver eseguito `cars <- mtcars` è possibile spostarsi all'interno del set di dati espandendo i diversi nodi in Esplora variabili:

![Visualizzazione espansa di Esplora variabili](media/variable-explorer-expanded-results.png)

Per eliminare variabili, fare clic con il pulsante destro del mouse e selezionare **Elimina** oppure selezionare la variabile da eliminare e premere Canc.

È anche possibile cercare un'osservazione in un dataframe tramite la ricerca incrementale. Prima espandere i nodi del dataframe in cui si vuole eseguire la ricerca e quindi immettere i termini di ricerca nella relativa casella.

## <a name="details-table-view"></a>Vista (tabella) dei dettagli

Poiché i dati sono spesso tabulari, è possibile visualizzare qualsiasi tipo di dati complesso come tabella separata selezionando l'icona della lente di ingrandimento oppure facendo clic con il pulsante destro del mouse e selezionando **Mostra dettagli**.

![Vista tabella di Esplora variabili](media/variable-explorer-table-view.png)

Se si fa clic sull'intestazione di una colonna, i dati vengono ordinati in base a tale colonna, alternatamente in ordine crescente e decrescente. Se si fa clic su altre colonne tenendo premuto MAIUSC, anche queste colonne vengono prese in considerazione per l'ordinamento. Se si fa clic su una colonna senza tenere premuto MAIUSC si torna all'ordinamento in base a una sola colonna.

La sequenza in cui si fa clic sulle intestazioni di colonna determina l'ordine in cui viene eseguito l'ordinamento. Se ad esempio tenendo premuto MAIUSC si fa clic sulla colonna **cyl** e quindi due volte su **mpg**, l'elenco viene ordinato per cilindri in ordine crescente e per miglia per gallone in ordine decrescente:

![Vista tabulare dell'ordinamento dei dati in base a due colonne.](media/variable-explorer-table-view-sorting.png)

Dato che Esplora variabili e le viste delle tabelle si trovano in finestre di Visual Studio separate, è possibile disporle nel modo voluto per usarle affiancate. Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) per istruzioni generali.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Visualizzare le variabili in Excel o in un'altra applicazione in grado di supportare file CSV

Per effettuare ulteriori modifiche e analisi, è spesso utile esportare le variabili di sessione in formato CSV. L'esportazione viene eseguita con l'icona di Excel di piccole dimensioni (![icona di esportazione in Excel](media/variable-explorer-excel-icon.png)) accanto a ogni nodo in Esplora variabili o facendo clic con il pulsante destro del mouse su un elemento e selezionando **Apri in app CSV**. Se si seleziona l'icona i dati vengono scritti in un nuovo file CSV nella cartella `%userprofile%\Documents\RTVS_CSV_Exports` e il file verrà aperto nell'applicazione associata all'estensione `.csv`.

## <a name="scopes"></a>Ambiti

Per impostazione predefinita, all'apertura l'ambito di Esplora variabili è l'ambito globale. È possibile passare all'ambito di un pacchetto selezionando il pacchetto dall'elenco a discesa nella parte superiore della finestra.

![Esplora variabile con l'ambito di un pacchetto](media/variable-explorer-package-scopes.png)

È anche possibile passare all'ambito di una funzione in caso di arresto in corrispondenza di un punto di interruzione nel debugger. Si noti che Esplora variabili non passa automaticamente all'ambito della funzione del codice in fase di debug:

![Esplora variabili con un dataframe durante il debug](media/variable-explorer-as-locals-window.png)

Esplora variabili modifica automaticamente l'ambito di funzione man mano che scorre il codice nel debugger, ad esempio mostrando le variabili locali di una funzione.

## <a name="importing-data-into-variable-explorer"></a>Importazione di dati in Esplora variabili

Due comandi sulla barra degli strumenti di Esplora variabili, disponibili anche nel menu **R Tools > Dati**, consentono di importare set di dati CSV esterni nella sessione di R: **Importa set di dati in una sessione di R da un URL Web** e **Importa set di dati in una sessione di R da un file di testo**. 

Dopo avere identificato il file CSV da importare, Visual Studio visualizza la finestra di dialogo **Importa set di dati**, in cui sono disponibili opzioni per controllare la modalità di analisi del file di dati, ovvero per definire il separatore di campo e stabilire come gestire le virgolette. È anche possibile visualizzare un'anteprima del dataframe importato e del file di dati originale:

![Finestra di dialogo Importa set di dati](media/variable-explorer-import-dataset-dialog.png)
