---
title: Gestire i test controller e gli agenti di test in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7372ce6b6c54b9b7b5a4c9dea1fb71fc730d5b08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="manage-test-controllers-and-test-agents"></a>Gestire i test controller e gli agenti di test

Se si desidera usare Visual Studio per eseguire test in modalità remota, distribuire test tra più computer o eseguire test di carico, è necessario configurare un controller di test, agenti di test e il file di impostazioni test. Questo argomento descrive come gestire i controller di test e gli agenti di test dopo averli installati e configurati per la prima volta.

Se si usa Microsoft Test Manager per eseguire test negli ambienti lab, è necessario gestire i test controller e i relativi agenti tramite **Gestione controller di test** in **Centro lab** di Microsoft Test Manager. Questo argomento è applicabile solo se si usa Visual Studio per eseguire i test.

Per informazioni su come installare e configurare test controller e agenti di test per eseguire test in Visual Studio, vedere [Configurare agenti e test controller](../test/configure-test-agents-and-controllers-for-load-tests.md).

Per configurare e monitorare il controller di test e gli eventuali agenti registrai, è necessario disporre di un file di impostazioni di test nel progetto di test che contiene i test da eseguire. Aprire il file di impostazioni di test, scegliere **Ruolo** e quindi selezionare **Gestisci controller di test** nell'elenco a discesa del campo **Controller**.

Per un progetto di test di carico è anche possibile scegliere **Gestisci controller di test** dal menu **Test di carico**.

## <a name="add-a-test-agent-to-a-test-controller"></a>Aggiungere un agente di test a un test controller

È possibile che si desideri aggiungere un agente di test a un diverso controller di test oppure che risulti necessario aggiungere un agente di test a un controller di test appena installato.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Per aggiungere un agente di test a un controller di test

1. Scegliere **Avvia** > **Test Agent Configuration Tool**.

     Viene visualizzata la finestra di dialogo **Configura agente di test**.

    > [!NOTE]
    > È necessario che l'agente di test sia già installato affinché possa essere aggiunto a un controller di test. Per altre informazioni su come installare un agente di test, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

