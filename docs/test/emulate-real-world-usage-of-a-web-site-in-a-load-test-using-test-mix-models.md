---
title: Emulazione dell'uso reale di un sito Web per l'esecuzione di test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 0458135040209f79648ca299bc56ba3acae21908
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="emulate-expected-real-world-usage-of-a-web-site-or-application-in-a-load-test-using-a-test-mix-models"></a>Emulazione dell'uso reale previsto di un'applicazione o un sito Web in un test di carico usando modelli di combinazione di test

È possibile usare le opzioni di modellazione del carico per prevedere più accuratamente il reale uso di un sito o un'applicazione Web sottoposti a test di carico. Tale procedura è importante perché un test di carico che non si basa su un modello di carico accurato può generare risultati fuorvianti.

## <a name="test-mix-model-enhancements"></a>Miglioramenti al modello di combinazione di test

Mediante l'Editor test di carico o la procedura guidata del modello di combinazione di test è possibile specificare i seguenti tipi di combinazione di test per uno scenario di test di carico. Per altre informazioni, vedere [Modifica del modello di combinazione di test in uno scenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

È possibile specificare una delle seguenti opzioni relative al modello di combinazione di test per lo scenario di test di carico:

-   **In base al numero totale di test:** determina quali test delle prestazioni Web o unit test vengono eseguiti quando un utente virtuale inizia un'iterazione di test. Alla fine del test di carico, il numero di volte in cui una determinata esecuzione dei test è risultata corrispondente alla distribuzione di test assegnata. Usare questo modello di combinazione di test quando si basa la combinazione di test sulle percentuali di transazioni in un log IIS o nei dati di produzione. Per altre informazioni, vedere [Percentuale basata sui test avviati](#BasedOnTestsStarted).

