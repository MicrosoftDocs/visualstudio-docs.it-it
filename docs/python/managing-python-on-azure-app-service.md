---
title: Installazione di interpreti e librerie di Python in Servizio app di Azure | Microsoft Docs
description: Come installare un interprete e librerie di Python in Servizio app di Azure e configurazione delle applicazioni Web per fare riferimento correttamente a tale interprete.
ms.custom: 
ms.date: 09/13/2017
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
- azure
ms.openlocfilehash: bc9317615edbf49e35aa0ac3d2ff079beab20df5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="managing-python-on-azure-app-service"></a>Gestione di Python nel servizio app di Azure

Il [servizio app di Azure](https://azure.microsoft.com/services/app-service/) è un'offerta di tipo piattaforma distribuita come servizio per le app Web, siano esse siti accessibili tramite un browser, API REST usate dai client o elaborazioni attivate da eventi. Il servizio app supporta pienamente l'uso di Python per implementare le app.

Il supporto di Python personalizzabile nel servizio app di Azure viene offerto come un *set di estensioni del sito* del servizio app, ognuna contenente una versione specifica del runtime di Python. È quindi possibile installare tutti i pacchetti desiderati direttamente in tale ambiente, come descritto in questo argomento. Personalizzando l'ambiente nel servizio app stesso, non è necessario gestire i pacchetti nei progetti di app Web o caricarli con il codice dell'app.

> [!Tip]
> Anche se il servizio app per impostazione predefinita include Python 2.7 e Python 3.4 installati nelle cartelle radice nel server, non è possibile personalizzare o installare i pacchetti in questi ambienti, né dipendere dalla loro presenza. È invece necessario affidarsi a un'estensione del sito sotto il proprio controllo, come descritto in questo argomento.

> [!Important]
> Le procedure descritte di seguito sono soggette a modifiche, in particolare per apportare miglioramenti. Le modifiche sono annunciate nel [blog Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/) (Progettazione Python in Microsoft).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Scelta di una versione di Python tramite il portale di Azure

1. Creare un servizio app per l'app Web nel portale di Azure.
1. Nella pagina del servizio app scorrere fino alla sezione **Strumenti di sviluppo**, selezionare **Estensioni** e quindi selezionare **Aggiungi**.
1. Scorrere verso il basso nell'elenco fino all'estensione che contiene la versione di Python desiderata:

    ![Portale di Azure con estensioni di Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Se è necessaria una versione precedente di Python e non è inclusa nell'elenco delle estensioni del sito, è comunque possibile installarla tramite Azure Resource Manager, come descritto nella sezione successiva.

1. Selezionare l'estensione, accettare le condizioni legali e quindi selezionare **OK**.
1. Nel portale viene visualizzata una notifica al termine dell'installazione.

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Scelta di una versione di Python tramite Azure Resource Manager

Se si distribuisce un servizio app con un modello di Azure Resource Manager, aggiungere l'estensione del sito come risorsa. L'estensione viene visualizzata come risorsa annidata con il tipo `siteextensions` e il nome da [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Ad esempio, dopo l'aggiunta di un riferimento a `python361x64` (Python 3.6.1 x64), il modello potrebbe essere simile al seguente (alcune proprietà sono state omesse):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="setting-webconfig-to-point-to-the-python-interpreter"></a>Impostazione di web.config per fare riferimento all'interprete di Python

Dopo aver installato l'estensione del sito (tramite il portale o un modello di Azure Resource Manager), è necessario configurare il file `web.config` dell'app in modo che faccia riferimento all'interprete di Python. Il file `web.config` indica al server Web IIS (7+) in esecuzione nel servizio app come gestire le richieste di Python tramite FastCGI o HttpPlatform.

Per iniziare, trovare il percorso completo del file `python.exe` dell'estensione del sito, quindi creare e modificare il file `web.config` appropriato.

### <a name="finding-the-path-to-pythonexe"></a>Ricerca del percorso di python.exe

Un'estensione del sito di Python viene installata nel server in `d:\home` in una cartella appropriata per la versione e l'architettura di Python, tranne che in alcune versioni precedenti. Ad esempio, Python 3.6.1 x64 viene installato in `d:\home\python361x64`. Il percorso completo dell'interprete Python è quindi `d:\home\python361x64\python.exe`.

Per visualizzare il percorso specifico nel servizio app, selezionare **Estensioni** nella pagina del servizio app e quindi selezionare l'estensione nell'elenco.

![Elenco delle estensioni nel servizio app di Azure](media/python-on-azure-extension-list.png)

Questa azione apre la pagina di descrizione dell'estensione contenente il percorso:

![Dettagli delle estensioni nel servizio app di Azure](media/python-on-azure-extension-detail.png)

In caso di difficoltà a visualizzare il percorso per l'estensione, è possibile trovarlo manualmente tramite la console:

1. Nella pagina del servizio App selezionare **Strumenti di sviluppo > Console**.
1. Immettere il comando `ls ../home` o `dir ..\home` per visualizzare le cartelle delle estensioni di primo livello, ad esempio `Python361x64`.
1. Immettere un comando come `ls ../home/python361x64` o `dir ..\home\python361x64` per verificare che contenga `python.exe` e altri file di interprete.

### <a name="configuring-the-fastcgi-handler"></a>Configurazione del gestore FastCGI

FastCGI è un'interfaccia che funziona a livello di richiesta. IIS riceve le connessioni in ingresso e inoltra ogni richiesta a un'app WSGI in esecuzione in uno o più processi Python persistenti. Il [pacchetto wfastcgi](https://pypi.io/project/wfastcgi) viene pre-installato e configurato con ogni estensione del sito Python, pertanto è possibile abilitarlo facilmente includendo il codice seguente in `web.config`, come illustrato di seguito per un'app Web basata sul framework Bottle. Si noti che i percorsi completi di `python.exe` e `wfastcgi.py` vengono inseriti nella chiave `PythonHandler`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Le `<appSettings>` definite di seguito sono disponibili come variabili di ambiente per l'app:

- Il valore per `PYTHONPATH` può essere esteso liberamente, ma deve includere la directory radice dell'app.
- `WSGI_HANDLER` deve puntare a un'app WSGI importabile dall'app.
- `WSGI_LOG` è facoltativo ma consigliato per il debug dell'app. 

Vedere [Pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) per altri dettagli sul contenuto di `web.config` per app Web Bottle, Flask e Django.

### <a name="configuring-the-httpplatform-handler"></a>Configurazione del gestore HttpPlatform

Il modulo HttpPlatform passa le connessioni socket direttamente a un processo di Python autonomo. Questo pass-through consente di eseguire qualsiasi server Web, ma richiede uno script di avvio che esegue un server Web locale. Specificare lo script nell'elemento `<httpPlatform>` di `web.config`, dove l'attributo `processPath` punta all'interprete Python dell'estensione del sito e l'attributo `arguments` punta allo script e a eventuali argomenti che si vogliono specificare:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

La variabile di ambiente `HTTP_PLATFORM_PORT` qui illustrata contiene la porta sulla quale il server locale deve essere in ascolto per le connessioni da localhost. In questo esempio viene anche illustrato come creare un'altra eventuale variabile di ambiente, in questo caso `SERVER_PORT`.

## <a name="installing-packages"></a>Installazione di pacchetti

L'interprete Python installato tramite un'estensione del sito è solo una parte dell'ambiente Python. È probabilmente necessario installare anche pacchetti diversi in tale ambiente.

Per installare i pacchetti direttamente nell'ambiente server, usare uno dei metodi seguenti:

| Metodi | Utilizzo |
| --- | --- |
| [Console Kudu del Servizio app di Azure](#azure-app-service-kudu-console) | I pacchetti vengono installati in modo interattivo. I pacchetti devono essere puri Python o è necessario pubblicare wheel. |
| [API REST Kudu](#kudu-rest-api) | Consente di automatizzare l'installazione dei pacchetti.  I pacchetti devono essere puri Python o è necessario pubblicare wheel. |
| Bundle con app | Installare i pacchetti direttamente nel progetto e quindi distribuirli al servizio app come se facessero parte dell'app. A seconda di quante dipendenze sono presenti e della loro frequenza di aggiornamento, questo metodo può essere il modo più semplice per ottenere una distribuzione funzionante. Tenere presente che queste librerie devono corrispondere alla versione di Python nel server. In caso contrario vengono visualizzati errori sconosciuti dopo la distribuzione. Tuttavia, dato che le versioni di Python nelle estensioni del sito del servizio app sono esattamente le stesse rilasciate su python.org, è possibile ottenere facilmente una versione compatibile per la distribuzione locale. |
| Ambienti virtuali | Non supportato. Ricorrere invece alla creazione di bundle e impostare la variabile di ambiente `PYTHONPATH` in modo che punti al percorso dei pacchetti. |

### <a name="azure-app-service-kudu-console"></a>Console Kudu del Servizio app di Azure

La [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) offre l'accesso diretto da riga di comando con privilegi elevati al server del servizio app e al relativo file system. Oltre a essere un utile strumento di debug, supporta operazioni CLI, come l'installazione dei pacchetti.

1. Aprire Kudu dalla pagina del servizio app nel portale di Azure: selezionare **Strumenti di sviluppo > Strumenti avanzati** e quindi selezionare **Vai**. Questa azione consente di passare a un URL uguale all'URL del servizio app di base, con l'aggiunta di `.scm`. Ad esempio, se l'URL di base è `https://vspython-test.azurewebsites.net/` Kudu è su `https://vspython-test.scm.azurewebsites.net/` ed è possibile aggiungere un segnalibro:

    ![Console Kudu per il servizio app di Azure](media/python-on-azure-console01.png)

1. Selezionare **Console di debug > CMD** per aprire la console, in cui è possibile esplorare l'installazione di Python e vedere quali librerie sono già presenti.

1. Per installare un singolo pacchetto:

    a. Passare alla cartella di installazione di Python in cui si vuole installare il pacchetto, ad esempio `d:\home\python361x64`.

    b. Usare `python.exe -m pip install <package_name>` per installare un pacchetto.

    ![Esempio di installazione di Bottle tramite la console Kudu per il Servizio app di Azure](media/python-on-azure-console02.png)

1. Se è già stato distribuito un file `requirements.txt` per l'app nel server, installare tutti questi requisiti come indicato di seguito:

    a. Passare alla cartella di installazione di Python in cui si vuole installare il pacchetto, ad esempio `d:\home\python361x64`.

    b. Eseguire il comando `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    È consigliabile usare `requirements.txt` perché è facile riprodurre l'esatto set di pacchetti sia in locale che nel server. Ricordarsi di visitare la console dopo la distribuzione di qualsiasi modifica apportata a `requirements.txt` e di eseguire nuovamente il comando.

> [!Note]
> Non è presente alcun compilatore C nel servizio app, pertanto è necessario installare il file wheel per tutti i pacchetti con moduli di estensione nativa. Molti pacchetti diffusi offrono i propri file wheel. Per i pacchetti che non li offrono, usare `pip wheel <package_name>` nel computer di sviluppo locale e quindi caricare il file wheel nel proprio sito. Per un esempio, vedere [Gestione dei pacchetti necessari](managing-python-environments-in-visual-studio.md#managing-required-packages-requirementstxt).

### <a name="kudu-rest-api"></a>API REST Kudu

Anziché usare la console Kudu tramite il portale di Azure, è possibile eseguire comandi in modalità remota tramite l'API REST Kudu inserendo il comando su `https://yoursite.scm.azurewebsites.net/api/command`. Ad esempio, per installare il pacchetto `bottle`, inserire il JSON seguente su `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Per informazioni sui comandi e l'autenticazione, vedere la [documentazione di Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

È anche possibile visualizzare le credenziali con il comando `az webapp deployment list-publishing-profiles` tramite l'interfaccia della riga di comando di Azure (vedere [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az_webapp_deployment_list_publishing_profiles)). È anche disponibile in [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42) una libreria helper per la pubblicazione dei comandi Kudu.