2. Se si desidera modificare la modalità di esecuzione dell'agente di test, scegliere **Opzioni di esecuzione**.

     Verranno visualizzate due opzioni relative alla modalità di esecuzione dell'agente di test:

     **Servizio** Se non è necessario eseguire test automatizzati che interagiscono con il desktop, ad esempio i test codificati dell'interfaccia utente o la creazione di una registrazione video durante l'esecuzione dei test, selezionare **Servizio** in **Esegui agente di test come**. L'agente di test verrà avviato come servizio. Scegliere **Avanti**.

     A questo punto è possibile immettere i dettagli sull'utente quando l'agente di test viene avviato come servizio.

    1. Immettere il nome in **Nome utente**.

    2. Immettere la password in **Password**.

        |**Informazioni importanti sull'account utente**|
        |--------------------------------------------|
        |-   Le password Null non sono supportate per gli account utente.|
        |-   Se si desidera utilizzare l'agente di raccolta di IntelliTrace o l'emulazione di rete, l'account utente deve essere un membro del gruppo Administrators.|
        |-   Se il nome utente dell'agente non è presente nel servizio agente, verrà effettuato il tentativo di aggiungerlo. Questa operazione richiede autorizzazioni sul test controller.|
        |-   È necessario che l'utente che sta tentando di usare il test controller  disponga di un account utente per tale test controller, diversamente non sarà in grado di eseguite i test.|

     **Processo interattivo** Se si desidera eseguire test automatizzati che devono interagire con il desktop, ad esempio i test codificati dell'interfaccia utente o la creazione di una registrazione video durante l'esecuzione dei test, selezionare **Processo interattivo**. L'agente di test verrà avviato come processo interattivo anziché come servizio.

     Nella pagina successiva immettere i dettagli relativi all'utente quando l'agente di test viene avviato come processo e specificare le altre opzioni.

    1. Immettere il nome in **Nome utente**.

    2. Immettere la password in **Password**.

        > [!NOTE]
        > Se si configura l'agente di test in modo che venga eseguito come processo interattivo con un utente diverso dall'utente attualmente attivo, è necessario riavviare il computer e accedere come utente corrente per poter avviare l'agente. Inoltre, le password Null non sono supportate per gli account utente. Se si desidera utilizzare l'agente di raccolta di IntelliTrace o l'emulazione di rete, l'account utente deve essere un membro del gruppo Administrators.

        |**Informazioni importanti sull'account utente**|
        |--------------------------------------------|
        |-   Le password Null non sono supportate per gli account utente.|
        |-   Se si desidera utilizzare IntelliTrace o l'adattatore dati di emulazione di rete e diagnostico, è necessario che l'account utente sia membro del gruppo Administrators. Se nel computer che esegue l'agente di test viene utilizzato un sistema operativo che dispone di un account utente con privilegi minimi, sarà necessario eseguire l'agente di test anche come amministratore (con privilegi elevati).|
        |-   Se il nome utente dell'agente non è presente nel servizio agente, verrà effettuato il tentativo di aggiungerlo. Questa operazione richiede autorizzazioni sul test controller.|
        |-   È necessario che l'utente che sta tentando di usare il test controller  disponga di un account utente per tale test controller, diversamente non sarà in grado di eseguite i test.|

    3. Per accertarsi che un computer che dispone di un agente di test sia in grado di eseguire i test dopo il riavvio, è possibile configurarlo per l'accesso automatico come utente dell'agente di test. Selezionare **Accesso automatico**. In questo modo il nome utente e la password verranno archiviati in formato crittografato nel Registro di sistema.

    4. Per assicurarsi che lo screen saver sia disabilitato in quanto potrebbe interferire con i test automatizzati che devono interagire con il desktop, selezionare **Verifica che lo screen saver sia disabilitato**.

        > [!WARNING]
        > L'accesso automatico e la disabilitazione dello screen saver implicano rischi per la sicurezza. Se si abilita l'accesso automatico si consente ad altri utenti di avviare il computer e di usare l'account in grado di accedere automaticamente. Se si disabilita lo screen saver, è possibile che non venga richiesto di immettere le credenziali di un utente per accedere e sbloccare il computer. In questo modo chiunque possa raggiungere fisicamente il computer potrà accedere al sistema. Se si abilitano queste funzionalità in un computer, è consigliabile accertarsi che esso sia fisicamente protetto. Ad esempio, i computer potrebbero essere collocati in un laboratorio sicuro. La deselezione dell'opzione **Verifica che lo screen saver sia disabilitato** non abilita lo screen saver.

3. Per registrare l'agente con un test controller diverso, selezionare **Registra con controller di test**. Digitare il nome del test controller seguito da **:** e dal numero di porta usato in **Registra l'agente di test con il controller di test seguente**. Digitare ad esempio **agent1:6901**.

    > [!NOTE]
    > Il numero di porta predefinito è 6901.

4. Per salvare le modifiche, scegliere **Applica impostazioni**. Chiudere la finestra di dialogo **Riepilogo configurazione**, quindi chiudere Test Agent Configuration Tool.

> [!WARNING]
> Se l'agente è attualmente configurato per essere eseguito in un altro controller di test, è necessario rimuoverlo da quest'ultimo.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Rimuovere un agente di test da un test controller

Per poter rimuovere un agente di test, è necessario che sia impostato sullo stato offline.

> [!NOTE]
> Non è possibile usare questa procedura per rimuovere gli agenti registrati per un controller nell'ambito di un ambiente lab. Per rimuovere questi agenti da un controller, è necessario rimuovere l'ambiente usando Microsoft Test Manager.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Per rimuovere un agente di test da un controller di test

