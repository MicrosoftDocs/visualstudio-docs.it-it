---
title: Configurare l'emulazione di rete tramite le impostazioni test in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 137f1980c53d457ef166008a438fca0effacbf44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Procedura: configurare l'emulazione di rete tramite le impostazioni test in Visual Studio

È possibile configurare l'adattatore dati di diagnostica per testare l'applicazione in vari ambienti di rete da Visual Studio. Può anche essere configurato per testare un carico di rete artificiale, o collo di bottiglia, quando si eseguono i test.

> [!WARNING]
> Se si eseguono i test in una rete reale, cioè un tipo più lento rispetto alla rete di cui viene eseguita l'emulazione, il test continuerà ad essere eseguito alla velocità di rete più lenta. L'emulazione può solo rallentare l'ambiente di rete, non renderlo più rapido.

 Nella procedura seguente viene illustrato come configurare l'emulazione di rete dall'editor di configurazione. La procedura è valida per l'editor di configurazione in Microsoft Test Manager e Visual Studio.

> [!NOTE]
> L'adattatore dati di diagnostica dell'emulazione di rete è applicabile solo alle impostazioni test di Visual Studio. Non viene usato per le impostazioni test in Microsoft Test Manager.

Per l'emulazione di rete è necessario usare un account con i privilegi di amministratore. Se è stata selezionata l'emulazione di rete per un ruolo locale che esegue test manuali, è necessario avviare Microsoft Test Manager usando privilegi di amministratore. Se è stata selezionata l'emulazione di rete per qualsiasi altro ruolo, è necessario verificare che l'agente di test nel computer per quel ruolo usi un account utente che è membro del gruppo Administrators. Per altre informazioni su come configurare l'account dell'agente di test, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> L'account Servizio di rete, che è l'account predefinito per l'agente di test, non è un membro del gruppo Administrators.

 **Emulazione di rete reale**

 Visual Studio utilizza l'emulazione di rete reale basata su software per tutti i tipi di test. Sono inclusi i test di carico. L'emulazione di rete reale simula le condizioni della rete tramite manipolazione diretta dei pacchetti di rete. L'emulatore di rete reale è in grado di emulare il comportamento di reti cablate e wireless tramite un collegamento fisico affidabile, ad esempio un cavo Ethernet. Gli attributi di rete seguenti sono incorporati nell'emulazione di rete reale:

-   Tempo di round trip nella rete (latenza)

-   Quantità di larghezza di banda disponibile

-   Comportamento di accodamento

-   Perdita di pacchetti

-   Riordinamento dei pacchetti

-   Propagazioni degli errori

 L'emulazione di rete reale offre anche flessibilità di filtro dei pacchetti di rete in base agli indirizzi IP o ai protocolli, ad esempio TCP, UDP e ICMP.

 L'emulazione di rete reale può essere usata dai tester e dagli sviluppatori basati su rete per emulare un ambiente di test desiderato, valutare le prestazioni, stimare l'impatto delle modifiche o prendere decisioni relative all'ottimizzazione della tecnologia. Rispetto ai dispositivi di test hardware, l'emulazione di rete reale è una soluzione molto più economica e flessibile.

## <a name="configure-network-emulation-for-your-test-settings"></a>Configurare l'emulazione di rete per le impostazioni di test
 Prima di eseguire i passaggi di questa procedura, è necessario aprire le impostazioni test da Visual Studio e selezionare la pagina **Dati e diagnostica**.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Per configurare l'emulazione di rete per le impostazioni di test

1.  Selezionare il ruolo da usare per emulare una rete specifica.

    > [!NOTE]
    > È necessario configurare l'adattatore di emulazione di rete solo sul ruolo client o sul ruolo server. Non è necessario usare l'adattatore su entrambi ruoli. L'adattatore emula il rumore nella rete che influisce sulla comunicazione tra entrambi i ruoli e non è pertanto necessario il suo uso su entrambi. A meno che non sia necessario il contrario, scegliere un ruolo client per l'adattatore di emulazione di rete per evitare sovraccarichi aggiuntivi sul ruolo server.

2.  Selezionare **Emulazione di rete**, quindi scegliere **Configura**.

     Verrà visualizzata la finestra di dialogo di configurazione dell'emulazione di rete.

3.  Scegliere la freccia accanto a **Seleziona il profilo di rete da utilizzare** e selezionare il tipo di rete che si vuole emulare quando si esegue un test, ad esempio **Cable-DSL 768Kps**.

    > [!WARNING]
    > Se si eseguono i test in una rete reale, cioè un tipo più lento rispetto alla rete di cui viene eseguita l'emulazione, il test continuerà ad essere eseguito alla velocità di rete più lenta. L'emulazione può solo rallentare l'ambiente di rete, non renderlo più rapido.

4.  Se si include l'adattatore dati di diagnostica dell'emulazione di rete nelle impostazioni di test e si vuole usarlo sul computer locale, è necessario anche associare il driver di emulazione di rete a una delle schede di rete del computer. Il driver di emulazione di rete è richiesto affinché l'adattatore dati di diagnostica dell'emulazione di rete funzioni. Il driver di emulazione di rete viene installato e associato all'adattatore in due modi:

    -   **Driver di emulazione di rete installato con Agente di test di Microsoft Visual Studio:** l'agente di test di Microsoft Visual Studio può essere usato sia nei computer remoti che nel computer locale. Quando si installa un agente di test di Visual Studio, il processo di installazione include un passaggio di configurazione che associa il driver di emulazione di rete alla scheda di rete. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

    -   **Driver di emulazione di rete installato con Microsoft Visual Studio Test Professional:** quando si usa l'emulazione di rete per la prima volta, viene richiesto di associare il driver di emulazione di rete a una scheda di rete.

    > [!TIP]
    > È anche possibile installare il driver di emulazione di rete dalla riga di comando nel computer locale senza installare l'agente di test di Visual Studio tramite il comando seguente: **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Vedere anche

- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Eseguire test manuali (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)