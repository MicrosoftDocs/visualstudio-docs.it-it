---
title: Editor standard
description: Uso dell'editor standard in Visual Studio per Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 8d2874b731bf0ad54b4a596034a23af8815fa502
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="source-editor"></a>Editor standard

Un editor standard affidabile è essenziale per scrivere codice in modo conciso ed efficiente. Visual Studio per Mac offre un editor standard sofisticato, centrale per le interazioni con l'ambiente di sviluppo integrato. L'editor standard offre funzionalità necessarie per lavorare in modo agevole: da funzioni di base, come ad esempio evidenziazione della sintassi, frammenti di codice e riduzione del codice, ai vantaggi derivanti dall'integrazione del compilatore Roslyn, ad esempio il completamento di codice completamente funzionale IntelliSense.

L'editor standard in Visual Studio per Mac consente un'esperienza ottimale di uso di tutte le altre funzionalità nell'IDE, ad esempio debug, refactoring e integrazione del controllo della versione.

Questo articolo presenta alcune delle funzionalità chiave dell'editor standard e illustra come è possibile usare Visual Studio per Mac nel modo più produttivo possibile.

## <a name="the-source-editor-experience"></a>Esperienza di uso dell'editor standard

L'efficienza di visualizzazione e di spostamento nel codice è una parte essenziale del flusso di lavoro di sviluppo. Il modo esatto in cui si desidera visualizzare e gestire il codice è una decisione personale che varia da uno sviluppatore all'altro e spesso anche tra un progetto e l'altro.

Visual Studio per Mac offre molte funzionalità potenti per rendere lo sviluppo multipiattaforma il più accessibile e utile possibile. Le sezioni seguenti descrivono alcune delle caratteristiche principali.


## <a name="code-folding"></a>Riduzione del codice

La riduzione del codice agevola la gestione di file di codice sorgente di grandi dimensioni consentendo agli sviluppatori di mostrare o nascondere intere sezioni di codice, ad esempio direttive, codice e commenti boilerplate e istruzioni #region. La riduzione del codice è disattivata per impostazione predefinita in Visual Studio per Mac

Per attivare la riduzione del codice, spostarsi su **Visual Studio > Preferenze... > Editor di testo > Generale > Riduzione del codice**:

![Opzioni di riduzione del codice](media/source-editor-image1.png)

Questo menu include anche l'opzione per ridurre #region e commenti per impostazione predefinita, visualizzando un hint denominato anziché il codice.

Per mostrare o nascondere sezioni, usare il widget di divulgazione accanto al numero di riga:

 ![Mostrare o nascondere sezioni nel codice](media/source-editor-image2.png)

È anche possibile selezionare alternativamente se visualizzare o nascondere le riduzioni, usando la voce di menu **Visualizza > Riduzione> Toggle Fold / Toggle All Folds (Attiva riduzione / Attiva/disattiva tutte le riduzioni)**:

 ![Voce di menu Riduzione](media/source-editor-image19.png)

Questa voce di menu può anche essere usata per abilitare o disabilitare la riduzione del codice.

## <a name="white-space"></a>Spazio vuoto

Può essere necessario visualizzare i caratteri invisibili nel codice sorgente. Questo è un modo per verificare visivamente che si stiano rispettando gli standard di codifica e che non si sprechi spazio. È anche utile quando si scrive in F#, dove la valutazione del codice dipende da righe con un rientro preciso.

Per impostare le opzioni per mostrare gli spazi vuoti, passare a **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli**. La selezione di questa opzione consente di impostare _quando_ visualizzare i caratteri invisibili: mai, alla selezione o sempre:

 ![Opzioni per mostrare i caratteri invisibili](media/source-editor-image3.png)

È anche disponibile l'opzione per mostrare tabulazioni, spazi e terminazioni riga:

 ![Mostrare tabulazioni e spazi](media/source-editor-image4.png)

 I caratteri invisibili vengono visualizzati come punti grigi, come illustrato nell'immagine seguente:

 ![spazi vuoti visualizzati](media/source-editor-image22.png)


## <a name="ruler"></a>Righello

Il righello per le colonne è utile per determinare le lunghezze delle righe, in particolare quando si lavora in un team che ha linee guida per tali lunghezze. Per attivare o disattivare il righello per le colonne, passare a **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli** e selezionare (o deselezionare) **Show Column ruler** (Mostra righello per le colonne), come illustrato nell'immagine seguente:

 ![](media/source-editor-image5.png)

 Verrà visualizzata una linea grigia verticale nell'editor standard.


## <a name="highlight-identifier-references"></a>Evidenzia riferimenti identificatore

Quando l'opzione "Highlight identifier references (Evidenzia riferimenti identificatore)" è attivata, è possibile selezionare qualsiasi simbolo nel codice sorgente e l'editor offrirà una guida visiva per tutti gli altri riferimenti in tale file. Per attivare questa opzione, passare a **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli** e selezionare _Highlight identifier references_ (Evidenzia riferimenti identificatore), come illustrato nell'immagine seguente:

![](media/source-editor-image6.png)

Anche il colore dell'evidenziazione è utile per indicare che qualcosa è assegnato o referenziato. Se qualcosa è assegnato, è evidenziato in rosso, se qualcosa è referenziato, è evidenziato in blu:

![](media/source-editor-image7.png)



