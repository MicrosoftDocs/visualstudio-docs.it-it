---
title: Opzioni e impostazioni per Python | Microsoft Docs
description: Informazioni di riferimento per le varie impostazioni di Visual Studio correlate al codice e ai progetti Python.
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 71c6e3424d93af2b3696f19193498ed6940cbc7a
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="options-for-python-in-visual-studio"></a>Opzioni di Python in Visual Studio

Per visualizzare le opzioni di Python, usare il comando di menu **Strumenti > Opzioni**, assicurarsi che sia selezionata l'opzione **Mostra tutte le impostazioni**, quindi passare a **Strumenti Python**:

![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general.png)

Sono disponibili anche opzioni specifiche per Python nella scheda **Editor di testo > Python > Avanzate** e nella scheda **Ambiente > Tipi di carattere e colori** all'interno del gruppo "Editor di testo".

> [!Note]
> Il gruppo **Sperimentale** contiene le opzioni per le funzionalità che sono ancora in fase di sviluppo e che non sono qui documentate. Sono spesso discusse in post nel [blog Python engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/) (Progettazione Python in Microsoft).

## <a name="general-options"></a>Opzioni generali

(Scheda **Strumenti > Opzioni > Python**.)

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Mostra la finestra di output durante la creazione degli ambienti virtuali| Attivato | Deselezionare per impedire che venga visualizzata la finestra di output. |
| Mostra la finestra di output durante l'installazione o la rimozione di pacchetti | Attivato | Deselezionare per impedire che venga visualizzata la finestra di output. |
| Esegui sempre pip come amministratore | Disattivato | Eleva sempre le operazioni `pip install` per tutti gli ambienti. Durante l'installazione dei pacchetti, Visual Studio richiede i privilegi di amministratore se l'ambiente si trova in un'area protetta del file system, come `c:\Program Files`. In questo prompt è possibile scegliere di elevare sempre `pip install` per tale specifico ambiente. Vedere [Scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab). |
| Genera automaticamente il database di completamento al primo uso | Attivato | *Si applica a Visual Studio 2017 versione 15.5 e versioni successive quando si usa un database di IntelliSense.* Assegna la priorità del completamento del database per una libreria, quando si scrive un codice che ne fa uso. Per altre informazioni, vedere [Informazioni di riferimento sulla finestra Ambienti - scheda Intellisense](python-environments-window-tab-reference.md). |
| Ignora variabili PYTHONPATH a livello di sistema | Attivato | PYTHONPATH viene ignorato per impostazione predefinita perché Visual Studio offre un mezzo più diretto per specificare i percorsi di ricerca negli ambienti e nei progetti. Per altri dettagli, vedere [Percorsi di ricerca](search-paths.md). |
| Aggiorna percorsi di ricerca quando vengono aggiunti file collegati | Attivato | Quando questa opzione è impostata, l'aggiunta di un [file collegato](managing-python-projects-in-visual-studio.md#linked-files) a un progetto aggiorna [Percorsi di ricerca](search-paths.md) in modo che IntelliSense possa includere il contenuto della cartella del file collegato nel relativo database di completamento. Deselezionare questa opzione per escludere tale contenuto dal database di completamento. |
| Avvisa quando non è possibile trovare il modulo importato | Attivato | Deselezionare questa opzione per non visualizzare gli avvisi quando si è certi che un modulo importato non è attualmente disponibile, ma non influisce comunque sul funzionamento del codice. |
| Segnala rientro incoerente come | Avvisi | Poiché l'interprete di Python dipende fortemente da un rientro corretto per determinare l'ambito, Visual Studio per impostazione predefinita genera dei messaggi di avviso quando rileva rientri incoerenti che potrebbero indicare errori di codifica. Per maggiore precisione, impostare su *Errori*, opzione che provoca la chiusura del programma in casi di questo tipo. Per disabilitare completamente questo comportamento, selezionare *No*. |
| Controlla disponibilità di sondaggi/novità | Una volta alla settimana | Imposta la frequenza con cui si consente a Visual Studio di aprire una finestra contenente una pagina web con sondaggi e notizie relativi a Python, qualora disponibili. Le opzioni sono *Mai*, *Una volta al giorno*, *Una volta alla settimana* e *Una volta al mese*. |
| Ripristina tutte le finestre di dialogo nascoste in modo permanente (pulsante) | N/D | Diverse finestre di dialogo presentano opzioni quali **Non visualizzare più questo messaggio**. Usare questo pulsante per cancellare tali opzioni e visualizzare nuovamente le finestre di dialogo. |