-   **In base al numero di utenti virtuali:** determina la percentuale di utenti virtuali che eseguiranno un determinato test delle prestazioni Web o unit test. Durante il test di carico, il numero di utenti che stanno eseguendo un determinato test corrisponde alla distribuzione assegnata. Utilizzare questo modello di combinazione di test quando si basa la combinazione di test sulla percentuale di utenti che sta eseguendo un determinato test. Per altre informazioni, vedere [Percentuale basata sugli utenti virtuali](#PercentageBasedonVirtualUsers).

-   **In base alla velocità dell'utente:** nel corso del test di carico ogni test delle prestazioni Web o unit test viene eseguito un numero specificato di volte per utente all'ora. Usare questo modello di combinazione di test quando si vuole che gli utenti virtuali eseguano il test a un ritmo determinato durante il test di carico. Per altre informazioni, vedere [Combinazione di test di velocità](#PacingTestMix).

    > [!TIP]
    > Quando scegliere **Combinazione di test di percentuale** e quando **Percentuale basata sugli utenti virtuali**? La differenza tra queste due scelte è importante quando alcuni test nella combinazione di test hanno una durata maggiore rispetto agli altri test. In questa situazione, è consigliabile scegliere **Percentuale basata sugli utenti virtuali**. Questa scelta consente di evitare esecuzioni di test di lunga durata. Se tuttavia i test sono tutti della stessa durata, è possibile scegliere **Combinazione di test di percentuale**.

-   **In base all'ordine sequenziale dei test:** ogni utente virtuale esegue il test delle prestazioni Web o unit test nell'ordine di definizione dei test nello scenario. L'utente virtuale continua a eseguire ciclicamente i test in questo ordine fino al completamento del test di carico. Per altre informazioni, vedere [Ordine sequenziale](#SequentialOrder).

###  <a name="BasedOnTestsStarted"></a> Percentuale basata sui test avviati
 Per ogni test della combinazione, è possibile specificare una percentuale che determina la frequenza di esecuzione del test successivo selezionato. Ad esempio, è possibile assegnare i seguenti valori in percentuale a tre test:

-   TestA (50%)

-   TestB (35%)

-   TestC (15%)

 Se si utilizza questa impostazione, l'avvio del test successivo si basa sulle percentuali assegnate. Non viene considerato il numero di utenti virtuali che stanno eseguendo attualmente ciascun test.

###  <a name="PercentageBasedonVirtualUsers"></a> Percentuale basata sugli utenti virtuali
 Questo modello di combinazione di test determina la percentuale di utenti virtuali che eseguiranno un determinato test. Se si utilizza questo modello di combinazione di test, l'avvio del successivo test si basa non solo sulle percentuali assegnate ma anche sulla percentuale di utenti virtuali che stanno eseguendo attualmente un determinato test. Durante il test di carico, il numero di utenti che stanno eseguendo un determinato test corrisponde il più possibile alla distribuzione assegnata.

###  <a name="PacingTestMix"></a> Combinazione di test di velocità
 Se si specifica una combinazione di test di velocità, si imposta una frequenza di esecuzione del test per ogni utente virtuale di ogni test nella combinazione di test. Per ogni test, questa frequenza viene espressa come test eseguiti per utente virtuale per ora. Ad esempio, è possibile assegnare la seguente combinazione di test di velocità a questi test:

-   TestA: 4 test per utente per ora

-   TestB: 2 test per utente per ora

-   TestC: 0,125 test per utente per ora

 Se si utilizza il modello di combinazione di test di velocità, il motore di runtime del test di carico garantisce che la frequenza effettiva di avvio dei test è minore o uguale alla frequenza specificata. Se la durata dell'esecuzione dei test è eccessiva per completare il numero assegnato, viene restituito un errore.

 L'impostazione **Tempo interazione utente tra due iterazioni test** non viene applicata quando si usa una combinazione di test di velocità.

#### <a name="applying-distribution-to-pacing-delay"></a>Applicazione della distribuzione al ritardo della velocità
 È possibile impostare il valore della proprietà **Applica distribuzione a ritardo velocità** in uno scenario di test di carico su True o False:

-   **True**: lo scenario applica ritardi di distribuzione statistici tipici specificati dal valore nella colonna **Test per utente all'ora** nella finestra di dialogo Modifica combinazione di test. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Presupporre ad esempio di avere il valore **Test per utente all'ora** nella finestra di dialogo Modifica combinazione di test impostato su 2 utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **True**, al tempo di attesa tra i test viene applicata una distribuzione statistica tipica. I test verranno ancora eseguiti in numero di 2 all'ora, ma non trascorreranno necessariamente 30 minuti tra le esecuzioni. Il primo test potrebbe venire eseguito dopo 4 minuti e il secondo test dopo 45 minuti.

-   **False**: i test verranno eseguiti al ritmo specificato per il valore della colonna **Test per utente all'ora** della finestra di dialogo Modifica combinazione di test. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Presupporre ad esempio di avere il valore **Test per utente all'ora** nella finestra di dialogo Modifica combinazione di test impostato su 2 utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **False**, non si prevede alcun intervallo di tolleranza nell'esecuzione dei test. Il test verrà eseguito ogni 30 minuti. In questo modo si è certi che verranno eseguiti 2 test all'ora.

 Per altre informazioni, vedere [Procedura: Applicare la distribuzione al ritardo velocità quando si usa un modello di combinazione di test basato sulla velocità dell'utente](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

###  <a name="SequentialOrder"></a> Ordine sequenziale
 La selezione dell'opzione In base a ordine sequenziale dei test consente a ogni utente virtuale di eseguire tutti i test nello scenario nell'ordine di definizione dei test.

## <a name="test-iterations-property"></a>Proprietà Iterazioni test
 Nelle proprietà Impostazioni di esecuzione è possibile specificare un valore per la proprietà Iterazioni test. Questo valore è il numero di iterazioni del test da eseguire in un test di carico. Dopo avere avviato il numero specificato di iterazioni di test, non verranno avviate altre iterazioni di test nonostante le impostazioni dei profili di carico. Dopo avere completato il numero specificato di iterazioni di test, il test di carico viene terminato. Per altre informazioni, vedere [Procedura: Specificare il numero di iterazioni test in un'impostazione di esecuzione](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Test di inizializzazione e terminazione
 È possibile selezionare i test da eseguire all'inizio e alla fine della sessione di test di carico di ciascun utente virtuale. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

-   **Test di inizializzazione**. Questo test viene eseguito da ciascun utente virtuale prima dell'esecuzione dei test nella combinazione di test.

-   **Test di terminazione**. Questo test viene eseguito dopo l'esecuzione di tutti i test di un determinato utente virtuale.

 Per i test di inizializzazione e terminazione osservare che:

-   È possibile specificare la durata del test di carico in base all'ora e non in base al conteggio di iterazioni. In questo caso, una volta completata la durata dell'esecuzione del test di carico, non verrà eseguito il test di terminazione.

-   Se il test di inizializzazione è uno unit test o un test Web, viene salvato lo stato dell'oggetto TestContext o WebTestContext dopo il completamento del test di inizializzazione. Verrà quindi utilizzato come contesto iniziale per le iterazioni dei test nella combinazione di test.

-   I nuovi utenti, in base alla definizione nella proprietà Percentuale di nuovi utenti dello scenario, eseguono sempre il test di inizializzazione, un'iterazione di un test dalla combinazione di test e il test di terminazione.

## <a name="see-also"></a>Vedere anche

- [Modifica di modelli di combinazione di testo per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Modifica dei modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modifica della combinazione di test per specificare quali test includere in uno scenario di test di carico](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modifica del modello di combinazione di test in uno scenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)