---
title: Uso dell'editor del codice in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5847c97f3fddea65b00c35a5a0f4d5665329ae7e
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="write-code-in-the-code-editor"></a>Scrivere codice nell'editor del codice

L'editor di Visual Studio include diverse funzionalità che semplificano la scrittura e la gestione di codice e testo. È possibile espandere e comprimere diversi blocchi di codice usando la struttura. Per altre informazioni sul codice, usare IntelliSense, **Visualizzatore oggetti** e Gerarchia di chiamata. Per trovare il codice, è possibile usare funzionalità quali **Vai a**, **Vai a definizione** e **Trova tutti i riferimenti**. È possibile inserire i blocchi di codice con i frammenti di codice e generare il codice usando funzionalità come **Generazione dall'utilizzo**. Se non si è mai usato l'editor di Visual Studio, vedere [Modifica del codice](https://www.visualstudio.com/features/ide-vs) per una rapida panoramica.

 Il codice può essere visualizzato in diversi modi. Per impostazione predefinita, **Esplora soluzioni** visualizza il codice organizzato in base ai file. È possibile fare clic sulla scheda **Visualizzazione classi** nella parte inferiore della finestra per visualizzare il codice organizzato in base alle classi.

 È possibile cercare e sostituire il testo in singoli file o più file. Per altre informazioni, vedere [Finding and Replacing Text](../ide/finding-and-replacing-text.md). È possibile usare espressioni regolari per la ricerca e la sostituzione di testo. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 I diversi linguaggi di Visual Studio offrono set di funzionalità diversi e, in alcuni casi, le funzionalità si comportano in modo diverso a seconda del linguaggio. Molte di queste differenze sono specificate nelle descrizioni delle funzionalità, ma per altre informazioni è possibile vedere le sezioni su linguaggi specifici di Visual Studio.

> [!IMPORTANT]
> L'edizione di Visual Studio e le impostazioni in uso possono influire sulle funzionalità nell'IDE, che potrebbero essere diverse da quelle descritte in questo argomento.

## <a name="editor-features"></a>Funzionalità dell'editor

