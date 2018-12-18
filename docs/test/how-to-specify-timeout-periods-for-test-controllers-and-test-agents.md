---
title: Periodi di timeout per test controller e agenti di test in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 067dee39ade864cd0e0211ed8fd27d8f8fd3d9c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Procedura: specificare i periodi di timeout per controller e agenti di test

Sia il controller di test che l'agente di test dispongono di diverse impostazioni di timeout che consentono di specificare il tempo che ognuno di essi deve attendere per le risposte dell'altro, o per quelle provenienti da un'origine dati, prima di generare un errore. In determinate circostanze potrebbe essere necessario modificare i valori di timeout per far fronte alle necessità della topologia o ad altre problematiche legate all'ambiente. Per cambiare i valori di timeout, modificare il file di configurazione XML associato al controller di test o all'agente di test, come illustrato nelle procedure riportate di seguito.

 Per modificare le varie impostazioni del timeout di un agente di test o controller di test, modificare i seguenti file di configurazione utilizzando i nomi di chiavi e i valori riportati di seguito nelle tabelle:

-   Controller di test: QTController.exe.config

    |Nome della chiave|Descrizione|Valore|
    |--------------|-----------------|-----------|
    |AgentConnectionTimeoutInSeconds|Numero di secondi di attesa per la richiesta di ping dell'agente prima che la connessione venga considerata persa.|"n" secondi.|
    |AgentSyncTimeoutInSeconds|Quando si avvia l'esecuzione di un test di sincronizzazione, il numero di secondi di attesa per la sincronizzazione di tutti gli agenti prima di interrompere l'esecuzione.|"n" secondi.|
    |AgentInitializeTimeout|Numero di secondi di attesa per l'inizializzazione di tutti gli agenti e dei relativi agenti di raccolta dati all'inizio dell'esecuzione di un test prima di interrompere l'esecuzione. Questo valore deve essere sufficientemente alto in caso di utilizzo di agenti di raccolta dati.|"n" secondi. Predefinito: "120" (due minuti).|
    |AgentCleanupTimeout|Numero di secondi di attesa per la pulizia di tutti gli agenti e dei relativi agenti di raccolta dati prima del completamento dell'esecuzione di un test. Questo valore deve essere sufficientemente alto in caso di utilizzo di agenti di raccolta dati.|"n" secondi. Predefinito: "120" (due minuti).|

-   Agente di test: QTAgentService.exe.config

    |Nome della chiave|Descrizione|Valore|
    |--------------|-----------------|-----------|
    |ControllerConnectionPeriodInSeconds|Numero di secondi tra tentativi di connessione al controller.|"n" secondi. Predefinito: "30" (trenta secondi).|
    |RemotingTimeoutSeconds|Tempo massimo che una chiamata remota può durare in secondi.|"n" secondi. Predefinito: "600" (dieci minuti).|
    |StopTestRunCallTimeoutInSeconds|Numero di secondi di attesa che una chiamata interrompa l'esecuzione del test.|"n" secondi. Predefinito: "120" (due minuti).|
    |GetCollectorDataTimeout|Numero di secondi per i quali attendere l'agente di raccolta dati.|"n" secondi. Predefinito: "300" (cinque minuti).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Per specificare le opzioni di timeout agente per un controller di test

1. Aprire il file di configurazione XML QTCcontroller.exe.config che si trova in %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

2. Individuare il tag `<appSettings>`.

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

3. Modificare un valore esistente con uno delle chiavi di timeout del controller di test. Ad esempio, è possibile modificare il valore predefinito per la chiave `AgentConnectionTimeoutInSeconds` da due minuti a tre minuti:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    oppure

    Aggiungere un'altra chiave e specificare un valore di timeout. È ad esempio possibile aggiungere la chiave `AgentInitializeTimeout` nella sezione `<appSettings>` e specificare un valore di cinque minuti:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Per specificare le opzioni di timeout agente per un agente di test

1. Aprire il file di configurazione XML QTAgentService.exe.config che si trova in %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

2. Individuare il tag `<appSettings>`.

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

3. Modificare un valore esistente con uno delle chiavi di timeout dell'agente di test. È ad esempio possibile modificare il valore predefinito per la chiave `ControllerConnectionPeriodInSeconds` da trenta secondi a un minuto:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    oppure

    Aggiungere un'altra chiave e specificare un valore di timeout. È ad esempio possibile aggiungere la chiave `RemotingTimeoutSeconds` nella sezione `<appSettings>` e specificare un valore di quindici minuti:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Vedere anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
- [Modifica delle impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md)
- [Configurazione delle porte per controller e agenti di test](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Procedura: Impostare la dimensione massima per il file di log](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Procedura: Associare un controller di test o un agente di test a una scheda di rete](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)