1. Se il controller di test non è registrato con un progetto team, attenersi alla procedura seguente.

    1. In Visual Studio aprire il file di impostazioni di test per il progetto di test, scegliere **Ruolo** e quindi selezionare **Gestisci controller di test** nell'elenco a discesa del campo **Controller**.

         Verrà visualizzata la finestra di dialogo **Amministra controller test**.

    2. Nell'elenco a discesa **Controller** digitare il nome del computer in cui è stato configurato il test controller. Se in precedenza si è già amministrato un controller di test specifico, è possibile selezionarne il nome dall'elenco.

    3. Nel riquadro **Agenti** selezionare il nome dell'agente di test. Se l'agente è ancora online, scegliere **Offline**. Per rimuoverlo, scegliere **Rimuovi**.

        > [!NOTE]
        > La rimozione di un agente di test ne determina la disassociazione dal controller di test. Per disinstallare completamente l'agente di test, usare **Programmi e funzionalità** nel Pannello di controllo del computer in cui l'agente è installato.

2. Se il test controller è registrato con un progetto team, rimuovere l'agente mediante Microsoft Test Manager.

## <a name="change-the-settings-for-a-test-agent"></a>Modificare le impostazioni di un agente di test

Lo stato dell'agente di test può essere rappresentato da uno qualsiasi dei valori seguenti:

|Status|Descrizione|
|------------|-----------------|
|Test in esecuzione|Sono in esecuzione test|
|Pronto|Disponibile per l'esecuzione dei test o la raccolta di informazioni e dati di diagnostica|
|Offline|Non disponibile per l'esecuzione dei test o la raccolta di informazioni e dati di diagnostica|
|Disconnesso|L'agente di test non è avviato|

È possibile modificare lo stato e altre impostazioni di un agente di test usando le procedure riportate di seguito.

### <a name="to-change-the-settings-of-a-test-agent"></a>Per modificare le impostazioni di un agente di test

> [!NOTE]
> Se l'agente di test è registrato con un test controller a sua volta registrato con un progetto team, modificare le impostazioni in Microsoft Test Manager.

1. Per configurare e monitorare il test controller e gli eventuali agenti registrati per un test di carico, scegliere il menu **Test di carico** in Visual Studio, quindi scegliere **Gestisci controller di test**. Per tutti gli altri test, aprire il file di impostazioni di test per il progetto di test in Visual Studio, scegliere **Ruolo** e quindi selezionare **Gestisci controller di test** nell'elenco a discesa del campo **Controller**.

   Verrà visualizzata la finestra di dialogo **Gestisci controller di test**.

1. Nell'elenco dei controller di test selezionare il nome di quello per il quale si desidera modificare gli agenti di test. Se il controller di test non è presente nell'elenco, controllare che sia registrato correttamente. Per altre informazioni, vedere la procedura seguente relativa alla configurazione di un controller di test.

1. (Facoltativo) Nel riquadro **Agenti di test** scegliere il computer dell'agente di test per il quale si desidera modificare le proprietà.

1. Scegliere **Proprietà**.

1. Modificare le seguenti proprietà dell'agente di test in base alle necessità:

|Proprietà dell'agente di test|Descrizione|
|-------------------------|-----------------|
|**Peso**|Consente di distribuire il carico quando si usano agenti di test con livelli diversi di prestazioni. Ad esempio, un agente di test con un peso pari a 100 riceve un carico doppio rispetto a uno con un peso di 50.|
|**Commutazione IP**|Usato per configurare la commutazione IP. La commutazione IP consente a un agente di test di inviare richieste a un server usando un intervallo di indirizzi IP. In questo modo si simulano le chiamate provenienti da computer client diversi.<br /><br /> La commutazione IP è importante se il test di carico accede a una Web farm. La maggior parte dei servizi di bilanciamento del carico stabilisce un'affinità tra un client e un determinato server Web usando l'indirizzo IP del client. Se tutte le richieste sembrano provenire da un singolo client, il servizio di bilanciamento del carico non bilancia il carico. Per ottenere un buon bilanciamento del carico nella Web farm, accertarsi che le richieste provengano da un intervallo di indirizzi IP. **Nota**: è possibile specificare una scheda di rete o usare **(Tutti non assegnati)** per selezionarne automaticamente una non in uso. <br /><br /> Per usare la funzionalità di commutazione IP, è necessario che il servizio agente di test di Visual Studio sia in esecuzione come utente del gruppo Administrators del computer in cui si trova l'agente. Questo utente viene selezionato durante l'installazione dell'agente, ma è possibile cambiarlo modificando le proprietà del servizio e riavviandolo.<br /><br /> Per verificare che la commutazione IP funzioni correttamente, abilitare la funzionalità di registrazione di IIS sul server Web e usarla per verificare che le richieste provengano dagli indirizzi IP configurati.|
|**Attributi**|Set di coppie nome/valore utilizzabili nella selezione di agenti di test. Ad esempio un test può richiedere un particolare sistema operativo. Nella scheda **Ruoli** del file di impostazioni di test è possibile aggiungere ruoli utilizzabili per selezionare un agente di test con attributi corrispondenti. Se si desidera eseguire un test su più computer, creare un attributo nel ruolo delle impostazioni di test configurato per l'esecuzione dei test, quindi configurare un attributo corrispondente in ogni agente di test da usare in tale ruolo. **Nota:** questa impostazione è disponibile solo per gli agenti di test registrati con un test controller non registrato in un progetto team, perché quegli attributi vengono usati solo nelle impostazioni di test per Visual Studio.|

