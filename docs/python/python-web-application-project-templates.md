---
title: Modelli di applicazione Web per Python in Visual Studio | Microsoft Docs
description: Panoramica dei modelli di Visual Studio per applicazioni Web scritte con Python mediante i framework Bottle, Flask e Django, incluse le configurazioni di debug e la pubblicazione in Servizio app di Azure.
ms.custom: 
ms.date: 07/13/2017
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
ms.openlocfilehash: 49b27fcc972cf8b0bb0411f5ee54ea611cdd4d75
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="python-web-application-project-templates"></a>Modelli di progetto applicazione Web di Python

Python in Visual Studio supporta lo sviluppo di progetti Web nei framework Bottle, Flask e Django, usando modelli di progetto e un'utilità di avvio del debug che può essere configurata in modo da gestire diversi framework. È anche possibile usare il modello generico **Progetto Web** per altri framework, come ad esempio Pyramid.

Visual Studio non include i framework, che devono essere installati separatamente. A tale scopo, fare clic con il pulsante destro del mouse sul progetto e scegliere **Python > Install/upgrade framework** (Installa/Aggiorna framework).

Un progetto creato da un modello (accessibile da **File > Nuovo > Progetto**), quando viene eseguito avvia un server Web con una porta locale selezionata in modo causale, apre il browser predefinito durante il debug e consente la pubblicazione diretta in Microsoft Azure.

![Nuovi modelli di progetto Web](media/template-web-new-project.png)

