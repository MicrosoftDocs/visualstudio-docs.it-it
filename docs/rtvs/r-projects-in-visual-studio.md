---
title: Progetti in R Tools per Visual Studio | Microsoft Docs
description: "Come creare una gestione di progetti di R in Visual Studio inclusi proprietà, comandi di progetto e modelli."
ms.custom: 
ms.date: 06/29/2017
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
ms.openlocfilehash: 230e3a1d9241a26bd39cda6cb5f88a9ed180d6e2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="creating-r-projects-in-visual-studio"></a>Creazione di progetti R in Visual Studio

Un progetto R (un file `.rxproj`) identifica tutti i file di origine e di contenuto associati al progetto,  contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici. Le informazioni relative all'area di lavoro, ad esempio l'elenco dei pacchetti installati, vengono gestite, tuttavia, separatamente nell'area di lavoro stessa.

I progetti vengono sempre gestiti all'interno di una *soluzione* di Visual Studio, che può contenere un numero qualsiasi di progetti che possono fare riferimento l'uno all'altro. Vedere [Usare più tipi di progetto in Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Creazione di un nuovo progetto R

1. Avviare Visual Studio.
1. Scegliere **File > Nuovo > Progetto** (CTRL+MAIUSC+N)
1. Selezionare "Progetto R" in **Modelli > R**, assegnare un nome e un percorso al progetto e selezionare **OK**:

    ![Finestra di dialogo Nuovo progetto per R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

Questo comando crea un progetto con un file `script.R` vuoto aperto nell'editor. Si noti anche che in **Esplora soluzioni** sono presenti altri due file per il progetto:

![Contenuto di un progetto R creato dal modello](media/projects-template-results.png)

Il file `.Rhistory` registra tutti i comandi immessi dall'utente nella finestra [R interattivo](interactive-repl-for-r-in-visual-studio.md). È possibile aprire una finestra dedicata per la cronologia con il comando **R Tools > Windows > Cronologia**. Tale finestra ha un pulsante della barra degli strumenti e voci di menu contestuale per cancellare il contenuto della cronologia.

Il file `rproject.rproj` consente di gestire alcune impostazioni di progetto specifiche di R non altrimenti gestite da Visual Studio:

| Proprietà | Impostazione predefinita | Descrizione |
| --- | --- | --- |
| Versione | 1.0 | La versione di R Tools per Visual Studio usata per creare il progetto. |
| RestoreWorkspace | Impostazione predefinita | Carica automaticamente le variabili precedenti dell'area di lavoro dal file `.RData` nella directory del progetto. |
| SaveWorkspace | Impostazione predefinita | Salva le variabili correnti dell'area di lavoro per il file `.RData` nella directory del progetto quando quest'ultimo viene chiuso. |
| AlwaysSaveHistory | Impostazione predefinita | Salva la cronologia corrente della finestra interattiva per il file `.RHistory` nella directory del progetto quando quest'ultimo viene chiuso. |
| EnableCodeIndexing | Yes | Determina se eseguire un'attività di indicizzazione in background per velocizzare le ricerche di codice. |
| UseSpacesForTab | Yes | Determina se inserire spazi (Sì) o un carattere di tabulazione (No) quando viene premuto Tab nell'editor. |
| NumSpacesForTab | 2 | Il numero di spazi da inserire se UseSpacesForTab è impostato su Sì. |
| Codifica | UTF-8 | La codifica predefinita per i file `.R`. |
| RnwWeave | Sweave | Pacchetto da usare per la composizione di un file Rnw. |
| LaTeX | pdfLaTeX | Libreria da usare per la conversione da RMarkdwon a PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Conversione di una cartella di file in un progetto R

Se si vuole gestire all'interno di un progetto una cartella di file `.R` esistente, eseguire i passaggi seguenti:

1. Creare un nuovo progetto in Visual Studio come descritto nella sezione precedente.
1. Copiare i file nella cartella del progetto.
1. In Esplora soluzioni di Visual Studio fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Elemento esistente** e selezionare i file che si vogliono aggiungere. Quando si seleziona **OK**, questi compaiono nell'albero del progetto.
1. Per organizzare il codice in sottocartelle, fare clic con il pulsante destro del mouse sul progetto, selezionare **Aggiungi > Nuova cartella**, quindi copiare i file nella cartella appena creata e aggiungere gli elementi esistenti nel passaggio 3.

## <a name="project-properties"></a>Proprietà di progetti

Per aprire le pagine delle proprietà del progetto, fare clic con il pulsante destro del mouse su **Esplora soluzioni** e selezionare **Proprietà** oppure scegliere la voce di menu **Progetto > Proprietà (nome progetto)...*. La finestra visualizzata riporta le proprietà del progetto:

| Scheda | Proprietà | Descrizione |
| --- | --- | --- |
| Esegui | File di avvio | Il nome del file che viene eseguito con il comando **Source startup file** (File di avvio di origine), F5, **Debug > Avvio del debug** o **Debug > Avvia senza eseguire debug**. Facendo clic con il pulsante destro del mouse sul file nel progetto e selezionando **Imposta come script R di avvio**, il file viene impostato anche come file di avvio. |
| | Ripristina R interattivo durante l'esecuzione | Cancella tutte le variabili dall'area di lavoro della finestra interattiva quando si esegue il progetto. Questa operazione garantisce che non ci sia contenuto residuo dell'area di lavoro dall'esecuzione precedente. |
| | Percorso progetto remoto | Percorso di un'area di lavoro remota. |
| | Trasferisci file durante l'esecuzione | Indica se i file di progetto, soggetti al filtro in **File da trasferire**, devono essere copiati in un'area di lavoro remota a ogni esecuzione. |
| | File da trasferire | Nomi di file e caratteri jolly che indicano i file specifici da copiare un'area di lavoro remota se l'opzione **Trasferisci file durante l'esecuzione** è selezionata. |
| Impostazioni | (File Settings.R) | Le impostazioni dei progetti R derivano dai file `Settings.R` o `*.Settings.R` che si trovano all'interno del progetto. Se non è presente alcun file di impostazioni, è possibile aggiungere variabili, salvare la pagina. Un file `Settings.R` predefinito viene creato automaticamente. È possibile aggiungere un file di impostazioni al progetto anche tramite il comando di menu **File > Aggiungi nuovo elemento...*. <br/> Le impostazioni vengono memorizzate come codice R e il file può essere originato prima di eseguire altri moduli, pre-popolando in questo modo l'ambiente con le impostazioni predefinite. |

## <a name="r-specific-project-commands"></a>Comandi di progetto specifici di R

I progetti di Visual Studio supportano diversi comandi generali sia tramite il menu di scelta rapida che tramite il menu **Progetto**. Per i dettagli su queste funzionalità generali, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Tenere presente, tuttavia, che 

Per i progetti R, R Tools per Visual Studio (RTVS) aggiunge diversi comandi specifici al menu di scelta rapida e un certo numero di file e cartelle all'interno del progetto.

| Comando | Descrizione |
| --- | --- |
| Imposta directory di lavoro qui | Imposta la directory di lavoro della finestra interattiva R sulla cartella del progetto, che può essere usata anche in qualsiasi sottocartella all'interno di un progetto. |
| Apri cartella superiore | Apre Esplora risorse in corrispondenza del percorso del file selezionato. | 
| Aggiungi script R | Crea e apre un nuovo file `.R` con nome predefinito. È anche possibile usare il comando **Aggiungi > Nuovo elemento...** per creare file `.R`, nonché diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates). |
| Aggiungi R Markdown | Crea e apre un nuovo documento `.rmd` con nome predefinito. È anche possibile usare il comando **Aggiungi > Nuovo elemento...** per creare file `.rmd`, nonché diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates).  | 
| Pubblica stored procedure | Avvia il processo di pubblicazione di eventuali stored procedure presenti all'interno di script R. Vedere [Uso di stored procedure di SQL Server](integrating-sql-server-with-r.md#working-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>Modelli di elemento specifici di R

