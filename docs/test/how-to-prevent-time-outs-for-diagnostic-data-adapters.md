---
title: Timeout per gli adattatori dati di diagnostica in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 61572a323fa29892096c963ad94a5e201dd61ec9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Procedura: impedire i timeout per gli adattatori dati di diagnostica

Se si utilizzano adattatori dati di diagnostica nelle impostazioni test, è possibile che si verifichi un timeout quando si inizia l'esecuzione dei test a causa di uno dei motivi seguenti:

-   Il servizio controller di test non è in esecuzione nel computer del controller di test. Potrebbe essere necessario riavviare il servizio. Per altre informazioni su come determinare il test controller e gestire i test controller, vedere [Gestione di test controller e agenti di test con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Se si raccolgono dati in un computer remoto, Microsoft Test Manager potrebbe essere bloccato dal firewall. È necessario che nel computer che esegue Microsoft Test Manager vengano accettate connessioni in ingresso dal test controller. Si verifica un timeout quando in Microsoft Test Manager non viene ricevuto un messaggio dal controller bloccato dal firewall. È necessario controllare le impostazioni del firewall nel computer in cui è in esecuzione Microsoft Test Manager. Per altre informazioni sulle impostazioni del firewall, vedere il [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=184980) seguente.

-   Il test controller non può risolvere il nome del computer che esegue Microsoft Test Manager. Ciò potrebbe verificarsi se dal DNS viene fornito l'indirizzo errato per questo computer. Per risolvere questo problema potrebbe essere necessario contattare l'amministratore di rete.

 Quando si esegue un test lungo durante il quale devono essere raccolti molti dati, è possibile che si verifichi un timeout. Per risolvere il problema, è possibile attenersi alla procedura riportata di seguito.

 È possibile aumentare il timeout aggiornando il file di configurazione per Microsoft Test Manager o il file di configurazione per l'agente di test per il quale si verifica il timeout.

 Il file di configurazione per Microsoft Test Manager è denominato **mtm.exe.config**. Il file è disponibile nella directory seguente: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

 Per aggiornare un agente di test, è necessario aggiornare i file di configurazione seguenti nel computer dell'agente di test. Tutti questi file sono memorizzati nel computer dell'agente di test nella stessa directory: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 Se si eseguono test manuali e si raccolgono dati da un ambiente, quando viene creato un bug o il test case viene completato, tutti i dati raccolti dagli adattatori dati di diagnostica vengono trasferiti al computer in cui vengono eseguiti i test manuali. Se sono stati raccolti molti dati o si dispone di una connessione di rete lenta, potrebbe essere necessario più tempo del valore predefinito di 60 secondi. Se ad esempio è stato configurato l'adattatore IntelliTrace per raccogliere eventi IntelliTrace e informazioni sulle chiamate per molti processi, il trasferimento di tali dati potrebbe superare il timeout predefinito. Per aumentare questo valore, è possibile attenersi alla procedura riportata di seguito per aggiornare **mtm.exe.config**.

 Un messaggio di errore viene visualizzato se si verifica il timeout dell'attività Test Runner o di un agente di test. Nel messaggio di errore per l'agente di test saranno presenti le informazioni sulle quali si è verificato il timeout nel computer dell'agente di test. Utilizzare la procedura riportata di seguito per aggiornare i file di configurazione, a seconda del messaggio di errore ricevuto.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Per aumentare i timeout per gli adattatori dati di diagnostica

1.  Aprire una finestra Esplora risorse (o Esplora file).

     A questo scopo, fare clic con il pulsante destro del mouse su **Start** e scegliere **Esplora**.

    > [!NOTE]
    > Occorre disporre dei privilegi amministrativi per aggiornare il file.

2.  Individuare la directory nel computer *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* che contiene il file da aggiornare.

3.  Fare clic con il pulsante destro del mouse sul file, quindi fare clic su **Apri con**. Selezionare un editor.

     Il file verrà aperto nell'editor. Molte impostazioni sono archiviate in questo file. La maggior parte delle impostazioni può essere modificata usando Microsoft Test Manager. Le impostazioni di timeout devono essere modificate manualmente, come descritto nei passaggi seguenti.

4.  È necessario modificare la sezione delle impostazioni di esecuzione dei test per aumentare i valori di timeout. Questa sezione presenta il formato seguente:

    ```
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Per aumentare il tempo che gli adattatori dati di diagnostica attendono per il completamento degli eventi, aumentare il valore della chiave **DataCollectorEventTimeoutInSeconds**

6.  Se il messaggio di errore di timeout riguarda l'attività Test Runner, è necessario aumentare il valore della chiave **RunOperationTimeoutInSeconds**.

7.  Per aumentare il timeout impostato per il trasferimento dei dati raccolti per un bug o quando termina un test nel computer in cui vengono eseguiti i test, è necessario aggiungere il timeout seguente nella sezione appSettings del file **mtm.exe.config**:

    ```
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > Il valore di timeout è espresso in millisecondi.

8.  Salvare le modifiche apportate al file e rieseguire i test per i quali si era verificato il timeout.

## <a name="see-also"></a>Vedere anche

- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)