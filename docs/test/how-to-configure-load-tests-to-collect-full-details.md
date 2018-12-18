---
title: Raccogliere dettagli completi per gli utenti virtuali per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: d18a93fad0d113369f48e21ae74a08484b99485c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Procedura: configurare i test di carico per raccogliere i dettagli completi per abilitare l'attività utente virtuale nei risultati del test

Per usare il Grafico attività utente virtuale per il test di carico, è necessario configurare il test di carico per raccogliere dettagli completi. Per configurare il test di carico in questo modo, selezionare l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** associata al test di carico. In questa modalità, nel test di carico verranno raccolte informazioni dettagliate su ogni test, pagina e transazione.

 Se si aggiorna un progetto da una versione precedente di un test di carico di Visual Studio, usare i passaggi nella procedura seguente per abilitare la raccolta di dettagli completi.

 Per l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** sono disponibili le opzioni seguenti:

-   **Tutti i singoli dettagli:** vengono raccolti e archiviati dati di intervallo individuali per i singoli test, transazioni e pagine emessi nel corso del test.

    > [!NOTE]
    > È necessario selezionare l'opzione **Tutti i singoli dettagli** per abilitare le informazioni sui dati degli utenti virtuali nei risultati del test di carico.

-   **Nessuno:** non vengono raccolti dettagli di intervallo individuali. Sono tuttavia disponibili i valori medi.

-   **Solo statistiche:** vengono archiviati dati di intervallo individuali, ma solo come dati percentili. In questo modo, è possibile risparmiare spazio.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Per configurare la proprietà di archiviazione dei dettagli di intervallo in un test di carico

1.  Aprire un test di carico nell'Editor test di carico.

2.  Espandere il nodo **Impostazioni di esecuzione** nel test di carico.

3.  Scegliere le impostazioni di esecuzione test che si vuole configurare, ad esempio **Run Settings1[Active]**.

4.  Aprire la finestra Proprietà. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

5.  Nella categoria **Risultati** scegliere la proprietà **Intervallo archiviazione dettagli** e selezionare **Tutti i singoli dettagli**.

     Dopo aver configurato l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** è possibile eseguire il test di carico e visualizzare il Grafico attività utente virtuale. Per altre informazioni, vedere [Procedura: Analizzare le attività degli utenti virtuali durante un test di carico](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Vedere anche

- [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procedura dettagliata: uso del grafico attività utente virtuale per isolare i problemi](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)