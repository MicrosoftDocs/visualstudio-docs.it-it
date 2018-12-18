---
title: Assegnazione di ruoli a un test controller e a un agente di test per l'esecuzione di test automatizzati in Visual Studio | Microsoft Docs
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 932a6fe470812fc647cad653fb95ba7ca8997ab0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Assegnare ruoli a un test controller e a un agente di test

Questa procedura dettagliata descrive come creare e configurare un'impostazione test in cui vengono usati un controller di test e agenti di test per distribuire i test a diversi computer usando Visual Studio. Viene inoltre descritto come aggiungere adattatori dati e diagnostici all'impostazione di test.

In questa procedura dettagliata, si completeranno le attività seguenti:

-   Creare un'impostazione di test.

-   Assegnare ruoli a un test controller e agli agenti di test.

-   Assegnare un adattatore dati e un adattatore diagnostico all'impostazione di test.

## <a name="prerequisites"></a>Prerequisiti

-   Creare unit test o test codificati dell'interfaccia utente da eseguire con l'impostazione di test.

-   Installare un test controller e agenti di test. Per informazioni su come installare un test controller e agenti di test, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Per creare e configurare un'impostazione di test

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Elementi di soluzione**, scegliere **Aggiungi** e quindi **Nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

2.  Nel riquadro **Modelli installati** fare clic su **Impostazioni test**.

3.  Nella casella **Nome** digitare **TestSettingDistributedTestWalkthrough**.

4.  Scegliere **Aggiungi**.

     Il nuovo file di test TestSettingDistributedTestWalkthrough.testsettings viene visualizzato nella cartella **Elementi di soluzione** in Esplora soluzioni.

     Verrà visualizzata la finestra di dialogo **Impostazioni test**. È selezionata la pagina **Generale**.

     È quindi possibile modificare e salvare i valori delle impostazioni di test.

    > [!NOTE]
    > Ogni impostazione test creata viene elencata tra le opzioni disponibili per **Seleziona impostazioni test attive** e **Modifica impostazioni test** nel menu **Test**.

5.  In **Nome** digitare il nome per le impostazioni di test.

6.  In **Descrizione** digitare **Impostazioni test distribuito**.

7.  Lasciare selezionata l'opzione **Schema di denominazione predefinito**.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Per assegnare ruoli a un test controller e agli agenti di test

1.  Scegliere **Ruoli**.

     Verrà visualizzata la pagina **Ruoli**.

2.  Per eseguire il test in modalità remota, usare l'elenco a discesa **Metodo di esecuzione dei test** e selezionare **Esecuzione remota**.

3.  Nell'elenco a discesa **Controller** digitare il nome del computer del [controller di test](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Se si aggiunge un controller per la prima volta, nell'elenco a discesa non saranno presenti controller. L'elenco viene popolato da controller precedenti specificati in altre impostazioni di test.

4.  In **Ruoli** scegliere **Aggiungi**.

5.  Nella riga evidenziata nella colonna **Nome** digitare **Test distribuito**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Per assegnare un adattatore dati e un adattatore diagnostico all'impostazione di test

1.  Scegliere **Dati e diagnostica**.

     Verrà visualizzata la pagina **Dati e diagnostica**.

2.  In **Ruolo** verificare che il ruolo **Test distribuito** sia selezionato.

3.  In **Dati e diagnostica per il ruolo selezionato** selezionare gli adattatori **IntelliTrace** e **Informazioni di sistema**.

     Per informazioni su questi e altri adattatori che è possibile usare in un'impostazione test, vedere [Configurare unit test](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Scegliere **Host**.

5.  (Facoltativo) Se nel computer viene eseguita una versione a 64 bit di Microsoft Windows e il test è stato compilato con la configurazione **Qualsiasi CPU**, usare l'elenco a discesa **Esegui test in un processo a 32 bit o a 64 bit** e selezionare **Esegui test in un processo a 64 bit in un computer a 64 bit**.

    > [!TIP]
    > Per la massima flessibilità, è consigliabile compilare i progetti di test con la configurazione **Qualsiasi CPU**. È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. Non esiste alcun vantaggio nel compilare i progetti di test con la configurazione **64 bit**.

6.  Per salvare le nuove impostazioni di test, scegliere **Applica**.

7.  Scegliere **Chiudi**.

8.  Scegliere **Seleziona impostazioni test** attive dal menu Test e quindi scegliere **TestSettingDistributedTestWalkthrough.testsettings**.

9. Eseguire il test nel modo abituale.

     Quando il controller di test elabora unit test e test codificati dell'interfaccia utente, il controller di test divide i test in gruppi di 100 e li invia a un computer dell'agente di test. Ad esempio, se sono presenti 250 unit test e tre agenti di test, i primi 100 unit test verranno inviati ad agente1, i successivi 100 unit test verranno inviati ad agente2 e i restanti 50 unit test verranno inviati a agente3.

## <a name="see-also"></a>Vedere anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)