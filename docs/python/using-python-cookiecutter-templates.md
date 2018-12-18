---
title: Estensione CookieCutter per Python in Visual Studio | Microsoft Docs
description: Visual Studio supporta l'estensione grafica Cookiecutter per individuare modelli per il codice Python e creare progetti da tali modelli.
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 96590d2856d14b8c74a9c30f73e3a933cf572164
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-the-cookiecutter-extension"></a>Uso dell'estensione Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) offre un'interfaccia utente grafica per individuare modelli, opzioni del modello di input e creare progetti e file. Questa estensione è inclusa in Visual Studio 2017 e può essere installata separatamente nelle versioni precedenti di Visual Studio.

Cookiecutter richiede Python 3.3 o versione successiva (a 32 bit o a 64 bit) o Anaconda 3 4.2 o versione successiva (a 32 bit o a 64 bit). Se non è disponibile un interprete Python appropriato, Visual Studio visualizza un avviso. Se si installa un interprete Python mentre Visual Studio è in esecuzione, fare clic sul pulsante Home sulla barra degli strumenti di Cookiecutter per rilevare l'interprete appena installato. (Vedere [Ambienti Python](managing-python-environments-in-visual-studio.md) per altre informazioni sugli ambienti in generale.)

Dopo aver eseguito l'installazione, selezionare **Visualizza > Cookiecutter Explorer** per aprire la finestra di questo strumento:

