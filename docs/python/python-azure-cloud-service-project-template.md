---
title: Modello di progetto servizio cloud di Azure per Python | Microsoft Docs
description: Panoramica del modello di Visual Studio per servizi cloud di Azure, scritto in Python, tra cui la distribuzione dei ruoli, le dipendenze e la risoluzione dei problemi.
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
- azure
ms.openlocfilehash: b8e12d8823d3246da7c607ca63c056d1927b97d0
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="azure-cloud-service-projects-for-python"></a>Progetti servizio cloud di Azure per Python

Visual Studio include modelli per iniziare rapidamente a creare servizi cloud di Microsoft Azure con Python.

Un [servizio cloud](http://go.microsoft.com/fwlink/?LinkId=306052) è costituito da un numero qualsiasi di *ruoli di lavoro* e *ruoli Web*, ognuno dei quali esegue un'attività distinta dal punto di vista concettuale, ma che può essere replicata separatamente in macchine virtuali a seconda delle esigenze di ridimensionamento. I ruoli Web offrono funzionalità di hosting per applicazioni Web front-end. Per quel che riguarda Python, per scrivere tale applicazione, supportata dal [modello Progetto Web](python-web-application-project-templates.md), è possibile usare qualsiasi framework Web che supporta WSGI. I ruoli di lavoro sono destinati a processi a esecuzione prolungata che non interagiscono direttamente con gli utenti. Essi usano in genere le librerie di [dati](http://go.microsoft.com/fwlink/?LinkId=401571) e [servizi app](http://go.microsoft.com/fwlink/?LinkId=401572), che è possibile installare con [`pip install azure`](http://pypi.org/project/azure).

Questo articolo contiene informazioni dettagliate sul modello di progetto e su altre opzioni di supporto in Visual Studio 2017 (le versioni precedenti sono simili, ma presentano alcune differenze). Per altre informazioni sull'uso di Azure da Python, visitare il [Centro per sviluppatori Python di Azure](http://go.microsoft.com/fwlink/?linkid=254360).

## <a name="create-a-project"></a>Creare un progetto

1. Installare [Azure .NET SDK per Visual Studio](https://www.visualstudio.com/vs/azure-tools/), che è necessario per usare il modello servizio cloud.
1. In Visual Studio selezionare **File > Nuovo > Progetto**, cercare "Azure Python" e quindi selezionare **Servizio cloud di Azure** nell'elenco:

    ![Modello Progetto servizio cloud di Azure per Python](media/template-azure-cloud-project.png)

1. Selezionare uno o più ruoli da includere. I progetti servizio cloud possono combinare ruoli scritti in linguaggi diversi, di conseguenza è possibile scrivere facilmente le singole parti dell'applicazione nel linguaggio più appropriato. Per aggiungere nuovi ruoli al progetto dopo aver completato questa finestra di dialogo, fare clic con il pulsante destro del mouse su **Ruoli** in Esplora soluzioni e selezionare uno degli elementi in **Aggiungi**.

    ![Aggiunta di ruoli nel modello Progetto servizio cloud di Azure](media/template-azure-cloud-service-project-wizard.png)

1. Via via che vengono creati i singoli progetti ruolo, potrebbe essere richiesta l'installazione di altri pacchetti Python, ad esempio Django, Bottle o Flask, se è stato selezionato un ruolo che usa uno di tali framework.

1. Dopo aver aggiunto un nuovo ruolo al progetto, vengono visualizzate alcune istruzioni di configurazione. In genere non è necessario modificare la configurazione, ma può essere utile per la futura personalizzazione dei progetti. Si noti che, quando si aggiungono più ruoli contemporaneamente, rimangono aperte solo le istruzioni relative all'ultimo ruolo. Le istruzioni e i suggerimenti per la risoluzione dei problemi relativi ad altri ruoli sono disponibili nei rispettivi file `readme.mht`, inclusi nella radice del ruolo o nella cartella `bin`.

1. La cartella `bin` di un progetto contiene anche uno o due script di PowerShell usati per la configurazione della macchina virtuale remota, tra cui quello di installazione di Python, eventuali file [requirements.txt](#dependencies) presenti nel progetto e quello per l'eventuale configurazione di IIS. È possibile modificare questi file a seconda della distribuzione, anche se le opzioni più comuni possono essere gestite in altri modi. Vedere [Configurazione della distribuzione del ruolo](#configuring-role-deployment) più avanti. È consigliabile non rimuovere questi file, perché se non sono disponibili viene usato uno script di configurazione legacy.

    ![File di supporto del ruolo di lavoro](media/template-azure-cloud-service-worker-role-support-files.png)

    Per aggiungere questi script di configurazione a un nuovo progetto, fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi > Nuovo elemento** e selezionare **File di supporto del ruolo Web** o **File di supporto del ruolo di lavoro**.

## <a name="configuring-role-deployment"></a>Configurazione della distribuzione del ruolo

Gli script di PowerShell nella cartella `bin` di un progetto di ruolo consentono di controllare la distribuzione di tale ruolo e possono essere modificati per personalizzare la configurazione:

- `ConfigureCloudService.ps1` viene usato in genere per ruoli Web e di lavoro per installare e configurare le dipendenze e per impostare la versione di Python.
- `LaunchWorker.ps1` viene usato solo per i ruoli di lavoro per modificare il comportamento di avvio, nonché per aggiungere argomenti della riga di comando o variabili di ambiente.

Entrambi i file contengono istruzioni per la personalizzazione. Per installare la propria versione di Python, aggiungere un'altra attività al file `ServiceDefinition.csdef` del progetto di servizio cloud principale e impostare la variabile `PYTHON` sul percorso installato di `python.exe` (o equivalente). Quando è impostato `PYTHON`, Python non viene installato da NuGet.

Per eseguire altre operazioni di configurazione, è possibile procedere come segue:

1. Installare i pacchetti con `pip` aggiornando il file `requirements.txt` nella directory radice del progetto. Lo script `ConfigureCloudService.ps1` installa questo file durante la distribuzione.
1. Impostare le variabili di ambiente modificando il file `web.config` (ruoli web) o la sezione `Runtime` del file `ServiceDefinition.csdef` (ruoli di lavoro).
1. Specificare lo script e gli argomenti da usare per un ruolo di lavoro modificando la riga di comando nella sezione `Runtime/EntryPoint` del file `ServiceDefinitions.csdef`.
1. Impostare lo script principale del gestore per un ruolo Web tramite il file `web.config`.

## <a name="testing-role-deployment"></a>Test della distribuzione del ruolo

Durante la scrittura dei ruoli è possibile testare il progetto cloud in locale usando l'emulatore del servizio cloud. L'emulatore è incluso in Azure SDK Tools e rappresenta una versione limitata dell'ambiente usato quando il servizio cloud viene pubblicato in Azure.

Per avviare l'emulatore, assicurarsi innanzitutto che il progetto cloud corrisponda al progetto di avvio nella soluzione. A questo scopo, fare clic con il pulsante destro del mouse e scegliere **Imposta come progetto di avvio**. Selezionare quindi **Debug > Avvia debug** (F5) o **Debug > Avvia senza eseguire il debug** (CTRL+F5).

Si noti che, a causa delle limitazioni previste nell'emulatore, non è possibile eseguire il debug del codice Python. È quindi consigliabile eseguire il debug dei ruoli eseguendoli in modo indipendente e usare successivamente l'emulatore per il test di integrazione prima della pubblicazione.

## <a name="deploying-a-role"></a>Distribuzione di un ruolo

Per aprire la **Pubblicazione guidata**, selezionare il progetto di ruolo in Esplora soluzioni e scegliere **Compila > Pubblica** nel menu principale oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

Il processo di pubblicazione prevede due fasi. Nella prima fase Visual Studio crea un singolo pacchetto contenente tutti i ruoli per il servizio cloud. Questo pacchetto corrisponde agli elementi distribuiti in Azure e consente di inizializzare una o più macchine virtuali per ogni ruolo e di distribuire l'origine.

Via via che vengono attivate le singole macchine virtuali, esegue lo script `ConfigureCloudService.ps1` e installa le eventuali dipendenze. Per impostazione predefinita, questo script installa una versione recente di Python da [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) ed eventuali pacchetti specificati in un file `requirements.txt`.

Al termine i ruoli di lavoro eseguono `LaunchWorker.ps1`, che avvia l'esecuzione dello script Python. I ruoli Web inizializzano IIS e avviano la gestione delle richieste Web.

## <a name="dependencies"></a>Dipendenze

Per i servizi cloud lo script `ConfigureCloudService.ps1` usa `pip` per installare un set di dipendenze di Python, che devono essere specificate in un file denominato `requirements.txt` (personalizzabile modificando `ConfigureCloudService.ps1`). Il file viene eseguito con `pip install -r requirements.txt` durante l'inizializzazione.

Si noti che le istanze del servizio cloud non includono compilatori C, di conseguenza tutte le librerie con estensioni C devono specificare file binari precompilati.

pip e le relative dipendenze, oltre ai pacchetti in `requirements.txt`, vengono scaricati automaticamente e conteggiati ai fini dell'utilizzo della larghezza di banda addebitabile. Vedere [Gestione dei pacchetti necessari](managing-required-packages-with-requirements-txt.md) per informazioni dettagliate sulla gestione dei file `requirements.txt`.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se il ruolo Web o di lavoro non funziona correttamente dopo la distribuzione, verificare che:

- Il progetto Python includa una cartella bin\ con (almeno):

  - `ConfigureCloudService.ps1`
  - `LaunchWorker.ps1` (per i ruoli di lavoro)
  - `ps.cmd`

- Il progetto Python include un file `requirements.txt` che elenca tutte le dipendenze (o in alternativa, una raccolta di file wheel).
- Abilitare Desktop remoto nel servizio cloud e analizzare i file di log.
- I log relativi a `ConfigureCloudService.ps1` e `LaunchWorker.ps1` sono archiviati nella cartella `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` del computer remoto.
- È possibile che i ruoli Web scrivano log aggiuntivi in un percorso configurato in `web.config`, ovvero il percorso nella voce appSetting `WSGI_LOG`. Funzionerà per la maggior parte anche la registrazione IIS normale o FastCGI.
- Al momento per visualizzare l'output o gli errori visualizzati dal ruolo di lavoro Python o output è possibile usare solo il file `LaunchWorker.ps1.log`.