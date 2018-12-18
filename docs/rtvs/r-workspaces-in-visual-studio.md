---
title: Aree di lavoro in R Tools per Visual Studio | Microsoft Docs
description: Come controllare la posizione di esecuzione del codice R tramite le aree di lavoro in Visual Studio.
ms.custom: 
ms.date: 01/24/2018
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
ms.openlocfilehash: bb520f317eb285bcc278ff9f37bb2dc25c91e950
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="controlling-where-r-code-runs-with-workspaces"></a>Controllo della posizione di esecuzione del codice R con le aree di lavoro

Un'area di lavoro in R Tools per Visual Studio (RTVS) consente di configurare la posizione di esecuzione di una sessione R, che può essere eseguita sia su computer locali che su computer remoti. L'obiettivo è offrire un'esperienza utente simile in entrambi i casi, anche grazie all'uso di computer più potenti nel cloud.

Per aprire la finestra **Aree di lavoro** usare il comando **R Tools > Finestre > Aree di lavoro** o premere Ctrl+9.

![Finestra Aree di lavoro in R Tools per Visual Studio (VS2017)](media/workspaces-window.png)

In questa finestra il segno di spunta verde indica l'area di lavoro attiva alla quale è associato RTVS. Selezionare una freccia blu per impostare l'area di lavoro attiva. L'icona delle impostazioni (a forma di ingranaggio) sulla destra di ogni area di lavoro consente di modificarne il nome, il percorso e gli argomenti della riga di comando. La X rossa rimuove un'area di lavoro aggiunta manualmente.

## <a name="saving-and-resetting-a-workspace"></a>Salvataggio e reimpostazione di un'area di lavoro

