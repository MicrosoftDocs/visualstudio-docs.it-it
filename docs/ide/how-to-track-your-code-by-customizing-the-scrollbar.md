---
title: 'Procedura: Tenere traccia del codice personalizzando la barra di scorrimento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f56e834e6c2b80706e4ed1d1a91583e1015791b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Procedura: Tenere traccia del codice personalizzando la barra di scorrimento

Quando si usano file di codice lunghi, può risultare difficile tenere presente tutto il contenuto. È possibile personalizzare la barra di scorrimento della finestra del codice per ottenere una panoramica del contenuto del codice.

## <a name="to-show-annotations-on-the-scroll-bar"></a>Per mostrare le annotazioni sulla barra di scorrimento

1. È possibile configurare la barra di scorrimento in modo da visualizzare le modifiche al codice, i punti di interruzione, gli errori e i segnalibri.

    Aprire la pagina Opzioni **Barra di scorrimento** scegliendo **Strumenti** > **Opzioni** > **Editor di testo** > **Tutti i linguaggi** o un linguaggio specifico, oppure digitando **barra di scorrimento** nella finestra Avvio veloce.

2. Selezionare **Mostra annotazioni su barra di scorrimento verticale** e quindi selezionare le annotazioni da visualizzare.

    L'opzione **Contrassegni** include punti di interruzione e segnalibri.

3. Provare ora a eseguire l'operazione. Aprire un file di codice di grandi dimensioni e sostituire un elemento presente in diversi punti nel file. La barra di scorrimento mostra l'effetto delle sostituzioni, pertanto è possibile annullare le modifiche se è stato sostituito qualche elemento che non doveva essere sostituito.

    Ecco l'aspetto della barra di scorrimento dopo la ricerca di una stringa. Si noti che vengono visualizzate tutte le istanze della stringa.

    ![Barra di scorrimento dopo la ricerca di una stringa.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

    Ecco la barra di scorrimento dopo la sostituzione di tutte le istanze della stringa. È possibile vedere immediatamente che l'operazione ha provocato alcuni problemi.

    ![Barra di scorrimento dopo la sostituzione di una stringa con errori](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

## <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Per impostare la modalità di visualizzazione per la barra di scorrimento

1. La barra di scorrimento ha due modalità: modalità barra (impostazione predefinita) e modalità mappa. La modalità barra consente di visualizzare solo gli indicatori delle annotazioni sulla barra di scorrimento. In modalità mappa sulla barra di scorrimento sono rappresentate le righe di codice. È possibile scegliere la larghezza delle righe e se visualizzare o meno il codice sottostante quando si posiziona il puntatore su di esse. Quando si fa clic su una posizione sulla barra di scorrimento, il cursore si sposta in tale posizione nel codice. Le aree compresse hanno un'ombreggiatura diversa e vengono espanse quando si fa doppio clic su di esse.

    Nella pagina delle opzioni **Barra di scorrimento** selezionare **Usa modalità barra per barra di scorrimento verticale** o **Usa modalità mappa per barra di scorrimento verticale**. È possibile scegliere la larghezza nell'elenco a discesa **Panoramica origine**.

    Ecco come appare l'esempio di ricerca quando è attivata la modalità mappa e la larghezza viene impostata su Media:

    ![Barra di scorrimento in modalità mappa](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. In modalità mappa per abilitare le anteprime del codice quando si sposta il cursore verso l'alto e il basso nella barra di scorrimento, selezionare l'opzione **Mostra descrizione comando anteprima**. L'aspetto è il seguente:

    ![Barra di scorrimento con una descrizione comando](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

    Se si vogliono mantenere il comportamento di scorrimento della modalità mappa e la descrizione comando anteprima ma non si vuole visualizzare la panoramica del codice sorgente, è possibile impostare **Panoramica origine** su **Off**.

## <a name="see-also"></a>Vedere anche

[Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)