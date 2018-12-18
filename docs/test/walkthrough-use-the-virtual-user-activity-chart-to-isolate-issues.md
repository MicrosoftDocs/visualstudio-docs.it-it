---
title: Uso del grafico attività utente virtuale per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7cf4d2d31bb037aba8af95caf5ffab1d7be2c132
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Procedura dettagliata: utilizzo del grafico attività utente virtuale per isolare i problemi

In questa procedura dettagliata verrà illustrato come usare il Grafico attività utente virtuale per isolare gli errori che si verificati per utenti virtuali singoli che hanno eseguito il test di carico.

 Il Grafico attività utente virtuale consente di visualizzare l'attività degli utenti virtuali associata al test di carico. Ogni riga del grafico rappresenta un singolo utente virtuale. Il Grafico attività utente virtuale mostra esattamente l'attività eseguita da ogni utente virtuale durante il test. Ciò consente di isolare i problemi di prestazioni visualizzando i modelli dell'attività utente e i modelli di carico, correlare test non riusciti o lenti e vedere le richieste con l'attività di altri utenti virtuali. Il Grafico attività utente virtuale è disponibile solo al termine dell'esecuzione del test di carico.

 In questa procedura dettagliata, si completeranno le attività seguenti:

-   Apprendere come usare i seguenti strumenti associati al Grafico attività utente virtuale:

    -   Usare lo strumento **Zoom periodo di tempo** per specificare un periodo di tempo specifico sul grafico che si vuole analizzare.

    -   Usare i pannelli **Legenda dettagli** e **Risultati filtro** per applicare un filtro al grafico e facilitare l'isolamento dei problemi.

-   Usare il Grafico attività utente virtuale per analizzare un errore che si è verificato per un utente virtuale specifico e visualizzare i dettagli del tipo di errore.

 Per altre informazioni, vedere [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Prerequisiti

-   Visual Studio Enterprise

-   Completare queste procedure:

    -   [Registrare ed eseguire un test prestazioni Web](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef).

    -   [Creare ed eseguire un test di carico](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Aprire la soluzione ColorWebApp creata nelle procedure dettagliate precedenti

### <a name="open-the-solution"></a>Aprire la soluzione

1.  Avviare Visual Studio.

2.  Aprire la soluzione ColorWebApp contenente LoadTest1.loadtest. Questo test di carico è il risultato dell'esecuzione dei passaggi delle tre procedure dettagliate indicate all'inizio di questo argomento nella sezione dei prerequisiti.

     I passaggi restanti in questa procedura dettagliata presuppongono l'esistenza di un'applicazione Web denominata ColorWebApp, un test delle prestazioni Web denominato ColorWebAppTest.webtest e un test di carico denominato LoadTest1.loadtest.

## <a name="run-the-load-test"></a>Eseguire il test di carico
 Eseguire il test di carico per raccogliere i dati dell'attività utente virtuale.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Eseguire il test di carico per raccogliere i dati dell'attività utente virtuale

-   Nell'Editor test di carico scegliere **Esegui** sulla barra degli strumenti. LoadTest1 inizia l'esecuzione.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Isolare problemi nel Grafico attività utente virtuale

Dopo avere eseguito il test di carico e raccolto i dati dell'attività utente virtuale, è possibile visualizzare i dati nei risultati del test di carico usando la visualizzazione Dettagli dell'analizzatore test di carico nel Grafico attività utente virtuale. Inoltre, è possibile usare il Grafico attività utente virtuale per facilitare l'isolamento dei problemi di prestazioni nel test di carico.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Per usare il Grafico attività utente virtuale nei risultati del test di carico

1.  Al termine dell'esecuzione del test di carico, viene visualizzata la pagina di riepilogo dei risultati del test nell'analizzatore test di carico. Nella barra degli strumenti scegliere il pulsante **Grafici**.

     Verrà aperta la visualizzazione Grafici.

2.  Nel grafico **Tempo di risposta per pagina** fare clic con il pulsante destro del mouse accanto a una delle icone di violazione di soglia e selezionare **Vai a dettagli utente**.

    > [!NOTE]
    > È possibile usare anche il pulsante **Dettagli** nella barra degli strumenti dell'Editor test di carico per aprire il grafico attività utente. Se si usa l'opzione **Vai a dettagli utente**, tuttavia, il Grafico attività utente virtuale eseguirà automaticamente lo zoom sulla parte del test sulla quale si è fatto clic con il pulsante destro del mouse nel grafico.

     La visualizzazione Dettagli viene visualizzata con il **Grafico attività utente virtuale** concentrato sul periodo di tempo in cui si sono verificate le violazioni di soglia.

     Sull'asse y, i tracciati orizzontali rappresentano utenti virtuali singoli. L'asse x visualizza la cronologia dell'esecuzione del test di carico.

3.  Nello strumento **Zoom periodo di tempo** in **Grafico attività utente virtuale** regolare i dispositivi di scorrimento sinistro e destro fino a che entrambi non saranno vicini all'icona di violazione di soglia. In questo modo viene modificata la scala temporale nel **Grafico attività utente virtuale**

4.  In **Legenda dettagli** selezionare la casella di controllo per **(Evidenzia errori)**. Notare che l'utente virtuale che provocato la violazione di soglia è evidenziato.

5.  Nel pannello **Risultati filtro** deselezionare le caselle di controllo per **Mostra risultati corretti** e **Errore HTTP** ma lasciare la casella di controllo **Errore regola di convalida** selezionata.

     Nel **Grafico attività utente virtuale** vengono visualizzati solo gli utenti virtuali che hanno trascorso più di 3 secondi sulla pagina Red.aspx, come specificato dalla violazione di soglia configurata nella procedura dettagliata precedente.

6.  Posizionare il puntatore del mouse sulla linea orizzontale che rappresenta l'utente virtuale con l'errore della regola di convalida per la violazione di soglia.

7.  Viene visualizzata una descrizione comando con le informazioni seguenti:

    -   **ID utente**

    -   **Scenario**

    -   **Test**

    -   **Risultato**

    -   **Network**

    -   **Ora di inizio**

    -   **Durata**

    -   **Agente**

    -   **Log test**

8.  Si noti che **Log test** è un collegamento. Scegliere il collegamento **Log test**.

9. Il test delle prestazioni Web ColorWebTest associato al log si apre nel Visualizzatore risultati test prestazioni Web. Ciò consente di isolare i punti in cui si sono verificate le violazioni di soglia.

     È possibile usare varie impostazioni nei pannelli **Legenda dettagli** e **Risultati filtro** per facilitare l'isolamento dei problemi di prestazioni e degli errori nei test di carico. Provare varie combinazioni di queste impostazioni e lo strumento **Zoom periodo di tempo** per vedere come i dati utente virtuale vengono presentati nel **Grafico attività utente virtuale**.

## <a name="see-also"></a>Vedere anche

- [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Procedura: Creare un'impostazione test per un test di carico distribuito](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)