![Finestra principale di Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Flusso di lavoro di Cookiecutter

Il processo di utilizzo di Cookiecutter include la ricerca e selezione di un modello, la clonazione del modello nel computer locale, l'impostazione delle opzioni e quindi la creazione di codice dal modello, come descritto nelle sezioni che seguono.

### <a name="browsing-templates"></a>Selezione dei modelli

Nella home page di Cookiecutter viene visualizzato un elenco di modelli tra cui scegliere, organizzati nei gruppi seguenti:

| Gruppo | Descrizione |
| --- | --- |
| Installed (Installati) | Modelli installati nel computer locale. Quando si usa un modello online, il repository corrispondente viene clonato automaticamente in una sottocartella di `~/.cookiecutters`. È possibile eliminare un modello installato selezionato premendo **CANC**. |
| Recommended (Consigliati) | Modelli caricati dal feed consigliato. Il feed predefinito è a cura di Microsoft. Vedere [Opzioni di Cookiecutter](#cookiecutter-options) di seguito per altri dettagli sulla personalizzazione del feed. |
| GitHub | Risultati di ricerca da GitHub per la parola chiave cookiecutter. I risultati da GitHub vengono impaginati. Se sono disponibili altri risultati, alla fine dell'elenco viene visualizzata l'opzione **Load More** (Carica altro). |
| Custom (Personalizzati) | Quando si immette una posizione personalizzata nella casella di ricerca, i risultati vengono visualizzati in questo gruppo. È possibile digitare il percorso completo del repository GitHub o il percorso completo di una cartella nel disco locale. |

### <a name="cloning"></a>Clonazione

Quando si seleziona un modello e si fa clic su **Next** (Avanti), Cookiecutter crea una copia locale su cui lavorare.

Se si seleziona un modello dai gruppi **Recommended** (Consigliati) o **GitHub** oppure si immette un URL personalizzato nella casella di ricerca e si seleziona tale modello, questo viene clonato e installato nel computer locale. Se tale modello è stato installato in una sessione precedente di Visual Studio, questo verrà eliminato automaticamente e verrà clonata la versione più recente.

Se si seleziona un modello dai gruppi **Installed** (Installati) oppure si immette un percorso di cartella personalizzato nella casella di ricerca e si seleziona tale modello, Visual Studio carica il modello senza clonarlo.

> [!Important]
> I modelli di Cookiecutter vengono clonati in un'unica cartella `~/.cookiecutters`. Il nome di ogni sottocartella viene definito in base al nome del repository GIT, che non include il nome utente di GitHub. Possono verificarsi conflitti se si clonano modelli diversi con lo stesso nome provenienti da autori diversi. In questo caso, Cookiecutter impedisce di sovrascrivere il modello esistente con un modello diverso con lo stesso nome. Per installare il nuovo modello, è prima necessario eliminare quello esistente.

### <a name="setting-template-options"></a>Impostazione delle opzioni per i modelli

Dopo aver installato il modello in locale, Cookiecutter visualizza una pagina di opzioni in cui è possibile specificare la posizione in cui Cookiecutter deve generare i file, oltre ad altre opzioni:

![Pagina delle opzioni di Cookiecutter](media/cookiecutter-template-options.png)

Ogni modello di Cookiecutter definisce un set proprio di opzioni e specifica un valore predefinito per ognuna (visualizzato come testo suggerito in ogni campo di immissione). Un valore predefinito può essere un frammento di codice, spesso quando è un valore dinamico che usa altre opzioni. 

È possibile personalizzare i valori predefiniti per opzioni specifiche con un file di configurazione dell'utente. Quando l'estensione Cookiecutter rileva un file di configurazione dell'utente, sovrascrive i valori predefiniti del modello con i valori predefiniti della configurazione dell'utente. Questo comportamento è trattato nella sezione [User Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) (Configurazione dell'utente) della documentazione di Cookiecutter.

Se il modello specifica attività specifiche di Visual Studio da eseguire dopo la generazione del codice, viene visualizzata un'ulteriore opzione **Run additional tasks on completion** (Esegui attività aggiuntive al completamento) che consente di rifiutare esplicitamente tali attività. Le attività vengono usate più comunemente per aprire un Web browser, aprire file nell'editor, installare dipendenze e così via.

### <a name="create"></a>Crea

Dopo aver impostato le opzioni, selezionare **Create** (Crea) per generare il codice. Se la cartella di output non è vuota viene visualizzato un messaggio di avviso. Se si ha familiarità con l'output del modello e non è un problema sovrascrivere file, è possibile ignorare l'avviso. In caso contrario, selezionare **Cancel** (Annulla), specificare una cartella vuota e quindi copiare manualmente i file creati nella cartella di output non vuota.

Dopo aver creato correttamente i file, Cookiecutter offre un'opzione per aprire i file in **Esplora soluzioni**:

![Comando per aprire Esplora soluzioni da Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opzioni di Cookiecutter

Le opzioni di Cookiecutter sono disponibili tramite **Tools > Options > Cookiecutter** (Strumenti > Opzioni > Cookiecutter):

![Opzioni di Cookiecutter](media/cookiecutter-tools-options.png)

| Opzione | Descrizione |
| --- | --- |
| Recommended Feed URL (URL feed consigliato) | Posizione del feed dei modelli consigliato. Può essere un URL o un percorso di un file locale. Lasciare l'URL vuoto per usare il feed predefinito a cura di Microsoft. Il feed offre un semplice elenco di percorsi di modelli, separati da caratteri di nuova riga. Per richiedere modifiche al feed curato, effettuare una richiesta pull per l'[origine su GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| Show Help (Mostra Guida) | Controlla la visibilità della barra informazioni della Guida nella parte superiore della finestra di Cookiecutter. |

## <a name="optimizing-cookiecutter-templates-for-visual-studio"></a>Ottimizzazione dei modelli di Cookiecutter per Visual Studio

Per informazioni di base sulla creazione di un modello di Cookiecutter, vedere la [documentazione di Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). L'estensione Cookiecutter per Visual Studio supporta modelli creati per Cookiecutter versione 1.4.

Il rendering predefinito delle variabili di un modello dipende dal tipo di dati (stringa o elenco):

- Stringa: etichetta del nome della variabile, casella di testo per l'immissione del valore e filigrana che mostra il valore predefinito. Descrizione comando per la casella di testo che mostra il valore predefinito.
- Elenco: etichetta del nome della variabile, casella combinata per la sezione di un valore. Descrizione comando per la casella combinata che mostra il valore predefinito.

È possibile migliorare il rendering specificando metadati aggiuntivi nel file `cookiecutter.json` specifico per Visual Studio (ignorato dall'interfaccia della riga di comando di Cookiecutter). Tutte le proprietà sono facoltative:

| Proprietà | Descrizione |
| --- | --- |
| Label | Specifica ciò che viene visualizzato sopra l'editor per la variabile, anziché il nome della variabile. |
| Descrizione | Specifica che la descrizione comando compare per il controllo di modifica, anziché per il valore predefinito per la variabile. |
| URL | Cambia l'etichetta in collegamento ipertestuale, con una descrizione comando che visualizza l'URL. Facendo clic sul collegamento ipertestuale, il browser predefinito dell'utente verrà aperto su tale URL. |
| Selector | Consente la personalizzazione dell'editor per una variabile. Sono attualmente supportati i selettori seguenti:<ul><li>`string`: casella di testo standard, impostazione predefinita per le stringhe.</li><li>`list`: casella combinata standard, impostazione predefinita per gli elenchi.</li><li>`yesno`: casella combinata per scegliere tra `y` e `n`, per le stringhe.</li><li>`odbcConnection`: casella di testo con un pulsante "..." che consente di visualizzare una finestra di dialogo per la connessione a un database.</li></ul> |

Esempio:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="running-visual-studio-tasks"></a>Esecuzione di attività di Visual Studio

Cookiecutter include una funzionalità denominata *hook di post-generazione* che consente di eseguire codice arbitrario Python dopo la generazione dei file. Sebbene flessibile, questa funzionalità non consente di accedere facilmente a Visual Studio.

Ad esempio, potrebbe essere necessario aprire un file nell'editor di Visual Studio o nel Web browser oppure attivare l'interfaccia utente di Visual Studio che richiede all'utente di creare un ambiente virtuale e installare i requisiti del pacchetto.

Per consentire a questi scenari, Visual Studio cerca i metadati estesi in `cookiecutter.json` che descrivono i comandi da eseguire dopo l'apertura dei file generati in Esplora soluzioni o dopo l'aggiunta dei file a un progetto esistente. L'utente può comunque rifiutare esplicitamente di eseguire le attività deselezionando **Eseguire altre attività al completamento** nelle opzioni del modello.

Esempio:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

I comandi vengono specificati in base al nome ed è necessario usare il nome inglese non localizzato anche nelle installazioni localizzate di Visual Studio. È possibile testare e individuare i nomi dei comandi nella finestra di comando di Visual Studio.

Per passare un solo argomento, specificarlo come una stringa come nell'esempio precedente.

Se non è necessario passare un argomento, lasciare una stringa vuota oppure ometterlo dal codice JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Usare una matrice per più argomenti. Per le opzioni, suddividere l'opzione e il relativo valore in argomenti separati, usando correttamente le virgolette. Ad esempio:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Gli argomenti possono fare riferimento ad altre variabili di Cookiecutter. Negli esempi precedenti, la variabile interna `_output_folder_path` viene usata per formare un percorso assoluto per i file generati.

Si noti che il comando `Python.InstallProjectRequirements` funziona solo per l'aggiunta di file a un progetto esistente, perché esiste una limitazione a causa della quale il comando viene elaborato dal progetto Python in Esplora soluzioni e non esiste alcun progetto che possa ricevere il messaggio in Esplora soluzioni - Visualizzazione cartelle. Si spera di superare questa limitazione in una versione futura, con un migliore supporto della visualizzazione delle cartelle in generale.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="error-loading-template"></a>Errore durante il caricamento del modello

Alcuni modelli potrebbero usare tipi di dati non validi, ad esempio il tipo booleano, nel codice `cookiecutter.json`. Segnalare tali istanze di report all'autore del modello selezionando il collegamento **Problemi** nel riquadro delle informazioni del modello.

### <a name="hook-script-failed"></a>Script hook non riuscito

Alcuni modelli possono usare script di post-generazione non compatibili con l'interfaccia utente di Cookiecutter. Ad esempio, gli script che richiedono input all'utente hanno esito negativo perché non è disponibile una console terminale.

### <a name="hook-script-not-supported-on-windows"></a>Script hook non supportato in Windows

Se lo script di post-generazione è `.sh`, potrebbe non essere associato a un'applicazione nel computer Windows in uso. È possibile che venga visualizzata una finestra di dialogo di Windows che richiede di trovare un'applicazione compatibile in Windows Store.

### <a name="templates-with-known-issues"></a>Modelli con problemi noti

Errori di clonazione:

- **wildfish/cookiecutter-django-crud** (carattere non valido `|` nel nome della sottocartella)
- **cookiecutter-pyvanguard** (carattere non valido `|` nel nome della sottocartella)

Errori di caricamento:

- **chrisdev/wagtail-cookiecutter-foundation** (uso di un tipo booleano in cookiecutter.json)
- **quintoandar/cookiecutter-android** (nessun cartella per il modello)

Errori di esecuzione:

- **iknite/cookiecutter-ansible-role** (lo script hook di post-generazione richiede input nella console)
- **benregn/cookiecutter-django-ansible** (errore Jinja)

Uso di Bash (non irreversibile):

- **openstack-dev/cookiecutter**