|||
|-|-|
|Colorazione della sintassi|Alcuni elementi della sintassi del codice e dei file di markup sono colorati in modo diverso per distinguerli. Ad esempio, le parole chiave (ad esempio `using` in C# e `Imports` in Visual Basic) sono di un colore, mentre i tipi (ad esempio `Console` e `Uri`) sono di un altro colore. Anche altri elementi della sintassi sono colorati, ad esempio i valori letterali stringa e i commenti. C++ usa i colori per distinguere i tipi, le enumerazioni e le macro dagli altri token.<br /><br /> È possibile visualizzare il colore predefinito per ogni tipo e modificare il colore per ogni specifico elemento della sintassi nella finestra di dialogo [Opzioni, Ambiente, Tipi di carattere](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), che può essere aperta dal menu **Strumenti**.|
|Contrassegni di errore e di avviso|Quando si aggiunge codice e si compila la soluzione, vengono visualizzate (a) sottolineature ondulate con diversi colori (note come sottolineature a zigzag) o (b) lampadine nel codice. Le sottolineature rosse denotano errori di sintassi, quelle blu errori del compilatore, quelle verdi gli avvisi e quelle viola altri tipi di errore. Le [lampadine](../ide/perform-quick-actions-with-light-bulbs.md) suggeriscono correzioni dei problemi e ne semplificano l'applicazione.<br /><br /> I colori predefiniti per ogni sottolineatura di errore e di avviso possono essere visualizzati nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Cercare **Errore di sintassi**, **Errore del compilatore**, **Avviso**e **Altro errore**.|
|Corrispondenza parentesi graffe|Quando il punto di inserimento viene inserito in una parentesi graffa di apertura in un file di codice, il punto e la parentesi graffa di chiusura vengono evidenziati. Questa funzionalità consente di ottenere un feedback immediato sulle parentesi graffe inserite non correttamente o mancanti. È possibile attivare o disattivare la corrispondenza tra parentesi graffe con l'impostazione **Evidenzia delimitatore automatico** (**Strumenti/Opzioni/Editor di testo**). È possibile modificare il colore di evidenziazione nell'impostazione **Tipi di carattere e colori** (**Strumenti/Opzioni/Ambiente**). Cercare **Corrispondenza parentesi (evidenziate)** o **Corrispondenza parentesi (rettangolo)**.|
|Visualizzatore di struttura|Per facilitare l'individuazione delle coppie di parentesi graffe di apertura e chiusura corrispondenti nel file di codice, vengono visualizzate linee tratteggiate che connettono le parentesi corrispondenti. In questo modo è possibile individuare più rapidamente il codice nella codebase. È possibile attivare o disattivare queste linee nell'opzione **Mostra guide per strutture** nella sezione **Visualizza** della pagina **Strumenti/Opzioni/Editor di testo/Generale**.|
|Numeri di riga|I numeri di riga possono essere visualizzati nel margine sinistro della finestra del codice. Non vengono visualizzati per impostazione predefinita. È possibile attivare questa opzione nelle impostazioni **Tutti i linguaggi dell'Editor di testo** (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**). È possibile visualizzare i numeri di riga per i singoli linguaggi di programmazione cambiando le impostazioni per i linguaggi (**Strumenti/Opzioni/Editor di testo/\<linguaggio>**). Per stampare i numeri di riga, è necessario selezionare **Includi numeri di riga** nella finestra di dialogo **Stampa**.|
|Rilevamento modifiche|Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Le modifiche apportate dall'apertura del file ma non ancora salvate vengono contrassegnate con una barra gialla nel margine sinistro (noto come margine di selezione). Dopo aver salvato le modifiche, ma prima di chiudere il file, la barra diventa verde. Se si annulla una modifica dopo aver salvato il file, la barra diventa arancione. Per attivare e disattivare questa funzionalità, modificare l'opzione **Revisioni** nelle impostazioni **Editor di testo** (**Strumenti/Opzioni/Editor di testo**).|
|Selezione di codice e testo|È possibile selezionare il testo con la modalità standard a flusso continuo oppure con la modalità riquadro, in cui non viene selezionato un set di righe, ma una porzione rettangolare di testo. Per effettuare una selezione in modalità riquadro, premere ALT mentre si trascina il mouse sulla selezione oppure premere ALT+MAIUSC+\<tasto di direzione>. La selezione include tutti i caratteri nel rettangolo definiti dal primo e dall'ultimo carattere nella selezione. Tutto ciò che viene digitato o incollato nell'area selezionata viene inserito nello stesso punto di ogni riga.|
|Zoom|È possibile ingrandire o ridurre qualsiasi finestra del codice tenendo premuto CTRL e spostando la rotellina del mouse (oppure CTRL+MAIUSC+. per ingrandire e CTRL+MAIUSC+, per ridurre). Per impostare una specifica percentuale di zoom, è anche possibile usare la casella Zoom nell'angolo in basso a sinistra della finestra del codice. La funzionalità di zoom non funziona nelle finestre degli strumenti.|
|Spazio virtuale|Per impostazione predefinita, le righe nell'editor di Visual Studio terminano dopo l'ultimo carattere, quindi il tasto freccia DESTRA alla fine della riga sposta il cursore all'inizio della riga successiva. In altri editor, una riga non termina dopo l'ultimo carattere ed è possibile posizionare il cursore in qualsiasi punto della riga. È possibile abilitare lo spazio virtuale nell'editor nelle impostazioni **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**. È possibile abilitare **Spazio virtuale** o **A capo automatico**, ma non entrambi.|
|Stampa|È possibile usare le opzioni nella finestra di dialogo **Stampa** per includere i numeri di riga o nascondere le aree di codice compresse quando si stampa un file. Nella finestra di dialogo **Imposta pagina** è possibile scegliere di stampare il percorso completo e il nome del file scegliendo **Intestazione pagina**.<br /><br /> È possibile impostare le opzioni di stampa a colori nella finestra di dialogo **Strumenti/Opzioni/Ambiente/Tipi di carattere e colori**. Scegliere **Stampante** nell'elenco **Mostra impostazioni per** per personalizzare la stampa a colori. Per la stampa di un file è possibile specificare colori diversi rispetto alla modifica di un file.|
|Fasi di rollforward e rollback globali|I comandi **Annulla ultima azione globale** e **Ripeti ultima azione globale** nel menu **Modifica** annullano o ripetono le azioni globali che interessano più file. Le azioni globali includono la ridenominazione di una classe o di uno spazio dei nomi, l'esecuzione di un'operazione di ricerca e sostituzione in una soluzione, il refactoring di un database o altre azioni che modificano più file. È possibile applicare questi comandi globali alle azioni nella sessione corrente di Visual Studio anche dopo aver chiuso la soluzione alla quale è stata applicata un'azione.|

## <a name="advanced-editing-features"></a>Funzionalità di modifica avanzate

Diverse funzionalità avanzate sono disponibili nel sottomenu **Modifica/Avanzate**. Non tutte le funzionalità sono disponibili per tutti i tipi di file di codice.

|||
|-|-|
|Formatta documento|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nel documento.|
|Formatta selezione|Imposta il rientro corretto per le righe di codice e sposta le parentesi graffe in righe separate nella selezione.|
|Inserisci tabulazione in righe selezionate|Cambia gli spazi iniziali in tabulazioni dove appropriato.|
|Rimuovi tabulazione da righe selezionate|Cambia le tabulazioni iniziali in spazi. Per convertire tutti gli spazi nel file in tabulazioni (o tutte le tabulazioni in spazi), è possibile usare i comandi `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Questi comandi non vengono visualizzati nei menu di Visual Studio, ma possono essere richiamati dalla finestra di accesso rapido o dalla finestra di comando.|
|Maiuscole|Converte in maiuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in maiuscolo il carattere nel punto di inserimento.|
|Minuscole|Converte in minuscolo tutti i caratteri nella selezione oppure, se non sono state effettuate selezioni, converte in minuscolo il carattere nel punto di inserimento.|
|Sposta in alto righe selezionate|Sposta la riga selezionata di una riga verso l'alto. Scelta rapida: ALT+freccia SU.|
|Sposta in basso righe selezionate|Sposta la riga selezionata di una riga verso il basso. Scelta rapida: ALT+freccia GIÙ.|
|Elimina spazio vuoto superfluo|Elimina le tabulazioni o gli spazi alla fine della riga corrente.|
|Mostra/Nascondi spazi|Visualizza gli spazi sotto forma di punti mediani e le tabulazioni sotto forma di frecce. La fine di un file viene visualizzata come un glifo rettangolare. Se è selezionato **Strumenti/Opzioni/Editor di testo/Tutti i linguaggi/A capo automatico/Mostra icone per ritorno a capo automatico**, viene visualizzato anche il glifo.|
|A capo automatico|Rende visibili tutte le righe di un documento nella finestra del codice. È possibile attivare e disattivare il ritorno a capo nelle impostazioni Tutti i linguaggi dell'editor di testo (**Strumenti/Opzioni/Editor di testo/Tutti i linguaggi**).|
|Commenta selezione|Aggiunge caratteri di commento alla selezione o alla riga corrente.|
|Rimuovi commento selezione|Rimuove tutti i caratteri di commento dalla selezione o dalla riga corrente.|
|Aumenta rientro riga|Aggiunge una tabulazione (o gli spazi equivalenti) alle righe selezionate o alla riga corrente.|
|Riduci rientro riga|Rimuove una tabulazione (o gli spazi equivalenti) dalle righe selezionate o dalla riga corrente.|
|Seleziona tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il tag.|
|Seleziona contenuto tag|In un documento che contiene tag, ad esempio XML o HTML, seleziona il contenuto.|

## <a name="navigate-and-find-code"></a>Eseguire ricerche e spostarsi nel codice

È possibile spostarsi nell'editor di codice in diversi modi, tra cui navigare avanti e indietro fino ai punti di inserimento precedenti, visualizzare la definizione di un tipo o membro e passare a un metodo specifico usando la barra di spostamento. Per altre informazioni, vedere [Esplorazione del codice](navigating-code.md).

## <a name="finding-references-in-your-code-base"></a>Ricerca di riferimenti nel codice di base

Per trovare i riferimenti a particolari elementi del codice presenti nella codebase, è possibile usare il comando **Trova tutti i riferimenti**. Inoltre, quando si sceglie un tipo o un membro, la funzionalità di **evidenziazione dei riferimenti** evidenzia automaticamente tutti i riferimenti a quel tipo o membro. Per altre informazioni, vedere [Finding references in your code](finding-references.md) (Ricerca di riferimenti nel codice).

## <a name="customize-the-editor"></a>Personalizzare l'editor

È possibile condividere le impostazioni di Visual Studio con un altro sviluppatore, renderle conformi a uno standard o ripristinare le impostazioni predefinite con il comando **Importazione/Esportazione guidata delle impostazioni** nel menu **Strumenti**. Nell'**Importazione/Esportazione guidata delle impostazioni** è possibile modificare impostazioni generali selezionate oppure impostazioni specifiche di un linguaggio e di un progetto.

Per definire i nuovi tasti di scelta o ridefinire quelli esistenti, passare a **Strumenti**, **Opzioni**, **Ambiente**, **Tastiera**. Per altre informazioni sui tasti di scelta rapida, vedere [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Per altre informazioni sulla personalizzazione dell'editor, vedere [Personalizzazione dell'editor](../ide/customizing-the-editor.md). Per le opzioni dell'editor specifiche per JavaScript, vedere [Opzioni, Editor di testo, JavaScript, Formattazione](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Vedere anche

[IDE di Visual Studio](../ide/visual-studio-ide.md)