I modelli Bottle, Flask e Django includono un sito di base contenente alcune pagine e file statici. Questo codice è sufficiente per avviare ed eseguire il debug del server in locale (in cui è necessario ottenere alcune impostazioni dall'ambiente) e per la distribuzione in Microsoft Azure (in cui è necessario specificare un oggetto [app WSGI](http://www.python.org/dev/peps/pep-3333/)).

Quando si crea un progetto da un modello specifico del framework, viene visualizzata una finestra di dialogo che consente di installare i pacchetti necessari con pip. Per i progetti Web è inoltre consigliabile usare un [ambiente virtuale](managing-python-environments-in-visual-studio.md#global-and-virtual-environments), in modo che durante la pubblicazione del sito Web vengano incluse le dipendenze corrette:

![Finestra di dialogo in cui è possibile installare i pacchetti necessari per un modello di progetto](media/template-web-requirements-txt-wizard.png)

Durante la distribuzione nel servizio app di Microsoft Azure, selezionare una versione di Python come [estensione sito](https://aka.ms/PythonOnAppService) e installare manualmente i pacchetti. Dal momento poi che il servizio app di Azure **non** installa automaticamente i pacchetti da un file `requirements.txt` quando viene distribuito da Visual Studio, attenersi ai dettagli di configurazione illustrati in [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

I servizi cloud di Microsoft Azure invece *supportano* il file `requirements.txt`. Per dettagli, vedere [Progetti servizio cloud di Azure per Python](python-azure-cloud-service-project-template.md).

## <a name="debugging"></a>Debug

Quando si avvia un progetto Web per il debug, Visual Studio avvia il server Web in locale e apre il browser predefinito usando l'indirizzo e la porta specificati. Per specificare altre opzioni, fare clic con il pulsante destro del mouse sul progetto, scegliere **Proprietà** e selezionare la scheda **Utilità di avvio Web**:

  ![Proprietà dell'utilità di Web per il modello Web generico](media/template-web-launcher-properties.png)

Nel gruppo **Debug** specificare le proprietà seguenti:

- **Percorsi di ricerca**, **Argomenti dello script**, **Argomenti dell'interprete** e **Percorso dell'interprete**: queste opzioni sono uguali a quelle per il [debug normale](debugging-python-in-visual-studio.md)
- **URL di avvio**: specifica l'URL che viene aperto nel browser. Il valore predefinito è `localhost`.
- **Numero di porta**: porta da usare se non ne viene specificata nessuna nell'URL (Visual Studio ne seleziona una automaticamente per impostazione predefinita). Questa impostazione consente di eseguire l'override del valore predefinito della variabile di ambiente `SERVER_PORT`, usata dai modelli per configurare la porta su cui è in ascolto il server di debug locale.

Le proprietà nei gruppi **Comando esegui server** e **Comando debug server** (quest'ultimo illustrato nell'immagine) determinano la modalità di avvio del server Web. Con molti framework è richiesto l'uso di uno script esterno al progetto corrente, di conseguenza è possibile configurare qui lo script e passare il nome del modulo di avvio come parametro.

- **Comando**: può essere uno script Python (file `*.py`), un nome di modulo (come in `python.exe -m module_name`), o una singola riga di codice (come in `python.exe -c "code"`). Il valore nell'elenco a discesa indica il tipo da usare.
- **Argomenti**: questi argomenti vengono passati nella riga di comando dopo il comando.
- **Ambiente**: elenco delimitato da caratteri di nuova riga di coppie `NAME=VALUE` che specificano le variabili di ambiente. Queste variabili vengono impostate dopo tutte le proprietà che possono comportare la modifica dell'ambiente, ad esempio il numero di porta e i percorsi di ricerca, di conseguenza possono sovrascrivere tali valori.

Per specificare qualsiasi proprietà di progetto o variabile di ambiente, è possibile usare la sintassi MSBuild, ad esempio: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` è il percorso relativo del file di avvio, mentre `{StartupModule}` è il nome importabile del file di avvio. `$(SERVER_HOST)` e `$(SERVER_PORT)` sono variabili di ambiente normale che vengono impostate tramite le proprietà **URL di avvio** e **Numero di porta** automaticamente oppure tramite la proprietà **Ambiente**.

> [!Note]
> I valori in **Comando esegui server** vengono usati con il comando **Debug > Avvia server** oppure quando si preme CTRL+F5. I valori nel gruppo **Comando debug server** vengono usati con il comando **Debug > Avvia il server di debug** oppure quando si preme F5.

### <a name="sample-bottle-configuration"></a>Esempio di configurazione di Bottle

Il modello **Progetto Web Bottle** include codice boilerplate che esegue la configurazione necessaria. Un'app Bottle importata potrebbe però non includere questo codice. In questo caso, le impostazioni seguenti consentono di avviare l'app usando il modulo `bottle` installato:

- Gruppo **Comando esegui server**:
  - **Comando**: `bottle` (modulo)
  - **Argomenti**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Gruppo **Comando debug server**:
  - **Comando**: `bottle` (modulo)
  - **Argomenti**: `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

L'opzione `--reload` è sconsigliata quando si usa Visual Studio per il debug.

### <a name="sample-pyramid-configuration"></a>Esempio di configurazione di Pyramid

Per la creazione di app Pyramid è attualmente preferibile usare lo strumento da riga di comando `pcreate`. L'app creata può quindi essere importata usando il modello [Da codice Python esistente](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files). Successivamente, selezionare la personalizzazione **Progetto Web generico** per configurare le opzioni. In queste impostazioni si presuppone che Pyramid sia installato in un ambiente virtuale nel percorso `..\env`.

- Gruppo **Debug**:
  - **Porta server**: 6543 (o qualunque altra sia configurata nei file con estensione ini)

- Gruppo **Comando esegui server**:
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argomenti: `Production.ini`

- Gruppo **Comando debug server**:
    - Comando: `..\env\scripts\pserve-script.py` (script)
    - Argomenti: `Development.ini`

> [!Tip]
> È probabilmente necessario configurare la proprietà **Directory di lavoro** del progetto perché le app Pyramid si trovano in genere a un livello di directory inferiore rispetto alla parte superiore dell'albero di origine.

### <a name="other-configurations"></a>Altre configurazioni

Se si vogliono condividere impostazioni personalizzate per un altro framework oppure richiederne altre, aprire una [segnalazione in GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Pubblicazione nel servizio app di Azure

È possibile pubblicare nel servizio app di Azure in due modi. È innanzitutto possibile usare la distribuzione dal controllo del codice sorgente in modo analogo a quanto avviene per altri linguaggi, come descritto nella [documentazione di Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Per pubblicare direttamente da Visual Studio, fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**:

![Comando Pubblica nel menu di scelta rapida di un progetto](media/template-web-publish-command.png)

Dopo aver selezionato il comando, verrà visualizzata una procedura guidata per la creazione di un sito Web o l'importazione delle impostazioni di pubblicazione, la visualizzazione dell'anteprima dei file modificati e la pubblicazione in un server remoto.

Quando si crea un sito nel servizio app, è necessario installare Python e tutti i pacchetti da cui dipende il sito. È possibile pubblicare prima il sito, che però non verrà eseguito fino a quando non si configura Python.

Per installare Python nel servizio app, è consigliabile usare le [estensioni sito](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Queste estensioni sono copie di [versioni ufficiali](https://www.python.org) di Python, ottimizzate e appositamente preparate per il servizio app di Azure.

Un'estensione del sito può essere distribuita attraverso il [portale di Azure](https://portal.azure.com/). Selezionare il pannello **Strumenti di sviluppo > Estensioni** per il servizio app, selezionare **Aggiungi** e scorrere l'elenco per trovare gli elementi di Python:

![Aggiungere un'estensione sito nel portale di Azure](media/template-web-site-extensions.png)

Se si usano modelli di distribuzione JSON, è possibile specificare l'estensione sito come risorsa del sito:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

È infine possibile accedere tramite la [console di sviluppo](https://github.com/projectkudu/kudu/wiki/Kudu-console) e installare un'estensione sito da tale posizione.

Per installare i pacchetti, è al momento consigliabile usare la console di sviluppo dopo aver installato l'estensione sito e aver eseguito pip direttamente. È importante usare il percorso completo di Python per evitare di usare quello errato. Non è inoltre in genere necessario usare un ambiente virtuale. Ad esempio:

```command
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Quando viene distribuito nel servizio app di Azure, per l'esecuzione del sito si usa Microsoft IIS. Per consentire l'uso del sito con IIS, è necessario aggiungere almeno un file `web.config`. Sono disponibili modelli per alcune destinazioni di distribuzione comuni facilmente modificabili per adattarli ad altri utilizzi. Per accedervi, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi > Nuovo elemento** (vedere la finestra di dialogo seguente). Per informazioni sulle impostazioni di configurazione disponibili, vedere la [guida di riferimento per la configurazione di IIS](https://www.iis.net/configreference).

![Modelli di elemento di Azure](media/template-web-azure-items.png)

Gli elementi disponibili includono:

- web.config di Azure (FastCGI): consente di aggiungere un file `web.config` per i casi in cui l'app fornisce un oggetto [WSGI](https://wsgi.readthedocs.io/en/latest/) per gestire le connessioni in ingresso.
- web.config di Azure (HttpPlatformHandler): consente di aggiungere un file `web.config` per i casi in cui l'app usa un socket per rimanere in ascolto delle connessioni in ingresso.
- web.config di file statici di Azure: se è disponibile uno dei file `web.config` indicati in precedenza, aggiungerlo a una sottodirectory per evitare che venga gestito dall'app.
- web.config di debug remoto di Azure: consente di aggiungere i file necessari per il debug remoto tramite WebSocket.
- File di supporto del ruolo Web: contiene gli script di distribuzione predefiniti per i ruoli Web del servizio cloud.
- File di supporto del ruolo di lavoro: contiene gli script di distribuzione e di avvio predefiniti per i ruoli di lavoro del servizio cloud.

Se si aggiunge il modello `web.config` di debug al progetto e si intende usare il debug remoto di Python, è necessario pubblicare il sito nella configurazione "Debug". Questa impostazione è diversa rispetto alla configurazione attiva corrente della soluzione ed è sempre contraddistinta dal valore predefinito "Versione". Per modificarla, aprire la scheda **Impostazioni** e usare la casella combinata **Configurazione** nella pubblicazione guidata. Per altre informazioni sulla creazione e la distribuzione in app Web di Azure, vedere la [documentazione di Azure](https://azure.microsoft.com/develop/python/):

![Modifica della configurazione di pubblicazione](media/template-web-publish-config.png)

Il comando **Converti in progetto servizio cloud di Microsoft Azure** (immagine seguente) consente di aggiungere un progetto di servizio cloud alla soluzione. Questo progetto include le impostazioni di distribuzione e la configurazione per i servizi e le macchine virtuali da usare. Usare il comando **Pubblica** nel progetto cloud per eseguire la distribuzione nei servizi cloud. Con il comando **Pubblica** nel progetto Python la distribuzione viene ancora eseguita nei siti Web. Per altre informazioni, vedere [Progetti servizio cloud di Azure per Python](python-azure-cloud-service-project-template.md).

![Comando Converti in progetto servizio cloud di Microsoft Azure](media/template-web-convert-menu.png)