![Finestra di dialogo Opzioni di Python, scheda Generale](media/options-general.png)

## <a name="debugging-options"></a>Opzioni di debug

(Scheda **Strumenti > Opzioni > Python > Debug**.)

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Chiedi conferma prima dell'esecuzione quando sono presenti errori | Attivato | Se impostato, viene chiesto di confermare che si desidera eseguire il codice contenente errori. Deselezionare questa opzione per disabilitare l'avviso. |
| Attendi input quando il processo viene chiuso in modo anomalo<br/><br/>Attendi input quando il processo viene chiuso normalmente | Attivato (per entrambi) | Un programma Python avviato da Visual Studio viene eseguito nella propria finestra della console. Per impostazione predefinita, la finestra attende che venga premuto un tasto prima di chiudere il programma, indipendentemente dalla modalità con cui viene chiuso il programma. Per rimuovere il prompt e chiudere la finestra automaticamente, deselezionare una o entrambe le opzioni. |
| Output del programma tee nella finestra di output del debug | Attivato | Visualizza l'output del programma in una finestra della console separata e nella finestra di output di Visual Studio. Deselezionare questa opzione per visualizzare l'output solo nella finestra della console separata. |
| Interrompi in caso di eccezione SystemExit con codice di uscita zero | Disattivato | Se l'opzione è selezionata, il debugger viene arrestato su questa eccezione. Se è deselezionata, il debugger viene chiuso senza interruzioni. |
| Abilita il debug della libreria standard Python | Disattivato | Consente di eseguire il codice sorgente della libreria standard durante il debug, ma aumenta il tempo necessario all'avvio del debugger.|

![Finestra di dialogo Opzioni di Python, scheda Debug](media/options-debugging.png)

## <a name="diagnostics-options"></a>Opzioni di diagnostica

(Scheda **Strumenti > Opzioni > Python > Diagnostica**.)

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Includi log di analisi | Attivato | Include log dettagliati relativi all'analisi di ambienti Python installati durante il salvataggio della diagnostica in un file o la copia negli Appunti tramite i pulsanti. Questa opzione può aumentare notevolmente le dimensioni del file generato, ma spesso è necessaria per diagnosticare problemi di IntelliSense. |
| Salva diagnostica nel file (pulsante) | N/D | Richiede un nome di file, quindi salva il log in un file di testo. |
| Copia diagnostica negli Appunti (pulsante) | N/D | Inserisce l'intero contenuto del log negli Appunti. Questa operazione potrebbe richiedere tempo a seconda delle dimensioni del log. |

