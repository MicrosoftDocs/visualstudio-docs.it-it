---
title: Finestra interattiva di Python (REPL) | Microsoft Docs
description: Come usare la finestra interattiva (REPL) per il codice Python in Visual Studio per lo sviluppo rapido di codice.
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 3492bdc10b94a58804ab31c71d2bdc7a66a77509
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="working-with-the-python-interactive-window"></a>Uso della finestra interattiva di Python

In Visual Studio è disponibile una finestra REPL (Read-Evaluate-Print Loop) per ognuno degli ambienti Python, che costituisce un miglioramento rispetto alla funzionalità REPL disponibile con `python.exe` dalla riga di comando. La finestra interattiva (aperta con i comandi di menu **Visualizza > Altre finestre > &lt;Ambiente&gt; interattivo**) consente di immettere codice Python arbitrario e visualizzare risultati immediati. Questo modo di generare codice consente di imparare e sperimentare con API e librerie e sviluppare in modo interattivo codice funzionante da includere nei propri progetti.

![Finestra interattiva di Python](media/interactive-window.png)

In Visual Studio sono disponibili numerose modalità REPL tra cui scegliere:

| REPL | Descrizione | Modifica | Debug | Immagini |
| --- | --- | --- | --- | --- |
| Standard | REPL predefinito, comunica direttamente con Python | Modifica standard (su più righe e così via). | Sì, tramite `$attach` | No |
| Debug | REPL predefinito, comunica con il processo Python di cui è in corso il debug | Modifica standard | Solo debug | No |
| IPython | REPL comunica con il back-end di IPython | Comandi IPython, vantaggi di Pylab | No | Sì, inline in REPL |
| IPython senza Pylab | REPL comunica con il back-end di IPython | IPython standard | No | Sì, finestra separata | 

Questo articolo descrive le modalità REPL **Standard** e **Debug**. Per informazioni dettagliate sulle modalità IPython, vedere [Uso di IPython nella finestra interattiva](interactive-repl-ipython.md).

Per una procedura dettagliata con esempi, incluse le interazioni con l'editor come CTRL+INVIO, vedere [Passaggio 3: Uso della finestra interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) sulla finestra interattiva (2m 22s).|

## <a name="opening-an-interactive-window"></a>Apertura di una finestra interattiva

È possibile aprire la finestra interattiva per un ambiente in diversi modi.

