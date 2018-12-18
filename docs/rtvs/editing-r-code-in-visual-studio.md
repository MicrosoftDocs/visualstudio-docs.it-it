---
title: Modifica del codice con R Tools per Visual Studio | Microsoft Docs
description: "Visual Studio offre un'esperienza di modifica su misura per R, pur mantenendo tutte le funzionalità e la possibilità di usare le estensioni."
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
ms.openlocfilehash: b318122163bf74035d19fd53c7da4be938b345f5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="editing-r-code-in-visual-studio"></a>Modifica del codice R in Visual Studio

R Tools per Visual Studio (RTVS) consente di adattare l'esperienza di modifica di Visual Studio in modo specifico per R, mantenendo tutte le funzionalità e la possibilità di usare le estensioni. Se si preferiscono i tasti di scelta rapida VIM, è ad esempio possibile installare l'[estensione VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) gratuita da Visual Studio Gallery.

Oltre alle funzionalità in questo articolo, vedere anche [IntelliSense](r-intellisense.md), [lint](linting-r-code.md), [frammenti di codice](code-snippets-for-r.md) e [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Evidenziazione della sintassi

Oltre ad applicare un colore alle diverse parti del codice, ad esempio stringhe, commenti e parole chiave, RTVS evidenzia e abilita anche i collegamenti nei commenti:

![Colorazione della sintassi per il codice R](media/editing-syntax-colors.png)

Per personalizzare i tipi di carattere e alcuni colori di evidenziazione, selezionare il comando **Strumenti > Opzioni**, passare ad **Ambiente > Tipi di carattere e colori** e modificare le impostazioni per gli elementi correlati a R nella casella **Elementi visualizzati:**:

![Tipi di carattere e opzioni di colore per il codice R](media/editing-syntax-colors-options.png)

Visual Studio sottolinea anche gli errori di sintassi nell'editor:

![Evidenziazione degli errori di sintassi nel codice R](media/editing-syntax-error.png)

Per modificare questo comportamento, vedere l'impostazione **Avanzate > Controllo della sintassi** nelle [opzioni dell'editor](#editor-options).

## <a name="editing-and-organizing-code"></a>Modifica e organizzazione del codice

Durante la digitazione del codice, RTVS offre il completamento automatico come descritto nella pagina su [IntelliSense](r-intellisense.md). Esegue anche la formattazione automatica, completando ad esempio il codice con graffe e parentesi: 

![Animazione della formattazione inline](media/editing-inline-formatting.gif)

Durante la digitazione di chiamate a funzioni con molti parametri, è spesso utile poter allineare i parametri per rendere il codice più leggibile. RTVS ricorda il rientro impostato per i parametri e lo applica automaticamente alle righe successive:

![Animazione del rientro automatico](media/editing-auto-indentation.gif)

Per modificare questo comportamento, vedere le [opzioni dell'editor](#editor-options) per il gruppo **Tabulazioni**.

Le aree di codice comprimibili consentono di nascondere temporaneamente parte del codice nell'editor. Visual Studio crea automaticamente diverse aree in caso di istruzioni su più righe, a meno che l'opzione **Avanzate > Struttura > Struttura del codice**  sia disattivata.

Per creare un'area personalizzata, racchiudere il codice interessato con commenti che terminano con `---`. Il piccolo controllo + /- a sinistra del codice consente di espandere e comprimere le aree:

![Creazione di un'area comprimibile con commenti](media/editing-collapsible-regions.gif)

Per impostazione predefinita, Visual Studio inserisce gli spazi quando si preme TAB. Anche in questo caso è possibile modificare tale comportamento, seguendo le istruzioni descritte in [Opzioni, Editor di testo, Tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Esplorazione del codice

Grazie all'esplorazione del codice è possibile accedere rapidamente al codice sorgente del programma R e alle sue librerie. Queste funzionalità consentono di restare nel flusso di lavoro senza dover eseguire manualmente ricerche nel codice.

**Vai a definizione** consente di passare rapidamente a una definizione di funzione o di visualizzare un editor inline ridotto per leggere il codice sorgente di una funzione di libreria. Fare clic con il tasto destro del mouse sulla funzione interessata e selezionare **Vai a definizione** oppure posizionare il cursore nella funzione e premere F12.

Questo comando apre una nuova finestra dell'editor contenente il codice sorgente per la funzione. Per praticità, il cursore viene posizionato all'inizio della definizione della funzione.

**Visualizza definizione**, se richiamata dal menu di scelta rapida o con ALT+F12, inserisce un'area scorrevole di sola lettura contenente il codice sorgente della funzione sotto la chiamata di funzione:

![Animazione per Visualizza definizione](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Invio di codice alla finestra interattiva

Molti sviluppatori preferiscono scrivere il codice nell'editor e inviarlo alla [finestra interattiva](interactive-repl-for-r-in-visual-studio.md) per eseguire immediatamente il test, noto anche come ciclo Read–Eval–Print o REPL. Premendo CTRL+INVIO nell'editor di R, la riga di codice corrente viene inviata alla finestra interattiva e il cursore passa poi alla riga successiva. Con CTRL+INVIO è quindi possibile esplorare il codice dall'editor.

È anche possibile selezionare il codice e premere CTRL+INVIO per applicare tale comportamento all'intera selezione. In alternativa, fare clic con il pulsante destro del mouse sul codice selezionato e scegliere **Esegui in interattivo**.

## <a name="formatting-code"></a>Formattazione del codice

La formattazione automatica di Visual Studio consente di usare la formattazione definita nelle preferenze per il codice che si sta scrivendo e per il codice incollato nell'editor. È anche possibile selezionare il codice, fare clic con il pulsante destro del mouse sul codice selezionato e scegliere **Formatta selezione** (CTRL+K,F) per applicare tali preferenze. Ad esempio, se la definizione di funzione era interamente su una singola riga:

```R
f<-function  (a){  return(a + 1) }
```

Applicando la formattazione, il codice viene pulito:

```R
f <- function(a) { return(a + 1) }
```

Per modificare la formattazione dell'intero file, selezionare **Modifica > Avanzate > Formatta documento** (CTRL+E,D).

La formattazione automatica è un'operazione distinta che può essere annullata. Ad esempio, se si incolla il codice nell'editor e si applica la formattazione, selezionando **Modifica > Annulla** o premendo CTRL+Z una volta, la formattazione viene annullata. Selezionando di nuovo Annulla, viene invertita l'operazione d'incollamento.

Le opzioni di formattazione, inclusa la disattivazione della formattazione, vengono impostate usando **Strumenti > Opzioni** nella scheda **Editor di testo > R > Avanzate**. È possibile passare direttamente a questa pagina usando il comando **R Tools > Opzioni editor** o facendo clic nell'editor e selezionando **Opzioni di formattazione**. Vedere la sezione relativa alle [opzioni dell'editor](#editor-options) per informazioni dettagliate.

## <a name="inserting-roxygen-comments"></a>Inserimento di commenti Roxygen

RTVS offre un collegamento per la generazione di commenti [Roxygen](http://roxygen.org/) che usa i nomi dei parametri di una funzione. È sufficiente digitare `###` in una riga vuota sopra la definizione della funzione:

![Animazione dell'inserimento di un commento Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opzioni dell'editor

Le opzioni specifiche dell'editor vengono impostate tramite il comando **Strumenti > Opzioni**, passando a **Editor di testo > R**, oppure usando il comando di scelta rapida **R Tools > Opzioni editor...** .

Le opzioni contenute nelle schede **Generale**, **Barre di scorrimento** e **Tabulazioni** non sono specifiche di R, ma piuttosto sono impostazioni generali di Visual Studio disponibili per tutti i linguaggi, ma che vengono applicate a seconda del linguaggio. Per informazioni dettagliate, vedere gli articoli seguenti:

- [Opzioni, Editor di testo, Tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md)
- [Procedura: Tenere traccia del codice personalizzando la barra di scorrimento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opzioni, Editor di testo, Tutti i linguaggi, Tabulazioni](../ide/reference/options-text-editor-all-languages-tabs.md)

Le opzioni nella scheda **R > Avanzate** sono specifiche di RTVS:

| Gruppo | Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- | --- |
| Formattazione | Formattazione automatica | Attivato | Riformatta il codice durante la digitazione. Non condiziona i comandi **Formatta selezione** o **Formatta documento**. |
| | Parentesi graffe espanse | Disattivato | Inserisce una { aperta in una nuova riga. |
| | Formatta dopo Incolla | Attivato | Applica la formattazione dopo aver incollato. |
| | Formatta ambito dopo } | Attivato | Formatta l'ambito dopo aver digitato una } chiusa. |
| | Spazio dopo la virgola | Attivato | Inserisce uno spazio dopo le virgole. |
| | Spazio dopo parola chiave | Attivato | Inserisce uno spazio dopo parole chiave come `if`, `while` e `repeat`. |
| | Spazio prima di { | Attivato | Inserisce uno spazio prima di una { aperta. |
| | Spazio prima e dopo = | Attivato | Inserisce spazi prima e dopo un segno di uguale. |
| IntelliSense | Esegui il commit quando si preme INVIO | Disattivato | Esegue il commit di selezione di completamento automatico quando si preme INVIO. |
| | Esegui il commit quando si preme la BARRA SPAZIATRICE | Disattivato | Esegue il commit di selezione di completamento automatico quando si preme la BARRA SPAZIATRICE.|
| | Elenco di completamento dopo la digitazione del primo carattere | Attivato | Visualizza l'elenco di completamento dopo aver digitato i primi caratteri. Se l'opzione è disattivata, viene visualizzato un elenco di completamento selezionando **Modifica > IntelliSense > Elenca membri** (CTRL+J). |
| | Elenco di completamento con il tasto TAB | Disattivato | Richiama l'elenco di completamento digitando uno o più caratteri e premendo TAB. |
| | Corrispondenza con nomi di argomento parzialmente digitati | Disattivato | Durante la digitazione dei nomi di un argomento in una chiamata di funzione, la firma visualizza una descrizione che meglio corrisponde all'argomento. |
| Finestra interattiva | Controllo della sintassi nella console R | Disattivato | Applica il controllo della sintassi nella finestra interattiva. Il controllo della sintassi non funziona correttamente se viene applicato a istruzioni su più righe. | 
| struttura | Struttura del codice | Attivato | Crea automaticamente aree comprimibili in caso di istruzioni su più righe. |
| Controllo della sintassi | Mostra errori di sintassi | Attivato | Abilita il controllo automatico della sintassi del codice. |
