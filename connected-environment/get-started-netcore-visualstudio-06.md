---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 6: Informazioni sullo sviluppo in team | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: d8d81afbe4fbf99c52107c8afc6f1eb9938de792
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introduzione a Connected Environment con .NET Core e Visual Studio

Passaggio precedente: [Chiamare un altro contenitore](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>Informazioni sullo sviluppo in team

Finora il codice dell'applicazione è stato eseguito come se all'app lavorasse un solo sviluppatore. In questa sezione si apprenderà come Connected Environment può semplificare lo sviluppo in team:
* Consentire a un team di sviluppatori di collaborare nello stesso ambiente di sviluppo.
* Ogni sviluppatore può eseguire iterazioni del codice di cui è responsabile in isolamento e senza timore di inficiare il lavoro di altri.
* Condurre test completi del codice, prima di eseguirne il commit, senza dover creare mockup o simulare dipendenze.

## <a name="challenges-with-developing-microservices"></a>Difficoltà per lo sviluppo di microservizi
L'applicazione di esempio non è molto complessa al momento. Nello sviluppo per il mondo reale, tuttavia, emergono difficoltà con l'aggiunta di altri servizi e l'espansione del team di sviluppo.

Si immagini di lavorare a un servizio che interagisce con decine di altri servizi.

1. Può diventare irrealistico eseguire tutto in locale per lo sviluppo. Il computer di sviluppo potrebbe non avere risorse sufficienti per eseguire l'intera app. L'app potrebbe anche avere endpoint che devono essere raggiungibili pubblicamente (ad esempio, l'app risponde a un webhook da un'app SaaS).
1. È possibile provare a eseguire solo i servizi da cui si dipende, ma in tal caso sarebbe necessario conoscere l'intera rete di dipendenze, incluse le dipendenze delle dipendenze. Occorre anche tenere conto che potrebbe non essere facile stabilire come compilare ed eseguire le dipendenze, perché sono state sviluppate da altri.
1. Alcuni sviluppatori ricorrono a simulazioni, o mockup, per molte delle dipendenze dei servizi. Questa soluzione può essere utile in alcuni casi, ma la gestione di questi mockup può diventare in fretta una vera e propria attività di sviluppo. Inoltre, in questo modo l'ambiente di sviluppo può diventare molto diverso da quello di produzione, con conseguente introduzione di bug difficili da individuare.
1. Ne consegue che diventa difficile eseguire in modo completo qualsiasi tipo di test. I test di integrazione possono avvenire realisticamente solo dopo il commit e questo significa che i problemi emergono in una fase avanzata del ciclo di sviluppo.

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Lavorare in un ambiente di sviluppo condiviso
Con Connected Environment è possibile impostare un ambiente di sviluppo *condiviso* in Azure. Ogni sviluppatore può concentrarsi solo sulla parte assegnata dell'applicazione e può sviluppare in modo iterativo il *codice pre-commit* in un ambiente che già contiene tutti gli altri servizi e le risorse del cloud da cui dipendono i suoi scenari. Le dipendenze sono sempre aggiornate e gli sviluppatori lavorano in un ambiente che rispecchia quello di produzione.

## <a name="work-in-your-own-space"></a>Lavorare nello spazio personale
Quando si sviluppa il codice per il servizio e prima di essere pronti per l'archiviazione, spesso il codice non sarà in buono stato, perché sono ancora in corso le operazioni iterative di definizione, test e sperimentazione con soluzioni. Connected Environment usa il concetto di **spazio**, che consente di lavorare in isolamento e senza timore di inficiare il lavoro degli altri membri del team.

Eseguire le operazioni seguenti per assicurarsi che entrambi i servizi `webfrontend` e `mywebapi` siano in esecuzione nell'ambiente di sviluppo **e nello spazio `mainline`**.
1. Chiudere eventuali sessioni di debug/F5 per entrambi i servizi, ma mantenere i progetti aperti nelle finestre di Visual Studio.
2. Passare alla finestra di Visual Studio con il progetto `mywebapi` e premere CTRL+F5 per eseguire il servizio senza il debugger collegato.
3. Passare alla finestra di Visual Studio con il progetto `webfrontend` e premere CTRL+F5 per eseguire anche questo.

> [!Note]
In alcuni casi è necessario aggiornare il browser dopo la visualizzazione iniziale della pagina Web in seguito a CTRL+F5.

Qualsiasi utente che apre l'URL pubblico e passa all'app Web richiamerà il percorso del codice scritto che esegue entrambi i servizi con lo spazio `mainline` predefinito. Si supponga ora di voler continuare a sviluppare `mywebapi`. Come è possibile procedere senza interrompere altri sviluppatori che usano l'ambiente di sviluppo? A tale scopo, verrà configurato uno spazio personale.

### <a name="create-a-new-space"></a>Creare un nuovo spazio
Da Visual Studio è possibile creare spazi aggiuntivi che verranno usati quando si preme F5 o CTRL+F5 per il servizio. È possibile usare qualsiasi nome per uno spazio ed essere flessibili sul significato (ad esempio `sprint4` o `demo`).

Eseguire le operazioni seguenti per creare un nuovo spazio:
1. Passare alla finestra di Visual Studio con il progetto `mywebapi`.
2. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Proprietà**.
3. Selezionare la scheda **Debug** a sinistra per visualizzare le impostazioni di Connected Environment.
4. Da qui è possibile modificare o creare Connected Environment e/o lo spazio che verrà usato quando si preme F5 o CTRL+F5. *Assicurarsi che l'ambiente Connected Environment creato in precedenza sia selezionato*.
5. Nell'elenco a discesa **Space** (Spazio) selezionare **<Create New Space…>** (Crea nuovo spazio).

    ![](images/Settings.png)

6. Nella finestra di dialogo **Add Space** (Aggiungi spazio) digitare un nome per lo spazio e fare clic su **OK**. In questo esempio è stato usato il nome dello sviluppatore "scott" per il nuovo spazio, in modo che lo spazio di quello sviluppatore sia facilmente identificabile dai colleghi.

    ![](images/AddSpace.png)

7. A questo punto dovrebbe essere visualizzato l'ambiente di sviluppo con il nuovo spazio selezionato nella pagina delle proprietà del progetto.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Aggiornare il codice per *mywebapi*

1. Nel progetto `mywebapi` modificare il codice del metodo `string Get(int id)` nel file `ValuesController.cs` come indicato di seguito:
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Impostare un punto di interruzione in questo blocco di codice aggiornato (potrebbe essercene già uno impostato in precedenza).
3. Premere F5 per avviare il servizio `mywebapi`. Il servizio verrà avviato nell'ambiente di sviluppo con lo spazio selezionato, che in questo caso è denominato `scott`.

Ecco un diagramma che consentirà di comprendere il funzionamento dei diversi spazi. Il percorso blu mostra una richiesta tramite lo spazio `mainline`, ovvero il percorso predefinito usato se non viene anteposto lo spazio all'URL. Il percorso di colore verde indica una richiesta tramite lo spazio `scott`.

![](media/Space-Routing.png)

Questa funzionalità predefinita di Connected Environment consente di eseguire test completi del codice in un ambiente condiviso senza richiedere a ogni sviluppatore di ricreare lo stack completo dei servizi nello spazio personale. Si noti che questo indirizzamento richiede l'inoltro di intestazioni di propagazione nel codice dell'app, come illustrato nel passaggio precedente di questa guida.

## <a name="test-code-running-in-the-scott-space"></a>Testare il codice in esecuzione nello spazio `scott`
Per testare la nuova versione di `mywebapi` in combinazione con `webfrontend`, aprire il browser all'URL del punto di accesso pubblico per `webfrontend` (ad esempio https://webfrontend-teamenv.vsce.io) e passare alla pagina About. Verrà visualizzato il messaggio originale "Hello from webfrontend and Hello from mywebapi".

A questo punto, aggiungere la parte "scott-" all'URL in modo che diventi simile a https://scott-webfrontend-teamenv.vsce.io e aggiornare il browser. Si dovrebbe raggiungere il punto di interruzione impostato nel progetto `mywebapi`. Premere F5 per continuare. Nel browser dovrebbe essere ora visualizzato il nuovo messaggio "Hello from webfrontend and mywebapi now says something new". Questo perché il percorso del codice aggiornato in `mywebapi` è in esecuzione nello spazio `scott`.

> [!div class="nextstepaction"]
> [Riepilogo](get-started-netcore-visualstudio-07.md)