---
title: Risoluzione dei problemi dei controller e degli agenti di test in Visual Studio | Microsoft Docs
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 3d785a559ff59a96861798a7c96bfdcb4147b7ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie di risoluzione dei problemi dei controller e degli agenti di test nei test di carico

Questo articolo descrive alcuni problemi comuni che possono verificarsi quando si usano controller di test e agenti di test in Visual Studio.

##  <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Impossibile raccogliere i contatori delle prestazioni nel computer agente di test

 Quando si esegue un test di carico, è possibile ricevere errori se si tenta di connettersi a un computer agente di test e raccogliere i contatori delle prestazioni. Il Registro di sistema remoto è il servizio responsabile di fornire i dati dei contatori delle prestazioni a un computer remoto. In alcuni sistemi operativi il servizio Registro di sistema remoto non viene avviato automaticamente. Per correggere questo problema, avviare manualmente il servizio Registro di sistema remoto.

> [!NOTE]
>  È possibile accedere al servizio Registro di sistema remoto nel **Pannello di controllo.** Scegliere **Strumenti di amministrazione** e quindi **Servizi**.

 Il problema potrebbe anche essere causato dalla mancata disponibilità di autorizzazioni sufficienti per leggere i contatori delle prestazioni. Per le esecuzioni di test locali, l'account dell'utente che esegue il test deve essere un membro del gruppo Power Users o superiore oppure del gruppo Performance Monitor Users. Per le esecuzioni di test remote, l'account per cui è configurata l'esecuzione del controller deve essere un membro del gruppo Power Users o superiore oppure del gruppo Performance Monitor Users.

## <a name="setting-the-logging-level-on-a-test-controller-computer"></a>Impostazione del livello di registrazione in un computer controller di test
 È possibile controllare il livello di registrazione in un computer controller di test. Questa funzione è utile quando si tenta di diagnosticare un problema durante l'esecuzione di un test di carico in un ambiente.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Per impostare il livello di registrazione in un computer controller di test

1.  Arrestare il servizio controller di test. Al prompt dei comandi digitare `net stop vsttcontroller`.

2.  Aprire file QTController.exe.config. Questo file si trova nella directory di installazione del controller.

3.  Modificare la voce per l'opzione `EqtTraceLevel` nella sezione del file relativa alla diagnostica di sistema. Il codice sarà simile a quello riportato di seguito:

    ```
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4.  Salvare il file.

5.  Avviare il servizio controller. Al prompt dei comandi digitare `net start vsttcontroller`.

 Questa procedura si applica al controller di test, al servizio agente di test e al processo agente di test. Quando si diagnosticano problemi, risulta utile attivare la registrazione su tutti e tre i processi. La procedura per impostare il livello di registrazione è identica per i tre processi, come specificato in precedenza per il controller di test. Per impostare i livelli di registrazione per il servizio agente di test e per il processo agente, utilizzare i file di configurazione seguenti:

-   **QTController.exe.config** Servizio controller

-   **QTAgentService.exe.config** Servizio agente

-   **QTDCAgent(32).exe.config** Processo dell'adattatore dati dell'agente per l'architettura a 32 bit.

-   **QTDCAgent(64).exe.config** Processo dell'adattatore dati dell'agente per l'architettura a 64 bit.

-   **QTAgent(32).exe.config** Processo di test dell'agente per l'architettura a 32 bit.

-   **QTAgent(64).exe.config** Processo di test dell'agente per l'architettura a 64 bit.

## <a name="binding-a-test-controller-to-a-network-adapter"></a>Associazione di un controller di test a una scheda di rete
 Quando si tenta di configurare un agente di test, potrebbe verificarsi l'errore seguente:

 **Errore 8110. Impossibile connettersi al controller specificato o accedere all'oggetto controller.**

 Questo errore può essere causato dall'installazione del controller di test in un computer con più di una scheda di rete.

> [!NOTE]
>  È anche possibile installare correttamente gli agenti di test e non riscontrare il problema finché non si tenta di eseguire un test.

 Per correggere questo errore, è necessario associare il controller di test a una delle schede di rete. Impostare la proprietà `BindTo` nel controller di test e quindi modificare l'agente di test in modo che faccia riferimento al controller di test in base all'indirizzo IP anziché al nome. I passaggi vengono illustrati nelle procedure seguenti.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Per ottenere l'indirizzo IP della scheda di rete

1.  Scegliere **Start** e quindi **Esegui**.

     Viene visualizzata la finestra di dialogo **Esegui**.

2.  Digitare `cmd` e quindi scegliere **OK**.

     Verrà aperto un prompt dei comandi.

3.  Digitare `ipconfig /all`.

     Verranno visualizzati gli indirizzi IP delle schede di rete. Registrare l'indirizzo IP della scheda di rete da associare al controller.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Per associare un controller di test a una scheda di rete

1.  Arrestare il servizio controller di test. Al prompt dei comandi digitare `net stop vsttcontroller`.

2.  Aprire file QTController.exe.config. Questo file si trova in %Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

3.  Aggiungere una voce per la proprietà `BindTo` alle impostazioni dell'applicazione. Specificare l'indirizzo IP della scheda di rete da associare al controller. Il codice sarà simile a quello riportato di seguito:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4.  Salvare il file.

5.  Avviare il servizio controller di test. Al prompt dei comandi digitare `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Per connettere un agente di test a un controller associato

-   Eseguire nuovamente l'installazione dell'agente di test. Questa volta, specificare l'indirizzo IP anziché il nome del controller di test.

 Questa procedura si applica al controller di test, al servizio agente di test e al processo agente di test. La proprietà `BindTo` deve essere impostata per ogni processo in esecuzione in un computer che dispone di più schede di rete. La procedura per impostare la proprietà `BindTo` è identica per i tre processi, come specificato in precedenza per il controller di test. Per impostare i livelli di registrazione per il servizio agente di test e il processo agente di test, usare i file di configurazione elencati in [Impostazione del livello di registrazione in un computer controller di test](#Logging).

## <a name="see-also"></a>Vedere anche

- [Test controller e agenti di test](../test/configure-test-agents-and-controllers-for-load-tests.md)