## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Inizializzare il codice per lo sviluppo di Docker e Kubernetes
Finora, è disponibile una semplice app Web che può essere eseguita in locale. L'app verrà ora inserita in un contenitore creando gli asset che definiscono il contenitore dell'app e il modo in cui verrà distribuito in Kubernetes. Si tratta di operazioni semplici con Connected Environment: 

1. Avviare Visual Studio Code e aprire la cartella `webfrontend`. (È possibile ignorare eventuali richieste predefinite per l'aggiunta di risorse di debug o il ripristino del progetto.)
1. Aprire il terminale integrato in Visual Studio Code (usando il menu **Visualizza | Terminale integrato**).
1. Eseguire questo comando (assicurarsi che la cartella corrente sia **webfrontend**):

```cmd
vsce init --public
```

Il comando dell'interfaccia della riga di comando di Connected Environment ```init``` genera asset Docker e Kubernetes con le impostazioni predefinite:
* `./Dockerfile` descrive l'immagine contenitore dell'app e la modalità di compilazione ed esecuzione del codice sorgente all'interno del contenitore.
* Un [grafico Helm](https://docs.helm.sh) in `./charts/webfrontend` descrive come distribuire il contenitore in Kubernetes.

Per il momento non è necessario comprendere l'intero contenuto di questi file. Vale tuttavia la pena sottolineare che **gli stessi asset di configurazione come codice di Kubernetes e Docker possono essere usati dallo sviluppo alla produzione, garantendo così una maggiore coerenza tra i diversi ambienti**.
 
Il comando `init` genera anche un file denominato `./vsce.yaml`, ovvero il file di configurazione per Connected Environment. Tale file è complementare agli artefatti di Docker e Kubernetes e rende disponibili elementi di configurazione aggiuntivi che consentono un'esperienza di sviluppo iterativo in Azure. Ad esempio, il grafico Helm predefinito non espone alcun endpoint pubblico. In alcuni casi, tuttavia, è utile aprire un endpoint pubblico temporaneamente durante lo sviluppo in modo da poter testare il codice, ad esempio, da un dispositivo mobile o un URL di webhook. Un file vsce.yaml creato con `init --public` sostituisce i parametri predefiniti Helm per esporre un endpoint pubblico solo per la fase di sviluppo.