Le modifiche apportate al peso e agli attributi di un agente di test vengono applicate immediatamente, ma non influenzano i test in esecuzione. L'Intervallo di indirizzi IP diventa effettivo dopo il riavvio del controller di test.

(Facoltativo) Per modificare lo stato di un agente di test, selezionare l'agente nell'elenco, quindi selezionare l'azione tra le opzioni disponibili in base allo stato corrente dell'agente stesso.

> [!NOTE]
> Se l'agente di test è in esecuzione come processo, il relativo stato può essere gestito dall'icona dell'area di notifica disponibile nel computer in cui l'agente è installato. Indica lo stato dell'agente di test. Se l'agente è in esecuzione come processo, con questo strumento è possibile avviarlo, arrestarlo o riavviarlo. Per avviare l'agente di test come processo se non è in esecuzione, scegliere **Start**, **Tutti i Programmi**, **Microsoft Visual Studio**, **Agente di test di Microsoft Visual Studio**. In questo modo verrà aggiunta l'icona dell'area di notifica.

## <a name="configure-a-test-controller"></a>Configurare un test controller

Per configurare un test controller, è necessario usare **lo strumento di configurazione controller Team Test**. Quando si configura il controller di test, è possibile effettuarne la registrazione con una diversa raccolta di progetti team oppure annullarne la registrazione in una raccolta di progetti team.

Se si vuole registrare il test controller con la raccolta di progetti Team Foundation Server, l'account usato per il servizio del test controller deve essere un membro del gruppo Account del servizio di test della raccolta di progetti per la raccolta di progetti team. In alternativa, l'account usato per eseguire lo strumento di configurazione del test controller deve essere un account Amministratore della raccolta di progetti.

> [!NOTE]
> Se si annulla la registrazione di un controller di test in una raccolta di progetti team che dispone di ambienti esistenti in una raccolta di progetti team, gli ambienti verranno mantenuti qualora quella raccolta di progetti team venisse spostata e si registrasse di nuovo il controller di test nella raccolta spostata.

### <a name="to-configure-a-test-controller"></a>Per configurare un controller di test

1. Per eseguire lo strumento per riconfigurare il test controller in qualsiasi momento, scegliere **Start** > **Tutti i programmi** >  **Microsoft Visual Studio** > **Microsoft Visual Studio Test Controller Configuration Tool**.

     Verrà visualizzata la finestra di dialogo **Configura controller di test**.

2. Selezionare l'utente da utilizzare come account di accesso per il servizio del controller di test.

    > [!NOTE]
    > Le password Null non sono supportate per gli account utente.

4. (Facoltativo) Se non si vuole usare il test controller con un ambiente lab ma solo eseguire test da Visual Studio, deselezionare **Registra con insieme di progetti team**.

5. (Facoltativo) Per configurare il test controller per test di carico, selezionare **Configura per test di carico**. Specificare quindi l'istanza di SQL Server in **Crea database dei risultati dei test di carico nell'istanza di SQL Server seguente**.

