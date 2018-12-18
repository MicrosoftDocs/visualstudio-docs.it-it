---
title: Creare ed eseguire un test di carico in Visual Studio | Microsoft Docs
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: cc59ffe0e394a89f8277470a2fcf9099aedccbbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Procedura dettagliata: Creare ed eseguire un test di carico contenente unit test

In questa procedura dettagliata viene creato un test di carico contenente unit test.

Questa procedura descrive i passaggi necessari per la creazione e l'esecuzione di un test di carico tramite Visual Studio Enterprise. Un test di carico è un contenitore di test Web e unit test. È possibile creare test di carico con la Creazione guidata test di carico.

In un test di carico sono presenti anche molte proprietà di runtime che possono essere modificate per generare la simulazione di carico desiderata. In questa procedura dettagliata viene utilizzata la Creazione guidata test di carico per aggiungere unit test a un test di carico.

In questa procedura dettagliata, si completeranno le attività seguenti:

-   Creare un test di carico in cui vengono utilizzati unit test.

-   Modifica di alcune impostazioni di un test di carico.

-   Esecuzione di un test di carico.

-   Eseguire i passaggi descritti in [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) per creare una libreria di classi C# semplice contenente un progetto di test di carico e prestazioni Web con alcuni unit test.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Creare un test di carico contenente unit test utilizzando la Creazione guidata test di carico

### <a name="to-start-the-new-load-test-wizard"></a>Per avviare la Creazione guidata test di carico

1.  Aprire la soluzione Bank creata nella [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione Bank, scegliere **Aggiungi** e quindi **Nuovo progetto**.

     Viene visualizzata la finestra di dialogo Aggiungi nuovo progetto.

3.  Nella finestra di dialogo Aggiungi nuovo progetto espandere **Visual C#** e scegliere **Test**. Nell'elenco di modelli scegliere **Progetto di test di carico e prestazioni Web** e, nel campo **Nome**, digitare `BankLoadTest`. Scegliere **OK**.

     Il progetto di test di carico e prestazioni Web di BankLoadTest viene aggiunto alla soluzione.

4.  Aprire il menu di scelta rapida per il nuovo progetto di test di carico e prestazioni Web di BankLoadTest, scegliere **Aggiungi** e quindi **Test di carico**.

5.  Viene avviata la **Creazione guidata test di carico**.

6.  La pagina di **Benvenuto** della **Creazione guidata test di carico** è la prima pagina.

7.  Scegliere **Avanti**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Per modificare le impostazioni per uno scenario di test di carico

1.  Nella casella di testo **Immettere un nome per lo scenario di test di carico** digitare **ScenarioSample**.

     Uno *scenario* è un meccanismo di raggruppamento. È composto da una serie di test e di proprietà per l'esecuzione di tali test sotto carico.

2.  Impostare il **Profilo tempo interazione utente** su `Use normal distribution centered on recorded think times`. Il tempo interazione utente rappresenta il tempo che un utente dedica a una pagina Web prima di passare alla successiva.

1.  Al termine scegliere **Avanti**.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Per modificare l'impostazione del modello di carico per lo scenario di test

1.  Scegliere **Carico per passaggio**.

    > [!NOTE]
    > È possibile scegliere da due tipi di modelli di carico: costante e per passaggio. Ogni tipo ha una funzione specifica nell'ambito dei test di carico. Ai fini di questa procedura dettagliata scegliere **Carico per passaggio**.

2.  Impostare **Numero iniziale utenti** su 10 utenti.

3.  Impostare **Durata passaggio** su 10 secondi.

4.  Impostare **Numero utenti per passaggio** su 10 utenti per passaggio.

5.  Impostare **Numero massimo utenti** su 100 utenti.

6.  Scegliere **Avanti**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Per selezionare un modello di combinazione di test per lo scenario

1.  In Specificare il modello di combinazione di test selezionare **In base al numero totale di test**.

2.  Scegliere **Avanti**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Per aggiungere unit test allo scenario

1.  Il passaggio successivo consente di **aggiungere test a uno scenario di test di carico e modificare una combinazione di test**.

2.  Scegliere **Aggiungi** per selezionare i test.

3.  Scegliere lo unit test CreditTest elencato nel riquadro **Test disponibili**, in cui sono visualizzati tutti i test di prestazioni Web e gli unit test nel progetto di test di carico e prestazioni Web.

4.  Scegliere la freccia per aggiungere lo unit test CreditTest al riquadro **Test selezionati**.

5.  Ripetere i passaggi 3 e 4 per gli unit test DebitTest e FreezeAccountTest.

6.  Dopo avere aggiunto i tre unit test, scegliere **OK**.

     Viene visualizzata una combinazione di test.

7.  Spostare leggermente il dispositivo di scorrimento sotto Distribuzione per CreditTest per regolare la distribuzione del test. Si noti che gli altri dispositivi di scorrimento si spostano automaticamente verso sinistra, in modo che la distribuzione rimanga uguale a 100%.

8.  Scegliere **Avanti**.

### <a name="to-select-network-mix-for-test-scenario"></a>Per selezionare la combinazione di reti per lo scenario di test

1.  Selezionare il tipo di connessione LAN da aggiungere alla combinazione della larghezza di banda della rete.

     È possibile aggiungere altri tipi di rete. Utilizzare i dispositivi di scorrimento per regolare la distribuzione e il peso dei test.

2.  Scegliere **Avanti**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Per specificare i computer da monitorare con gli insiemi di contatori durante l'esecuzione del test di carico

1.  Scegliere **Avanti**.

     Per altre informazioni sugli insiemi di contatori, vedere [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Per modificare l'impostazione di esecuzione per il test di carico

1.  Selezionare **Durata test di carico** e quindi impostare **Durata esecuzione** su 2 minuti per eseguire uno *smoke test* del test di carico.

     Quando vengono compilati i test di carico, è consigliabile verificare di avere impostato tutto correttamente e che tutto funzioni come previsto eseguendo un breve test di carico ridotto. Questo processo è noto come *smoke test*.

2.  Scegliere **Fine**. Il testo di carico si apre nell'**Editor test di carico**.

## <a name="running-the-load-test"></a>Esecuzione del test di carico
 Una volta creato il test di carico, eseguirlo per visualizzare il modo in cui l'applicazione bancaria risponde alla simulazione di carico. Mentre il test di carico è in esecuzione, viene visualizzata la finestra **Analizzatore test di carico**.

### <a name="to-run-the-load-test"></a>Per eseguire il test di carico

1.  Dopo aver aperto un test di carico nell'**Editor test di carico**, scegliere il pulsante verde **Esegui test** sulla barra degli strumenti. Il test di carico viene eseguito.

2.  Se la simulazione di test supera una o più soglie, nei nodi del controllo albero vengono visualizzate icone per indicare la violazione di soglia. Gli errori sono indicati da un cerchio rosso, gli avvisi da un triangolo giallo. Per individuare il contatore che ha superato la soglia e tracciarne il grafico, trascinare l'icona sul grafico. Questa operazione può essere effettuata durante l'esecuzione del test.

## <a name="see-also"></a>Vedere anche

- [Modifica della combinazione di test per specificare quali test includere in uno scenario di test di carico](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Specifica dei tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Modifica dei modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modifica di modelli di combinazione di testo per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)