RTVS include diversi modelli per tipi di file specifici. È possibile accedere ai modelli facendo clic con il pulsante destro del mouse sul progetto R e selezionando **Aggiungi > Nuovo elemento...**, selezionando **Progetto > Aggiungi nuovo elemento...** o usando **File > Nuovo > File...** e selezionando la scheda **R**. Il modo migliore per esplorare i modelli è semplicemente creare un nuovo progetto e inserirvi file di ogni tipo.

> [!Note]
> I comandi **Aggiungi > Nuovo elemento...** visualizzano anche tipi di file generici non elencati nella tabella, mentre con **File > Nuovo > File...** tali tipi si trovano nella scheda **Generale**.

| Tipo di file | Descrizione |
| --- | --- |
| Script R | Un file di testo che contiene gli stessi comandi che è possibile immettere nella riga di comando R. |
| R Markdown | File contenente un documento [R Markdown](rmarkdown-with-r-in-visual-studio.md). |
| Impostazioni R | File che contiene le impostazioni applicazione R. | 
| Documentazione di R | File di documentazione di R generico che contiene solo i campi nome, alias e titolo. |
| Documentazione di R (funzione) | File di documentazione di R contenente molti campi con commenti di descrizione di una funzione. |
| Documentazione di R (set di dati) | File di documentazione di R contenente molti campi con commenti di descrizione di un set di dati. |
| Query SQL | File `.sql` vuoto. Vedere [SQL Server integration](integrating-sql-server-with-r.md) (Integrazione con SQL Server). |
| Stored procedure con R | File R con una query SQL figlio e un file modello di stored procedure figlio. Vedere [SQL Server integration](integrating-sql-server-with-r.md) (Integrazione con SQL Server). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Usare più tipi di progetto in Visual Studio

Le soluzioni di Visual Studio rappresentano un modo pratico per raccogliere e gestire progetti correlati in un'unica posizione logica, consentendo un'organizzazione efficiente del codice e semplificando la collaborazione all'interno del team.

Nell'esempio seguente la soluzione contiene un progetto R con un modello compilato tramite R e Azure Machine Learning, un progetto Python/scikit-learn, un progetto C++ contenente moduli per un processo di calcolo intensivo, un progetto SQL per la gestione dei dati e un progetto Python/Bottle per il sito Web in cui viene pubblicato il risultato:

![Esplora soluzioni di Visual Studio con più progetti correlati in una soluzione](media/projects-polyglot.png)

Il progetto evidenziato in grassetto è il progetto di "avvio" per la soluzione. Per cambiarlo, fare clic con il pulsante destro del mouse su un altro progetto e selezionare **Imposta come progetto di avvio**.

> [!Note]
> Al momento, a differenza di quanto avviene con Python (vedere [Creazione di un'estensione C++ per Python](../python/working-with-c-cpp-python-in-visual-studio.md)) non esiste alcuna integrazione esplicita tra R e i linguaggi C#/C++.  Sono tuttavia disponibili librerie che consentono di creare punti di comunicazione tra R e i linguaggi C# e C++.

Per altre informazioni sulla gestione di progetti e soluzioni in generale, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