> [!NOTE]
> Per altre informazioni sulla risoluzione dei problemi relativi ai test controller, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Gestire gli agenti quando si eseguono test con un test controller

Quando si aggiungono ruoli per l'applicazione alle impostazioni test per Visual Studio, è possibile aggiungere proprietà dell'agente per ognuno dei ruoli. Ciò determina quali agenti di test sono disponibili per il ruolo. Quando si eseguono i test usando tali impostazioni di test, il controller di test selezionato per le impostazioni di test determina la disponibilità degli agenti necessari. Quando viene determinata la disponibilità degli agenti, possono verificarsi le situazioni seguenti:

-   Non sono disponibili agenti per il ruolo che deve eseguire i test. Non è possibile eseguire i test. È possibile effettuare una delle azioni seguenti e quindi rieseguire i test:

    -   È possibile attendere che un agente diventi disponibile per il ruolo affinché possano essere eseguiti i test.

    -   Se sono presenti agenti attualmente offline utilizzabili per il ruolo, è possibile riavviare l'agente in modo che risulti disponibile.

    -   È possibile aggiungere al controller di test un altro agente con le proprietà corrette per il ruolo.

    -   È possibile modificare le proprietà dell'agente per il ruolo nelle impostazioni di test in modo da abilitare gli altri agenti che si desidera usare.

-   Non sono disponibili agenti per uno o più ruoli che eseguono adattatori dati di diagnostica. È possibile eseguire i test ma non l'adattatore dati di diagnostica. È possibile eseguire i test senza l'adattatore dati di diagnostica oppure effettuare una delle azioni seguenti e rieseguire i test:

    -   È possibile attendere che un agente diventi disponibile per i ruoli.

    -   Se sono presenti agenti attualmente offline utilizzabili per il ruolo, è possibile modificare lo stato dell'agente impostandolo su online scegliendo **Amministra controller test** dal menu **Test**. Potrebbe essere inoltre necessario riavviare l'agente se questo è stato disconnesso dal controller.

    -   Verificare che gli agenti che potrebbe essere necessario usare per l'esecuzione del test non siano occupati con altri test. È possibile controllare lo stato di qualsiasi agente scegliendo **Amministra controller test** dal menu **Test**.

    -   È possibile aggiungere al controller di test un altro agente con le proprietà corrette per il ruolo.

    -   È possibile modificare le proprietà dell'agente per il ruolo nelle impostazioni di test in modo da abilitare altri agenti che si desidera usare.

## <a name="load-tests-from-delay-signed-assemblies"></a>Caricare test da assembly di test con firma ritardata

I controller di test e gli agenti di test possono caricare solo assembly di test di carico con firma con nome sicuro o assembly non firmati. Per alcuni assembly di test viene usata la firma ritardata in quanto tali assembly devono accedere agli assembly di produzione per l'applicazione. Questi assembly, tuttavia, non dispongono di firma con nome sicuro in quanto si tratta solo di assembly di test, che non vengono distribuiti. Questi assembly non possono essere caricati poiché dispongono di firma ritardata, pertanto è necessario disabilitare la verifica del nome sicuro per tali assembly in tutti i computer in cui l'assembly verrà caricato, incluso il computer del controller di test. Per disabilitare la verifica con firma ritardata, usare sn.exe. Potrebbe essere necessario includere anche il token di chiave pubblica dell'assembly con firma ritardata per il quale viene richiesto di ignorare la verifica del nome sicuro.

Usare lo strumento Nome sicuro (Sn.exe) per disabilitare la verifica con firma ritardata.

La verifica dei nomi sicuri viene disabilitata, solo per l'assembly specificato, nel computer in cui viene eseguito il comando. È possibile eseguire questa operazione solo se si dispone di autorizzazioni sufficienti.

Dopo aver completato l'esecuzione dei test, abilitare nuovamente la verifica con firma ritardata tramite il comando SN.exe.

Per disabilitare e riabilitare la verifica della firma, si consiglia di usare i comandi SN.exe negli script. È possibile disabilitare la verifica in uno script di installazione e riattivarla in uno script di pulitura.

## <a name="see-also"></a>Vedere anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)