![Finestra di dialogo Opzioni di Python, scheda Diagnostica](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Opzioni della finestra interattiva

(Scheda **Strumenti > Opzioni > Python > Finestre interattive**.)

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Script | N/D | Specifica una cartella generale per gli script di avvio valida per le finestre interattive per tutti gli ambienti. Vedere [Script di avvio](python-environments-window-tab-reference.md#startup-scripts). Si noti, tuttavia, che questa funzionalità non è attualmente supportata. |
| Spostarsi nella cronologia con le frecce su/giù | Attivato | Usare i tasti freccia per spostarsi nella cronologia, nella finestra interattiva. Deselezionare questa impostazione per usare i tasti freccia per spostarsi invece all'interno dell'output della finestra interattiva. |
| Modalità di completamento | Valutare unicamente le espressioni senza chiamate di funzione | Il processo di determinazione dei membri disponibili su un'espressione nella finestra interattiva può richiedere la valutazione dell'espressione incompleta corrente, con la conseguente chiamata ripetuta di effetti collaterali o funzioni. L'impostazione predefinita, *Valuta solo le espressioni senza chiamate di funzione* esclude le espressioni che sembrano chiamare una funzione, ma valuta altre espressioni. Ad esempio, valuta `a.b` ma non `a().b`.  *Non valutare mai le espressioni* evita tutti gli effetti collaterali e usa solo il motore di IntelliSense normale per i suggerimenti. *Valuta tutte le espressioni* valuta l'espressione completa per ottenere suggerimenti, indipendentemente dagli effetti collaterali. |
| Nascondi suggerimenti analisi statica | Disattivato | Se è impostata questa opzione, vengono visualizzati solo i suggerimenti ottenuti dalla valutazione dell'espressione. Se è associata alla modalità di completamento *Non valutare mai le espressioni*, non viene visualizzato alcun completamento utile nella finestra interattiva. |

![Finestra di dialogo delle opzioni di Python, scheda Finestre interattive](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Opzioni avanzate dell'editor di Python

(Scheda **Strumenti > Opzioni > Editor di testo > Python > Avanzate**.)

### <a name="completion-results"></a>Risultati del completamento

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Il completamento dei membri visualizza l'intersezione dei membri | Disattivato | Se l'opzione è impostata, vengono visualizzati solo i completamenti supportati da tutti i tipi possibili. |
| Elenco di filtri in base alla stringa di ricerca | Attivato | Applica il filtro dei suggerimenti di completamento durante la digitazione (l'opzione è selezionata per impostazione predefinita). |
| Visualizza automaticamente i completamenti per tutti gli identificatori | Attivato | Deselezionare questa opzione per disabilitare i completamenti sia nell'editor che nelle finestre interattive. |

### <a name="selection-in-completion-list"></a>Selezione negli elenchi di completamento

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Commit alla digitazione dei caratteri seguenti | `{}[]().,:;+-*/%&&#124;^~=<>#@\` | Questi caratteri seguono in genere un identificatore che può essere selezionato da un elenco di completamento, pertanto è consigliabile eseguire il commit del completamento semplicemente digitando un carattere. È possibile rimuovere o aggiungere caratteri specifici all'elenco in base alle esigenze.  |
| Immetti completamento corrente dei commit | Attivato | Se questa opzione è impostata, il tasto INVIO sceglie e applica il completamento attualmente selezionato in modo analogo ai caratteri riportati sopra (ma ovviamente, non esiste un carattere per il tasto Invio, pertanto non può entrare direttamente in tale elenco). |
| Aggiungi nuova riga quando si preme Invio alla fine della parola digitata | Disattivato | Per impostazione predefinita, se si digita la parola che viene visualizzata nella finestra popup di completamento e si preme INVIO, si esegue il commit di tale completamento. Impostando questa opzione, si esegue il commit dei completamenti quando si finisce di digitare l'identificatore, di conseguenza, premendo il tasto INVIO viene inserita una nuova riga. |

### <a name="miscellaneous-options"></a>Altre opzioni

| Opzione | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Attiva modalità struttura all'apertura del file | Attivato | Attiva automaticamente la funzionalità di struttura nell'editor di Visual Studio all'apertura di un file di codice Python. |
| Paste removed REPL prompts (Incolla prompt REPL rimossi) | Attivato | Rimuove >>> e ... dal testo incollato, consentendo il trasferimento agevole del codice dalla finestra interattiva all'editor. Deselezionare questa opzione se è necessario conservare tali caratteri provenienti da altre origini. |
| Nomi dei colori in base ai tipi | Attivato | Abilita la colorazione della sintassi nel codice Python. |

![Finestra di dialogo delle opzioni dell'editor di Python, scheda avanzate](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opzioni Tipi di carattere e colori

(Scheda **Ambiente > Tipi di carattere e colori** all'interno del gruppo "Editor di testo".)

I nomi delle opzioni di Python sono preceduti tutti dal prefisso "Python" e sono autoesplicativi. Il tipo di carattere predefinito per tutti i temi colori di Visual Studio è 10pt Consolas Regular (non grassetto). I colori predefiniti variano a seconda del tema. In genere, si modifica un tipo di carattere o un colore se la leggibilità del testo non è adeguata con le impostazioni predefinite.

![Opzioni per tipo di carattere e colori di Python](media/options-fonts-and-colors.png)