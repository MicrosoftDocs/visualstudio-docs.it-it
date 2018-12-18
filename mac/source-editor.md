---
title: Editor standard | Microsoft Docs
description: Uso dell'editor standard in Visual Studio per Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: f52e60c0ade8cebc78b3408b4ef81ef85fcd767b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="source-editor"></a>Editor standard

Un editor standard affidabile è essenziale per scrivere codice in modo conciso ed efficiente. Visual Studio per Mac offre un editor standard sofisticato, centrale per le interazioni con l'ambiente di sviluppo integrato. L'editor standard offre funzionalità necessarie per lavorare in modo agevole: da funzioni di base, come ad esempio evidenziazione della sintassi, frammenti di codice e riduzione del codice, ai vantaggi derivanti dall'integrazione del compilatore Roslyn, ad esempio il completamento di codice completamente funzionale IntelliSense.

L'editor standard in Visual Studio per Mac consente un'esperienza ottimale di uso di tutte le altre funzionalità offerte dall'ambiente di sviluppo integrato, ad esempio debug, refactoring e integrazione del controllo della versione.

Questo argomento presenta alcune delle funzionalità chiave dell'editor standard e illustra come è possibile usare Visual Studio per Mac nel modo più produttivo possibile.

## <a name="the-source-editor-experience"></a>Esperienza di uso dell'editor standard

L'efficienza di visualizzazione e di spostamento nel codice è una parte essenziale del flusso di lavoro di sviluppo. Il modo esatto in cui si desidera visualizzare e gestire il codice è una decisione personale che varia da uno sviluppatore all'altro e spesso anche tra un progetto e l'altro.

Visual Studio per Mac offre molte funzionalità potenti per rendere lo sviluppo multipiattaforma il più accessibile e utile possibile. Le sezioni seguenti descrivono alcune delle caratteristiche principali.


### <a name="code-folding"></a>Riduzione del codice

La riduzione del codice agevola la gestione di file di codice sorgente di grandi dimensioni consentendo agli sviluppatori di mostrare o nascondere intere sezioni di codice, ad esempio direttive, codice e commenti boilerplate e istruzioni #region. Questa funzionalità è disattivata per impostazione predefinita in Visual Studio per Mac

Per attivare la riduzione del codice, spostarsi su **Visual Studio > Preferenze... > Editor di testo > Generale > Riduzione del codice**:

![Opzioni di riduzione del codice](media/source-editor-image1.png)

Oltre a offrire l'opzione per abilitare la riduzione del codice, questo menu include anche l'opzione per ridurre #region e commenti per impostazione predefinita, visualizzando un hint denominato anziché il codice.

Per mostrare o nascondere sezioni, usare il widget di divulgazione accanto al numero di riga:

 ![Mostrare o nascondere sezioni nel codice](media/source-editor-image2.png)

È anche possibile selezionare alternativamente se visualizzare o nascondere le riduzioni, usando la voce di menu **Visualizza > Riduzione> Toggle Fold / Toggle All Folds (Attiva riduzione / Attiva/disattiva tutte le riduzioni)**:

 ![Voce di menu Riduzione](media/source-editor-image19.png)

Questa voce di menu può anche essere usata per abilitare o disabilitare la riduzione del codice.

### <a name="white-space"></a>Spazio vuoto

Può essere necessario poter visualizzare i caratteri invisibili nel codice sorgente. Questo è un modo per verificare visivamente che si stiano rispettando gli standard di codifica e che non si sprechi spazio. È anche molto utile quando si scrive in F#, dove la valutazione del codice dipende da righe con un rientro preciso.

Impostare opzioni per mostrare spazi vuoti spostandosi su **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli**, come illustrato di seguito. La selezione di questa opzione consente di impostare _quando_ visualizzare i caratteri invisibili: mai, alla selezione o sempre:

 ![Opzioni per mostrare i caratteri invisibili](media/source-editor-image3.png)

È anche disponibile l'opzione per mostrare tabulazioni, spazi e terminazioni riga:

 ![Mostrare tabulazioni e spazi](media/source-editor-image4.png)

 I caratteri invisibili vengono visualizzati come punti grigi, come illustrato di seguito:

 ![spazi vuoti visualizzati](media/source-editor-image22.png)


### <a name="ruler"></a>Righello

La visualizzazione del righello di colonna è utile per determinare le lunghezze delle righe, in particolare quando si lavoro in un team che ha linee guida per tali lunghezze. Il righello di colonna può essere attivato o disattivato spostandosi su **Visual Studio > Preferenze... > Editor di testo > Marcatori e righelli** e selezionando (o selezionando) **Show Column ruler (Mostra righello di colonna)**, come illustrato di seguito:

 ![](media/source-editor-image5.png)

 Verrà visualizzata una linea grigia verticale nell'editor standard.


### <a name="highlight-identifier-references"></a>Evidenzia riferimenti identificatore

Quando questa opzione è attivata, uno sviluppatore può posizionare il mouse su qualsiasi simbolo nel codice sorgente e l'editor standard offrirà una guida visiva per tutti gli altri riferimenti in tale file. Per attivare questa funzionalità, spostarsi su **Visual Studio > Preferenze... > Editor di testo > Marcatori e righelli** e selezionare _Highlight identifier references (Evidenzia riferimenti identificatore)_, come illustrato di seguito:

![](media/source-editor-image6.png)

Anche il colore dell'evidenziazione è utile per indicare che qualcosa è assegnato o referenziato. Se qualcosa è assegnato, è evidenziato in rosso, se qualcosa è referenziato, è evidenziato in blu:

![](media/source-editor-image7.png)



