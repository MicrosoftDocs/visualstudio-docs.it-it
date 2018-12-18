---
title: Includere le registrazioni dello schermo e della voce durante i test tramite le impostazioni test in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 3888f9c07c02fa640c451f84f58243369ce1fda6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Procedura: includere le registrazioni dello schermo e della voce durante i test mediante le impostazioni test

Dall'editor di configurazione in Visual Studio è possibile configurare l'adattatore dati di diagnostica che registra lo schermo e la voce dell'utente che esegue il test. Con l'adattatore dati di diagnostica è possibile salvare una registrazione dello schermo e della voce della sessione desktop durante il test. La registrazione viene salvata con il risultato del test oppure può essere allegata a un bug. Gli altri membri del team possono utilizzare la registrazione per isolare i difetti dell'applicazione difficili da riprodurre.

> [!WARNING]
> Le registrazioni dello schermo e della voce non supportano configurazioni con più monitor.

La funzionalità di registrazione dello schermo e della voce può essere utilizzata con i test manuali o automatizzati. Ad esempio, se si esegue un test codificato dell'interfaccia utente in modalità remota è necessario registrare il desktop per visualizzare il test nel corso dell'esecuzione. Per altre informazioni su come acquisire una registrazione dello schermo e della voce in modalità remota, vedere [Procedura: Configurare l'agente di test per eseguire test che interagiscono con il desktop](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Per configurare la registrazione dello schermo e della voce per le impostazioni di test

1.  Aprire le impostazioni di test che si desidera configurare per la registrazione dello schermo e della voce. Per altre informazioni, vedere [Raccogliere dati diagnostici durante i test (VSTS)](/vsts/manual-test/collect-diagnostic-data) o [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

2.  Nelle impostazioni di test selezionare il **Ruolo** da usare per registrare lo schermo e la voce.

    > [!NOTE]
    > Per i test manuali e automatizzati, si tratta del computer in cui vengono eseguiti i test.

3.  Selezionare **Registrazione dello schermo e della voce**, quindi **Configura**.

     Verrà visualizzata la finestra di dialogo Configura adattatore dati di diagnostica - Registrazione dello schermo e della voce.

     ![Configurazione video](../test/media/testsettingvideoconfiggdr.png "TestSettingVideoConfigGDR")

4.  (Facoltativo) Selezionare **Abilita registrazione voce** per acquisire contenuti audio nella registrazione.

5.  (Facoltativo) Selezionare la casella di controllo accanto a **Salva registrazione in caso di superamento del test case** per specificare il salvataggio delle registrazioni dello schermo e della voce per i test superati e non superati.

    > [!WARNING]
    > Se si seleziona **Salva registrazione in caso di superamento del test case**, la registrazione viene archiviata con i risultati del test, usando spazio di archiviazione sul server. È possibile utilizzare lo strumento di pulizia allegati di test per pulire questi allegati.

6.  In **Qualità registrazione dello schermo** configurare le opzioni seguenti:

    1.  **Frequenza dei fotogrammi:** specificare il numero di fotogrammi al secondo da usare nella registrazione dello schermo e della voce. Il valore predefinito è 4 fotogrammi al secondo. È possibile specificare valori compresi tra 2 e 20.

    2.  **Velocità in bit:** specificare quanti KB al secondo usare nella registrazione dello schermo e della voce. Il valore predefinito è 512. È possibile specificare valori compresi tra 512 e 10.000.

    3.  **Qualità (1-100):** è possibile specificare la qualità della registrazione dello schermo e della voce selezionando un intervallo compreso tra 1 e 100. Il valore predefinito è 50 (intermedio).

7.  Scegliere **OK**. Le impostazioni dell'agente di raccolta traccia di diagnostica sono ora configurate e salvate per le impostazioni di test.

    > [!TIP]
    > Per reimpostare la configurazione dell'adattatore dati di diagnostica, scegliere **Reimposta configurazione predefinita** per Visual Studio e **Ripristina predefinito** per Microsoft Test Manager.

## <a name="see-also"></a>Vedere anche

- [Raccogliere dati di diagnostica durante i test (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Raccogliere dati di diagnostica nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Eseguire test manuali (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)