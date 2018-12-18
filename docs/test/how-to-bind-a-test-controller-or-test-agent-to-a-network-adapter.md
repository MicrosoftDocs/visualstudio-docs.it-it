---
title: Associare un test controller o un agente di test a una scheda di rete in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 79aef9a4ad15f364df00dfd4ee6c7f1d7925c281
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Procedura: Associare un test controller o un agente di test a una scheda di rete

Se un computer con installato il software del test controller o dell'agente di test dispone di più schede di rete, è necessario specificare l'indirizzo IP anziché il nome del computer per identificare il test controller o l'agente di test.

> [!WARNING]
> Quando si tenta di configurare un agente di test, potrebbe verificarsi l'errore seguente:
>
> **Errore 8110. Impossibile connettersi al controller specificato o accedere all'oggetto controller**
>
> Questo errore può essere causato dall'installazione del controller di test in un computer con più di una scheda di rete. È anche possibile installare correttamente gli agenti e non riscontrare il problema finché non si tenta di eseguire un test.

## <a name="binding-a-test-controller-to-a-specific-network-adapter"></a>Associazione di un controller di test a una scheda di rete specifica

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Per ottenere gli indirizzi IP delle schede di rete

1.  In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **cmd** e quindi scegliere **INVIO**.

2.  Digitare **ipconfig /all**.

     Verranno visualizzati gli indirizzi IP delle schede di rete. Registrare l'indirizzo IP della scheda di rete da associare al controller.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Per associare un adattatore di rete a un controller di test

1.  In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **services.msc** e quindi scegliere **INVIO**.

     Viene visualizzata la finestra di dialogo **Servizi**.

2.  Nel riquadro dei risultati, nella colonna **Nome** fare clic con il pulsante destro del mouse sul servizio **Visual Studio Test Controller** e quindi scegliere **Arresta**.

     oppure

     Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente nella riga di comando:

     `net stop vsttcontroller`

3.  Aprire il file di configurazione XML *QTCcontroller.exe.config* che si trova in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Individuare il tag `<appSettings>`.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5.  Aggiungere la chiave `BindTo` per specificare gli adattatori di rete da utilizzare nella sezione `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Avviare il servizio controller di test. A tale scopo, eseguire il comando seguente dal prompt dei comandi:

    `net start vsttcontroller`

    > [!WARNING]
    > Per connettere l'agente di test al controller è necessario eseguire nuovamente l'installazione dell'agente di test. Questa volta, specificare l'indirizzo IP anziché il nome del controller.

     Questa procedura si applica al controller, al servizio agente e al processo agente. La proprietà `BindTo` deve essere impostata per ogni processo in esecuzione in un computer che dispone di più schede di rete. La procedura per impostare la proprietà `BindTo` è identica per i tre processi, come specificato più indietro in questo argomento per il controller di test.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Per associare una scheda di rete a un agente di test

1.  In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **services.msc** e quindi scegliere **INVIO**.

    Viene visualizzata la finestra di dialogo **Servizi**.

2.  Nel riquadro dei risultati, nella colonna **Nome** fare clic con il pulsante destro del mouse sul servizio **Agente di test di Visual Studio** e quindi scegliere **Arresta**.

     oppure

     Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente nella riga di comando:

     **net stop vsttagent**

3.  Aprire il file di configurazione XML *QTAgentService.exe.config* che si trova in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Individuare il tag `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5.  Aggiungere la chiave `BindTo` per specificare gli adattatori di rete da utilizzare nella sezione `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Avviare il servizio agente di test. A tale scopo, eseguire il comando seguente dal prompt dei comandi:

    `net start vsttagent`

## <a name="see-also"></a>Vedere anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
- [Modifica delle impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md)
- [Configurazione delle porte per controller e agenti di test](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Procedura: Impostare la dimensione massima per il file di log](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Procedura: Specificare i periodi di timeout per controller e agenti di test](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)