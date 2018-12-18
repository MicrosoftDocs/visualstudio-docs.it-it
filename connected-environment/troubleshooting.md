---
title: Risoluzione dei problemi | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 0f35e31e3f3a109e65565592b56b6dc4177dd7c0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="troubleshooting-guide"></a>Guida alla risoluzione dei problemi

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Errore 'upstream connect error or disconnect/reset before headers' (errore di connessione upstream o disconnessione/ripristino prima delle intestazioni)
Questo errore potrebbe essere visualizzato quando si tenta di accedere al servizio. Ad esempio, quando si passa all'URL del servizio in un browser. 

**Motivo:** la porta del contenitore non è disponibile. Questi sono i motivi più comuni: 
* Il contenitore è ancora in corso di compilazione e distribuzione. Questa condizione può verificarsi se si esegue `vsce up` o si avvia il debugger e quindi si tenta di accedere al contenitore prima del completamento della distribuzione.
* La configurazione delle porte non è coerente tra Dockerfile, il grafico Helm e qualsiasi codice sul lato server che apre una porta.

**Possibile soluzione:**
1. Se il contenitore è in corso di compilazione/distribuzione, è possibile attendere 2-3 secondi e tentare di accedere nuovamente al servizio. 
1. Controllare la configurazione delle porte. I numeri di porta specificati devono essere **identici** in tutti gli asset seguenti:
    * **Dockerfile:** specificati dall'istruzione `EXPOSE`.
    * **[Grafico Helm](https://docs.helm.sh):** specificati dai valori `externalPort` e `internalPort` per un servizio (spesso disponibili in un file `values.yml`),
    * Qualsiasi porta aperta nel codice dell'applicazione, ad esempio in Node.js: `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>File di configurazione non trovato
Si esegue `vsce up` e viene visualizzato l'errore seguente: `Config file not found: .../vsce.yaml`

**Motivo:** `vsce up` deve essere eseguito dalla directory radice del codice da eseguire e la cartella del codice deve essere stata inizializzata per l'esecuzione con Connected Environment.

**Possibile soluzione:**
1. Impostare la directory corrente sulla cartella radice contenente il codice del servizio. 
1. Se nella cartella del codice non è disponibile un file vsce.yaml, eseguire `vsce init` per generare gli asset di Docker, Kubernetes e VSCE.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Errore: 'The pipe program 'vsce' exited unexpectedly with code 126.' (Chiusura imprevista del programma pipe 'vsce' con il codice 126.)
L'avvio del debugger di Visual Studio Code può generare a volte questo errore. Si tratta di un bug.

**Possibile soluzione:**
1. Chiudere e riaprire Visual Studio Code.
2. Premere di nuovo F5.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Errore di debug 'Configured debug type 'coreclr' is not supported' (Il tipo di debug configurato 'coreclr' non è supportato)
Quando si esegue il debugger di Visual Studio Code viene segnalato l'errore: `Configured debug type 'coreclr' is not supported.`

**Motivo:** l'estensione di Visual Studio Code per Connected Environment non è installata nel computer di sviluppo.

**Possibile soluzione:** installare l'[estensione di Visual Studio per Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Il portale di Azure non mostra le istanze di Connected Environment

**Motivo:** un'esperienza del portale di Azure per Connected Environment non è ancora pronta per l'anteprima.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>Non è possibile trovare il tipo o il nome di spazio dei nomi 'MyLibrary'

**Motivo:** il contesto di compilazione è a livello di progetto/servizio per impostazione predefinita, pertanto non verrà trovato un progetto di libreria in uso.

**Possibile soluzione:** operazioni da eseguire:
1. Modificare il file vsce.yaml per impostare il contesto di compilazione a livello di soluzione.
2. Modificare i file Dockerfile e Dockerfile.develop in modo da fare riferimento ai file csproj in modo corretto, rispetto al nuovo contesto di compilazione.
3. Affiancare un file con estensione dockerignore al file con estensione sln e apportare le modifiche necessarie.

È possibile trovare un esempio all'indirizzo https://github.com/sgreenmsft/buildcontextsample

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Errore di autorizzazione 'Microsoft.ConnectedEnvironment/register/action' durante la creazione di un ambiente
Potrebbe essere visualizzato l'errore seguente quando si gestisce un ambiente e si lavora in una sottoscrizione di Azure a cui non si ha accesso come Proprietario o Collaboratore.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Motivo:** la sottoscrizione di Azure selezionata non ha registrato lo spazio dei nomi Microsoft.ConnectedEnvironment.

**Possibile soluzione:** un utente con accesso come Proprietario o Collaboratore per la sottoscrizione di Azure può eseguire il seguente comando dell'interfaccia della riga di comando di Azure per registrare manualmente lo spazio dei nomi Microsoft.ConnectedEnvironment:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE non sembra usare il Dockerfile esistente per compilare un contenitore 

**Motivo:** VSCE può essere configurato per puntare a un Dockerfile specifico nel progetto. Se apparentemente VSCE non usa il Dockerfile previsto per compilare i contenitori, potrebbe essere necessario indicare in modo esplicito a VSCE dove si trova. 

**Possibile soluzione:** aprire il file `vsce.yaml` generato da VSCE nel progetto. Usare la direttiva `configurations->develop->build->dockerfile` per puntare al Dockerfile che si vuole usare:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```