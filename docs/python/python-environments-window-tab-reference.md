---
title: Informazioni di riferimento sulla finestra Ambienti Python | Microsoft Docs
description: Dettagli su ognuna delle schede visualizzate nella finestra Ambienti Python in Visual Studio.
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f323bfbe65a5e25935673674e604425bc33185c
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="python-environments-window-tabs-reference"></a>Informazioni di riferimento sulle schede della finestra Ambienti Python

Per aprire la finestra **Ambienti Python**:

- Selezionare il comando di menu **Visualizza > Altre finestre > Ambienti Python**.
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in Esplora soluzioni e scegliere **Visualizza tutti gli ambienti Python**.

Se si allarga a sufficienza la finestra **Ambienti Python**, queste opzioni vengono visualizzate come schede, un layout che può risultare più comodo. Per maggiore chiarezza, le schede in questo articolo sono visualizzate nella modalità espansa.

![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Scheda Panoramica

Include informazioni di base e comandi per l'ambiente:

![Scheda Panoramica di Ambienti Python](media/environments-overview-tab.png)

| Comando | Descrizione |
| --- | --- |
| Make this environment the default for new projects (Imposta questo ambiente come predefinito per i nuovi progetti) | Imposta l'ambiente attivo, facendo sì che Visual Studio non risponda per un breve periodo finché non viene caricato il database di IntelliSense. Gli ambienti che contengono molti pacchetti potrebbero non rispondere per un periodo più lungo. |
| Visita il sito Web del server di distribuzione | Apre un browser all'URL offerto dalla distribuzione di Python. Python 3.x, ad esempio, passa a python.org. |
| Apri finestra interattiva | Apre la [finestra (REPL) interattiva](python-interactive-repl-in-visual-studio.md) per questo ambiente all'interno di Visual Studio, applicando qualunque [script di avvio (vedere sotto)](#startup-scripts). |
| Esplora gli script interattivi | Vedere [Script di avvio](#startup-scripts). |
| Usa la modalità interattiva IPython | Se impostato, apre la finestra interattiva con IPython per impostazione predefinita. Questa inline abilitata viene tracciata come la sintassi estesa IPython quale `name?` per visualizzare la Guida e `!command` per i comandi della shell. Questa opzione è consigliata quando si usa una distribuzione Anaconda, perché richiede pacchetti aggiuntivi. Per altre informazioni, vedere [Uso di IPython nella finestra interattiva](interactive-repl-ipython.md). |
| Apri in PowerShell | Avvia l'interprete in una finestra di comando di PowerShell. |
| (Collegamenti alla cartella e ai programmi) | Consentono di accedere rapidamente alla cartella di installazione dell'ambiente, all'interprete python.exe e all'interprete pythonw.exe. Il primo apre Esplora risorse, gli ultimi due aprono una finestra della console. |

### <a name="startup-scripts"></a>Script di avvio

Quando si usano le finestre interattive nel proprio flusso di lavoro quotidiano, è probabile sviluppare funzioni helper da usare regolarmente. Ad esempio, è possibile creare una funzione che apre un dataframe in Excel, quindi salvare tale codice come script di avvio in modo che sia sempre disponibile nella finestra interattiva.

Gli script di avvio contengono codice che la finestra interattiva carica ed esegue automaticamente, incluse le importazioni, le definizioni di funzione e letteralmente qualunque altra cosa. Tali script sono referenziati in due modi:

1. Quando si installa un ambiente, Visual Studio crea una cartella `Documents\Visual Studio 2017\Python Scripts\<environment>` dove &lt;environment&gt; corrisponde al nome dell'ambiente. È possibile passare alla cartella specifica dell'ambiente con il comando **Esplora gli script interattivi**. Quando si avvia la finestra interattiva per tale ambiente, vengono caricati ed eseguiti tutti i file `.py` disponibili qui in ordine alfabetico.

1. Il controllo **Script** nella scheda **Strumenti > Opzioni > Strumenti Python > 	Finestre interattive** (vedere [Opzioni delle finestre interattive](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) è destinato a specificare una cartella aggiuntiva per gli script di avvio che vengono caricati ed eseguiti in tutti gli ambienti. Tuttavia, questa funzionalità non è attualmente operativa.

## <a name="configure-tab"></a>Scheda Configura

Se disponibile, contiene i dettagli descritti nella tabella seguente. Se questa scheda non è presente, Visual Studio gestisce automaticamente tutti i dettagli.

![Scheda Configura di Ambienti Python](media/environments-configure-tab.png)

| Campo | Descrizione |
| --- | --- |
| **Descrizione** | Nome da assegnare all'ambiente. |
| **Percorso di prefisso** | Percorso della cartella di base dell'interprete. Se si compila questo valore e si fa clic su **Rilevamento automatico**, Visual Studio prova a compilare automaticamente gli altri campi. |
| **Percorso dell'interprete** | Percorso del file eseguibile dell'interprete, costituito in genere dal percorso di prefisso seguito da `python.exe`. |
| **Interprete con finestra** | Percorso del file eseguibile non di console, spesso costituito dal percorso di prefisso seguito da `pythonw.exe`. |
| **Percorso della libreria**<br/>(se disponibile) | Radice della libreria standard. Questo valore può essere ignorato se Visual Studio è in grado di richiedere un percorso più accurato all'interprete. |
| **Versione del linguaggio** | Selezionata dal menu a discesa. |
| **Architettura** | In genere rilevata e inserita automaticamente; in caso contrario, il valore da specificare è 32 bit o 64 bit. |
| **Variabile di ambiente del percorso** | Variabile di ambiente usata dall'interprete per trovare i percorsi di ricerca. All'avvio di Python, Visual Studio modifica il valore della variabile in modo che contenga i percorsi di ricerca del progetto. In genere questa proprietà deve essere impostata su `PYTHONPATH`, ma alcuni interpreti usano un valore diverso. |

## <a name="packages-tab"></a>Scheda Pacchetti

*Denominata anche "pip" nelle versioni precedenti.*

Consente di gestire i pacchetti installati nell'ambiente, nonché di cercare e installare quelli nuovi (incluse eventuali dipendenze).

I pacchetti già installati vengono visualizzati con controlli per aggiornare (freccia rivolta verso l'alto) e disinstallare (X in un cerchio) il pacchetto:

![Scheda Pacchetti della finestra Ambienti Python](media/environments-pip-tab-controls.png)

Quando di immette un termine di ricerca viene filtrato l'elenco dei pacchetti installati e quello dei pacchetti che possono essere installati da PyPI.

![Scheda Pacchetti nella finestra Ambienti Python con la ricerca di "num"](media/environments-pip-tab.png)

È anche possibile immettere direttamente qualsiasi comando `pip install` nella casella di ricerca, compresi i flag, come `--user` o `--no-deps`.

L'installazione di un pacchetto crea sottocartelle all'interno della cartella `Lib` dell'ambiente nel file system. Ad esempio, se si dispone di Python 3.6 installato in `c:\Python36`, i pacchetti vengono installati in `c:\Python36\Lib`; se è installato Anaconda3 in `c:\Program Files\Anaconda3` i pacchetti vengono installati in `c:\Program Files\Anaconda3\Lib`.

Nel secondo caso, poiché l'ambiente si trova in un'area protetta del file system, `c:\Program Files`, Visual Studio deve eseguire `pip install` con privilegi elevati per consentirgli di creare sottocartelle di pacchetto. Quando è necessaria l'elevazione, Visual Studio visualizza il prompt dei comandi "Potrebbero essere necessari i privilegi di amministratore per installare, aggiornare o rimuovere i pacchetti per questo ambiente":

![Richiesta di elevazione dei privilegi per l'installazione del pacchetto](media/environments-pip-elevate.png)

**Eleva ora** concede privilegi di amministratore per pip per un'unica operazione, subordinatamente anche a qualunque richiesta di permessi del sistema operativo. Se si seleziona **Continua senza privilegi di amministratore** viene tentata l'installazione del pacchetto, ma pip ha esito negativo quando cerca di creare delle cartelle, con un output come "errore: impossibile creare 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': Autorizzazione negata."

Selezionando **Eleva sempre quando si installano o rimuovono pacchetti** si impedisce la visualizzazione della finestra di dialogo per l'ambiente in questione. Per visualizzare nuovamente la finestra di dialogo, passare a **Strumenti > Opzioni > Strumenti Python > Generale** e selezionare il pulsante, **Ripristina tutte le finestre di dialogo nascoste in modo permanente**.

In tale scheda, è anche possibile selezionare **Esegui sempre pip come amministratore** per eliminare la finestra di dialogo per tutti gli ambienti. Vedere [Opzioni - Scheda Generale](python-support-options-and-settings-in-visual-studio.md#general-options).

## <a name="intellisense-tab"></a>Scheda IntelliSense

Mostra lo stato corrente del database di completamento IntelliSense:

![Scheda IntelliSense di Ambienti Python](media/environments-intellisense-tab.png)

In **Visual Studio 2017 versione 15.5** e versioni precedenti, i completamenti IntelliSense dipendono da un database che è stato compilato per tale libreria. La creazione del database viene eseguita in background quando viene installata una libreria, ma potrebbe richiedere tempo e non essere completa quando si avvia la scrittura del codice. **Visual Studio 2017 versione 15.6** e versioni successive usano un metodo più rapido per fornire i completamenti che non dipendono dal database a meno che non si scelga espressamente di abilitarlo.

Quando Visual Studio rileva un nuovo ambiente (o ne viene aggiunto uno), avvia automaticamente la compilazione del database analizzando i file di origine della libreria. Questo processo può avvenire ovunque e richiedere da un minuto a oltre un'ora a seconda dei componenti installati. Anaconda include ad esempio molte librerie, di conseguenza la compilazione del database può richiedere molto tempo. Al termine dell'operazione, si ottengono informazioni IntelliSense dettagliate e non è necessario aggiornare di nuovo il database (con il pulsante **Aggiorna database**) fino a quando non si installano altre librerie.

Le librerie i cui dati non sono stati compilati vengono contrassegnate con un punto esclamativo (**!**). È presente un punto esclamativo (**!**) anche accanto al database di un ambiente non completo nell'elenco degli ambienti principale.

## <a name="see-also"></a>Vedere anche

- [Gestione di ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Uso di requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