Passare prima alla finestra Ambienti Python (**Visualizza > Altre finestre > Ambienti Python** oppure premere CTRL+K,CTRL+') e selezionare il comando o il pulsante **Apri finestra interattiva** per un ambiente scelto.

![Collegamento Finestra interattiva nella finestra Ambienti Python](media/interactive-window-opening.png)

In seguito, nella parte inferiore del menu **Visualizza > Altre finestre** è presente un comando **Finestra Python interattivo** per l'ambiente predefinito oltre a un comando per passare alla finestra degli ambienti:

![Voci di menu relative alla finestra interattiva in Visualizza > Altre finestre](media/interactive-window-menu.png)

È quindi possibile aprire una finestra interattiva nel file di avvio del progetto oppure per un file autonomo selezionando il comando di menu **Debug > Esegui progetto in Python interattivo oppure Esegui file in Python interattivo** (MAIUSC+ALT+F5):

![Menu Esegui progetto in Python interattivo](media/interactive-execute-project.png)

È infine possibile selezionare il codice nel file e usare il [comando per inviare codice alla finestra interattiva](#send-code-to-interactive-command) descritto più avanti.

## <a name="interactive-window-options"></a>Opzioni della finestra interattiva

È possibile controllare vari aspetti della finestra interattiva tramite **Strumenti > Opzioni > Strumenti Python > Finestre interattive** (vedere [Opzioni](python-support-options-and-settings-in-visual-studio.md)):

![Opzioni della finestra interattiva di Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Uso della finestra interattiva

Dopo aver aperto la finestra interattiva, è possibile iniziare a immettere codice riga per riga al prompt dei comandi di `>>>`. La finestra interattiva esegue ogni riga non appena viene immessa, incluse le operazioni di importazione di moduli, definizione di variabili e così via:

![Finestra interattiva di Python](media/interactive-window.png)

L'eccezione si verifica quando sono necessarie righe di codice aggiuntivo per creare un'istruzione completa, ad esempio quando un'istruzione `for` termina con i due punti, come illustrato in precedenza. In questi casi, il prompt della riga diventa `...`, per indicare che è necessario immettere altre righe per il blocco, come illustrato nella quarta e nella quinta riga della figura precedente. Quando si preme INVIO in una riga vuota, la finestra interattiva chiude il blocco e lo esegue nell'interprete.

> [!Tip]
> La finestra interattiva costituisce un miglioramento rispetto all'esperienza REPL di Python dalla riga di comando in quanto imposta automaticamente un rientro per le istruzioni che appartengono a un ambito circostante. La relativa cronologia (richiamata con la freccia su) visualizza inoltre elementi su più righe, mentre la riga di comando REPL visualizza solo singole righe.

<a name="meta-commands"></a> La finestra interattiva supporta anche diversi metacomandi. Tutti i metacomandi iniziano con `$` ed è possibile digitare `$help` per ottenere un elenco dei metacomandi oppure `$help <command>` per ottenere i dettagli relativi all'utilizzo di un comando specifico.

| Metacomando | Descrizione |
| --- | --- |
| `$$` | Inserisce un commento ed è quindi utile per aggiungere commenti al codice durante la sessione. |
| `$attach` | Collega il debugger di Visual Studio al processo della finestra REPL per abilitare il debug. |
| `$cls`, `$clear` | Cancella il contenuto della finestra dell'editor, lasciando intatti la cronologia e il contesto di esecuzione. |
| `$help` | Visualizza un elenco di comandi o la Guida su un comando specifico. |
| `$load` | Carica i comandi dal file e viene eseguito fino al completamento. |
| `$mod` | Consente di passare dall'ambito corrente al nome di modulo specificato. |
| `$reset` | Ripristina lo stato iniziale dell'ambiente di esecuzione, mantenendo però la cronologia. |
| `$wait` | Attende almeno il numero di millisecondi specificato. |

I comandi sono anche estendibili tramite le estensioni di Visual Studio implementando ed esportando `IInteractiveWindowCommand` ([esempio](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switching-scopes"></a>Passaggio a un altro ambito

Per impostazione predefinita, l'ambito della finestra interattiva di un progetto è impostato sul file di avvio del progetto, come se la finestra venisse eseguita dal prompt dei comandi. Per un file autonomo l'ambito corrisponde al file stesso. È però possibile cambiare in qualsiasi momento l'ambito durante la sessione REPL tramite il menu a discesa disponibile nella parte superiore della finestra interattiva:

![Ambiti della finestra interattiva](media/interactive-scopes.png)

Dopo aver importato un modulo, ad esempio digitando `import importlib`, nel menu a discesa vengono visualizzate le opzioni per passare a un qualsiasi ambito presente in tale modulo. Nella finestra interattiva viene anche visualizzato un messaggio che indica il nuovo ambito, in modo che sia possibile tenere traccia di come si è arrivati a un determinato stato nel corso della sessione.

Se si immette `dir()` in un ambito, vengono visualizzati gli identificatori validi presenti in tale ambito, inclusi nomi di funzione, classi e variabili. Se ad esempio si usa `import importlib` seguito da `dir()`, viene visualizzato quanto segue:

![Finestra interattiva nell'ambito importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Comando per inviare codice alla finestra interattiva

Oltre a lavorare direttamente nella finestra interattiva, è possibile selezionare codice nell'editor, fare clic con il pulsante destro del mouse e scegliere **Invia a Interactive** o premere CTRL+INVIO.

![Comando di menu Invia a finestra interattiva](media/interactive-send-to.png)

Questo comando è utile per lo sviluppo di codice iterativo o evolutivo, tra cui il test del codice durante lo sviluppo. Dopo aver inviato una parte di codice alla finestra interattiva e averne visualizzato l'output, è ad esempio possibile premere la freccia su per visualizzare di nuovo il codice, modificarlo e testarlo rapidamente premendo CTRL+INVIO. Se si preme INVIO alla fine dell'input, si esegue il codice, mentre se lo si preme durante la digitazione viene inserito un carattere di nuova riga. Dopo aver creato il codice desiderato, è possibile copiarlo nuovamente nel file di progetto.

> [!Tip]
> Per impostazione predefinita, Visual Studio rimuove i prompt >>> e ... REPL quando si incolla il codice dalla finestra interattiva nell'editor. È possibile modificare questo comportamento nella scheda **Strumenti > Opzioni > Editor di testo > Python > Avanzate** scheda usando l'opzione **L'operazione Incolla rimuove i prompt REPL**. Vedere [Opzioni - Miscellaneous options (Opzioni varie)](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Quando si usa un file di codice come un'area dei file temporanei, spesso si ha un piccolo blocco di codice che si vuole inviare in una sola volta. Per raggruppare il codice, contrassegnare il codice come una *cella codice* aggiungendo un commento che inizia con `#%%` all'inizio della cella, che termina quella precedente. Le celle di codice possono essere compresse ed espanse e l'uso di CTRL+INVIO all'interno di una cella di codice invia l'intera cella alla finestra interattiva e passa alla successiva.

Visual Studio rileva anche le celle di codice a partire da commenti come `# In[1]:`, che è il formato visualizzato quando si esporta un blocco appunti Jupyter come file Python. Questo rilevamento semplifica l'esecuzione di un blocco appunti da [Azure Notebooks](https://notebooks.azure.com/) scaricandolo come file Python, aprendolo in Visual Studio e usando CTRL+INVIO per eseguire ogni cella.

![Celle di codice interattive](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportamento di IntelliSense

La finestra interattiva include la funzionalità IntelliSense basata su oggetti attivi, a differenza dell'editor del codice in cui IntelliSense è basato solo sull'analisi del codice sorgente. Questi suggerimenti risultano più corretti nella finestra interattiva, in particolare con codice generato dinamicamente. Può però capitare che funzioni con effetti collaterali, ad esempio la registrazione di messaggi, influiscano negativamente sull'esperienza di sviluppo.

Se questo comportamento costituisce un problema, modificare le impostazioni in **Strumenti > Opzioni > Strumenti Python > Finestre interattive** nel gruppo **Modalità di completamento**, come descritto in [Opzioni - Interactive Windows options (Opzioni della finestra interattiva)](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