Per impostazione predefinita lo stato dell'area di lavoro non viene salvato quando si chiude e si riapre un progetto in RTVS. È tuttavia possibile modificare questa funzionalità mediante le [opzioni dell'area di lavoro](options-for-r-tools-in-visual-studio.md#workspace).

Il comando **R Tools > Sessione > Reimposta** e il pulsante di reimpostazione della barra degli strumenti nella finestra interattiva consentono di reimpostare lo stato dell'area di lavoro in qualsiasi momento. Per le aree di lavoro remote la reimpostazione elimina il profilo utente creato alla prima connessione al server remoto e di fatto elimina anche tutti i file accumulati nel server remoto.

## <a name="local-workspaces"></a>Aree di lavoro locali

Nell'elenco delle aree di lavoro locali vengono visualizzati tutti gli interpreti R installati nel computer in uso. 

All'avvio Visual Studio tenta di rilevare automaticamente tutte le versioni di R installate, esaminando la chiave del Registro di sistema `HKEY_LOCAL_MACHINE\Software\R-Core\`. Poiché questo controllo viene effettuato solo all'avvio, se si installa un nuovo interprete R è necessario riavviare Visual Studio.

È possibile che un interprete R installato in modo non standard (ad esempio copiando direttamente i file in una cartella invece di eseguire un programma di installazione) non venga rilevato. In questo caso creare manualmente una nuova area di lavoro R locale come segue:

1. Selezionare il pulsante **Aggiungi** nella finestra Aree di lavoro.
1. Immettere un nome per la nuova area di lavoro.
1. Immettere il percorso della cartella radice R, che contiene la cartella `bin` con l'interprete. Immettere anche eventuali argomenti della riga di comando facoltativi da passare all'interprete all'avvio di RTVS.
1. Al termine selezionare **Salva**.

![Aggiunta di una nuova area di lavoro](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Aree di lavoro remote

Le aree di lavoro remote consentono di connettersi a una sessione R in un computer remoto. Per informazioni su come configurare un computer a questo scopo, vedere [Impostazione di aree di lavoro remote](setting-up-remote-r-workspaces.md).

Visual Studio non rileva automaticamente le aree di lavoro remote, quindi è necessario aggiungerle manualmente con il pulsante **Aggiungi** nella finestra Aree di lavoro come descritto nella sezione precedente. In questo caso immettere l'URI del computer remoto anziché un percorso locale.

> [!Important]
> Le aree di lavoro remote sono identificate da un URI che *deve usare il protocollo HTTPS* per garantire la riservatezza e l'integrità delle comunicazioni con il computer remoto. Visual Studio non è in grado di connettersi a un computer remoto che non supporta HTTPS.

> [!Note]
> Le aree di lavoro remote sono una funzionalità in anteprima. È in corso l'elaborazione di un approccio migliore al problema della sincronizzazione dei file per una versione successiva ed eventuali idee e suggerimenti sono benvenuti.

## <a name="remote-workspace-logon"></a>Accesso ad aree di lavoro remote

È necessario usare un nome utente e una password per accedere all'area di lavoro remota.

### <a name="logon-to-windows-workspace"></a>Accesso all'area di lavoro di Windows

Se il computer remoto è configurato per usare l'account di dominio, è possibile usare l'accesso al dominio per accedere a un'area di lavoro remota. In caso contrario, è necessario usare il formato `machine-name\username` per accedere con un account computer nel computer remoto.

### <a name="logon-to-linux-workspace"></a>Accesso all'area di lavoro di Linux

Per accedere a un account Linux, usare il formato `<<unix>>\username`. Ad esempio, se è disponibile un account con il nome `ruser`, è necessario digitare il nome utente come `<<unix>>\ruser`.

## <a name="switching-between-workspaces"></a>Passaggio da un'area di lavoro all'altra

RTVS è associato solo a una singola area di lavoro alla volta. L'area di lavoro associata è indicata da un piccolo segno di spunta verde nella finestra Aree di lavoro. Per impostazione predefinita, RTVS esegue l'associazione all'ultima area di lavoro locale aperta in una sessione precedente.

Per cambiare l'area di lavoro attiva, selezionare la freccia blu accanto all'area di lavoro desiderata. Viene richiesto di salvare la sessione e l'area di lavoro corrente viene chiusa, quindi viene attivata la nuova area di lavoro.

> [!Tip]
> Per disattivare la richiesta di salvataggio selezionare il comando **R Tools > Opzioni** e impostare l'opzione **Mostra finestra di conferma prima di passare da un'area di lavoro all'altra** su `No`. Vedere [Opzioni dell'area di lavoro](options-for-r-tools-in-visual-studio.md#workspace).

Se si prova a passare a un'area di lavoro locale che è stata disinstallata o a un'area di lavoro remota non disponibile, RTVS potrebbe non essere associato ad alcuna area di lavoro. Di conseguenza, potrebbe apparire un errore se si immette codice nella finestra interattiva o si prova a eseguire codice con altri metodi:

![Errore quando nessuna area di lavoro è associata a RTVS](media/workspaces-disconnected-interactive-window.png)

Per risolvere il problema passare a un'altra area di lavoro nella finestra Aree di lavoro. Se non è disponibile alcuna area di lavoro, è necessario installare un interprete R. È anche possibile provare a riavviare Visual Studio se è stato installato un interprete durante l'esecuzione di Visual Studio.

### <a name="switching-to-a-remote-workspace"></a>Passaggio a un'area di lavoro remota

Quando in RTVS si esegue per la prima volta la connessione a un'area di lavoro remota vengono richieste le credenziali, che vengono quindi memorizzate nella cache (tramite la Casella di sicurezza delle credenziali di Windows) per le sessioni successive. Le comunicazioni con il server remoto vengono quindi eseguite in modo sicuro su HTTPS (obbligatorio).

A seconda della configurazione del server, è possibile che al momento della connessione venga visualizzato questo avviso relativo al certificato: "Il certificato di sicurezza presentato da Remote R Services non consente di dimostrare che l'utente sia effettivamente connesso al computer (nome)".

![Avviso di certificato autofirmato durante la connessione a un'area di lavoro remota](media/workspaces-remote-self-signed-certificate-warning.png)

Il certificato è un documento presentato a RTVS dal computer a cui si sta tentando di connettersi. Il certificato contiene un campo che identifica l'URI di quel computer. L'avviso viene visualizzato quando RTVS rileva una mancata corrispondenza tra l'URI del certificato e l'URI usato per la connessione al computer, indice di una possibile violazione della sicurezza del server.

Questo avviso viene tuttavia visualizzato anche quando si usa un *certificato autofirmato* anziché un certificato di un provider attendibile per abilitare HTTPS sul computer remoto. Per altre informazioni, vedere [Impostazione di aree di lavoro remote](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Directory sui computer locali e remoti

Per impostazione predefinita, quando si avvia un nuovo interprete R in un'area di lavoro locale la directory di lavoro corrente è `%userprofile%\Documents`. È possibile cambiare directory in qualsiasi momento usando il comando **R Tools > Directory di lavoro** o facendo clic con il pulsante destro del mouse in Esplora soluzioni di Visual Studio e selezionando un comando come **Imposta directory di lavoro qui**.

Quando si effettua la connessione a un computer remoto per la prima volta, RTVS crea automaticamente un profilo utente basato sulle credenziali usate e la directory di lavoro viene impostata sulla cartella `Documents` in quel profilo. La cartella viene usata per tutte le sessioni remote successive che usano le stesse credenziali. 

Di conseguenza la posizione esatta in cui viene eseguito il codice può essere diversa nelle aree di lavoro locali e remote. Usare quindi sempre nel codice percorsi relativi per i file di dati ed elementi simili, in modo tale che il codice sia portabile tra le aree di lavoro.

Si noti anche che con le aree di lavoro remote tutti i file presenti nella directory di lavoro vengono mantenuti tra le diverse sessioni eseguite con lo stesso profilo utente. Come indicato in precedenza, quando si usa un'area di lavoro remota è possibile eliminare questi file con il comando **R Tools > Sessione > Reimposta** o con il pulsante di reimpostazione nella finestra interattiva. Questo comando elimina dal server il profilo utente, che verrà ricreato quando si effettua di nuovo la connessione.

## <a name="copying-project-files-to-remote-workspaces"></a>Copia di file di progetto in aree di lavoro remote

Quando si lavora con progetti R in Visual Studio, i file di progetto più recenti si trovano sempre nel computer locale, anche quando si usa un'area di lavoro remota. In altri termini, quando si apre un progetto in Visual Studio (il che in genere equivale ad aprire una soluzione contenente tale progetto), RTVS presuppone che il contenuto del progetto risieda interamente nel computer locale. L'area di lavoro remota è di fatto solo un host temporaneo per i file del progetto e l'eventuale output del codice. Ciò significa ad esempio che quando si carica un file usando `source` nella finestra interattiva, tale file deve già essere presente nel computer remoto nel percorso specificato o deve trovarsi nella directory di lavoro corrente dell'interprete R remoto (impostato con la funzione `setwd()`).

I file vengono copiati nel server remoto come indicato di seguito:

- Per lavorare con i file in modalità remota tramite la finestra interattiva è necessario copiarli manualmente facendo clic con il pulsante destro del mouse su di essi (o sul progetto) in Esplora Soluzioni e scegliendo **Source Selected ** (**Origine selezionata**). I singoli file vengono copiati nella directory di lavoro nel server. Se si copia un progetto, RTVS crea una cartella per il progetto.

- È anche possibile copiare i file selezionandoli in Esplora soluzioni, quindi scegliendo **File di origine selezionati**. Con questa azione i file vengono caricati nella finestra interattiva ed eseguiti in tale posizione. Se la sessione è connessa a un computer remoto, i file vengono in primo luogo copiati in tale computer.

- Quando RTVS è associato a un'area di lavoro remota e si preme F5, si seleziona **Debug > Avvia debug** o si avvia in un altro modo l'esecuzione del codice, per impostazione predefinita RTVS copia automaticamente il file del progetto nell'area di lavoro remota (vedere di seguito le informazioni sulla gestione di questo comportamento).

- Tutti i file già esistenti nel server vengono sovrascritti.

> [!Note]
> Poiché RTVS non intercetta in modo affidabile tutte le chiamate di funzione R, la chiamata di funzioni come `source()` o `runApp()` (per le applicazioni Shiny) all'interno della finestra interattiva *non* copia i file nell'area di lavoro remota.

Le [proprietà del progetto](r-projects-in-visual-studio.md#project-properties) determinano se i file vengono copiati da RTVS quando si esegue un progetto e quali file vengono copiati. Per aprire la pagina corrispondente selezionare il comando **Progetto > Proprietà (nome)** o fare clic con il pulsante destro del mouse in Esplora soluzioni e selezionare **Proprietà**.

![Scheda di esecuzione delle proprietà del progetto con le impostazioni di trasferimento file](media/workspaces-remote-file-transfer-filter-settings.png)

L'opzione **Trasferisci file durante l'esecuzione** determina se RTVS deve copiare i file di progetto automaticamente. Il valore **Files to transfer** (File da trasferire) consente quindi di filtrare con precisione i file da trasferire. Per impostazione predefinita vengono copiati solo i file `.R`, `.Rmd`, `.sql`, `.md` e `.cpp`. Questo comportamento evita che vengano copiati inavvertitamente file di dati di grandi dimensioni nel server a ogni esecuzione. 

## <a name="copying-files-from-a-remote-workspace"></a>Copia di file da un'area di lavoro remota

Se lo script R genera file nel server, è possibile copiare tali file nel client con la funzione `rtvs::fetch_file`. Questa funzione accetta come argomento minimo il percorso remoto del file da copiare nel proprio computer e come argomento facoltativo il percorso di destinazione nel computer. Se non si specifica un percorso il file viene copiato nella cartella `%userprofile%\Downloads`.
