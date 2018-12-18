---
title: Insiemi di contatori e regole di soglia per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: d2b80ab1aaed9f5f59399a02026c9334f38701c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Specificare insiemi di contatori e regole di soglia per i computer in un test di carico

I test di carico rendono disponibili insiemi di contatori denominati, utili per analizzare i dati dei contatori delle prestazioni. Gli insiemi di contatori sono organizzati in base alla tecnologia e includono Applicazione, ASP.NET, Applicazione .NET, IIS, e SQL. Quando si crea un test di carico usando la **Creazione guidata test di carico**, è necessario aggiungere un insieme di contatori iniziale. Ciò offre una serie di insiemi di contatori predefiniti e importanti per eseguire il test di carico. I contatori vengono gestiti nell'**Editor test di carico**.

> [!NOTE]
> Se i test di carico vengono distribuiti in computer remoti, viene eseguito il mapping dei contatori di controller e agenti ai relativi set. Per altre informazioni sull'uso dei computer remoti nel test di carico, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

Gli insiemi di contatori vengono raggruppati sui computer specificati dall'utente. L'associazione tra un insieme di contatori e un computer usata durante un test di carico viene definita *mapping dell'insieme di contatori*. Il server Web che si sta testando potrebbe, ad esempio, disporre di mapping di insiemi di contatori per applicazioni ASP.NET, IIS e .NET.

Per impostazione predefinita i contatori di prestazioni sono raccolti sul controller e sugli agenti. Per altre informazioni, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

È importante aggiungere i server in fase di test all'elenco dei computer sui quali raccogliere i contatori. Tutti i dati importanti del sistema verranno quindi raccolti e monitorati durante il test di carico.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Gestire gli insiemi di contatori per il test di carico:** dopo aver creato un test di carico, è possibile modificare l'insieme di contatori nell'Editor test di carico. La gestione degli insiemi di contatori implica la scelta del gruppo di computer da cui raccogliere i dati sulle prestazioni e l'assegnazione di una serie di insiemi di contatori da raccogliere da ogni singolo computer. I contatori vengono gestiti nell'Editor test di carico.|-   [Procedura: Gestire insiemi di contatori](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Aggiungere insiemi di contatori al test di carico:** quando si crea un test di carico con la Creazione guidata test di carico, si aggiunge un insieme di contatori iniziale. Ciò offre una serie di insiemi di contatori predefiniti per il test di carico. Dopo aver creato un test di carico, è possibile aggiungere i nuovi contatori agli insiemi di contatori esistenti utilizzando l'Editor test di carico.|-   [Procedura: Aggiungere contatori agli insiemi di contatori](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Procedura: Aggiungere insiemi di contatori personalizzati](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Specificare una regola di soglia usando i contatori per il test di carico:** una regola di soglia è una regola impostata per un singolo contatore delle prestazioni per monitorare l'uso delle risorse di sistema durante un test di carico. Le definizioni degli insiemi di contatori contengono regole di soglia predefinite per molti contatori di prestazioni principali. Le regole di soglia nei test di carico consentono di confrontare il valore di un contatore delle prestazioni con il valore di una costante o di un altro contatore delle prestazioni.|-   [Procedura: Aggiungere una regola di soglia](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Assegnare nomi descrittivi ai computer ai quali sono mappati gli insiemi di contatori:** è possibile aggiungere tag computer che consentono di applicare un nome facilmente riconoscibile a un computer. I tag vengono visualizzati nel nodo **Mapping insiemi di contatori** nella struttura ad albero dell'Editor test di carico. Inoltre, i tag vengono visualizzati nei rapporti di Excel che consentono agli stakeholder di identificare il ruolo del computer nel test di carico, ad esempio "Web Server1 in lab2" o "SQL Server2 in Phoenix office".<br /><br /> Per altre informazioni, vedere [Creazione di report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md).|-   [Procedura: Aggiungere tag computer ai mapping dell'insieme di contatori](../test/how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor.md)|

## <a name="use-counter-sets"></a>Usare gli insiemi di contatori

Gli strumenti del test di carico consentono di raccogliere e riprodurre in un grafico i dati delle prestazioni utilizzando i contatori nel tempo. I dati dei contatori vengono raccolti a intervalli di tempo specificati dall'utente durante l'esecuzione di un test di carico. Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento](../test/how-to-specify-the-sample-rate-for-a-load-test.md). È possibile visualizzare i contatori in fase di esecuzione o dopo l'esecuzione di un test di carico usando l'*Analizzatore test di carico*.

I dati del contatore vengono raccolti nel server e in tutti i computer su cui viene eseguito un test. Se è stato configurato un set di computer agenti in cui eseguire i test, i contatori vengono raccolti anche in questi computer.

Esistono tre categorie di contatori: percentuali, conteggi e medie. Alcuni esempi sono la percentuale di utilizzo della CPU, i conteggi dei blocchi di SQL Server e le richieste IIS al secondo.

![Insiemi di contatori dei test di carico](../test/media/loadtestcountersets.png "LoadTestCounterSets")

I dati delle prestazioni per le singole richieste HTTP vengono segnalati dal computer che esegue un test, ad esempio un computer agente. Per le richieste è possibile monitorare i dati quali Tempo medio ricezione primo byte, Tempo di risposta e Media richieste al secondo.

Per semplificare la raccolta dei dati delle prestazioni in un server Web, in Visual Studio Enterprise sono disponibili anche insiemi di contatori predefiniti e denominati, basati sulla tecnologia per l'uso nei test di carico. Questi insiemi si rivelano utili quando occorre analizzare un server che esegue IIS, ASP.NET o SQL Server. Tramite l'Editor test di carico è possibile aggiungere ulteriori contatori all'insieme di contatori predefinito. È importante aggiungere al test di carico i computer o i server sottoposti a test per assicurarsi che sia possibile eseguire il monitoraggio dell'utilizzo delle risorse in tali computer. Per altre informazioni, vedere [Procedura: Gestire insiemi di contatori](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

L'analisi dei risultati delle esecuzioni di test di carico necessita spesso di conoscenze specifiche del dominio di una particolare area, per sapere esattamente quali dati raccogliere, dove impostare le regole di soglia e come segnalare quando una misurazione rivela un problema specifico nell'applicazione. Per altre informazioni, vedere [Informazioni sulle regole di soglia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md#SpecifyingCounterSetsThresholdRulesAboutThresholdRules).

### <a name="performance-counter-sampling-interval-considerations"></a>Considerazioni sull'intervallo di campionamento dei contatori delle prestazioni

Nelle impostazioni esecuzione test di carico selezionare un valore appropriato per la proprietà **Frequenza di campionamento** in base alla durata del test di carico. Una frequenza di campionamento inferiore, ad esempio il valore predefinito di cinque secondi, richiede più spazio nel database dei risultati del test di carico. Per i test di carico più lunghi, l'aumento della frequenza di campionamento riduce la quantità di dati raccolti. Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Di seguito sono riportate alcune linee guida per le frequenze di campionamento.

|Durata test di carico|Frequenza di campionamento consigliata|
|------------------------|-----------------------------|
|\< 1 ora|5 secondi|
|1 - 8 ore|15 secondi|
|8 - 24 ore|30 secondi|
|> 24 ore|60 secondi|

## <a name="store-performance-data"></a>Archiviare i dati sulle prestazioni

Durante l'esecuzione di un test di carico, i dati del contatore delle prestazioni vengono raccolti e archiviati nel *repository dei risultati del test di carico*. Per altre informazioni, vedere [Gestione dei risultati dei test di carico nel repository dei risultati del test di carico](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Informazioni sulle regole di soglia

La *regola di soglia* è una regola impostata su un singolo contatore delle prestazioni per monitorare l'uso delle risorse di sistema durante un test di carico. Le definizioni degli insiemi di contatori contengono regole di soglia predefinite per molti contatori di prestazioni principali. Per altre informazioni, vedere [Uso di insiemi di contatori per analizzare i dati del contatore di prestazioni nei test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Regole di soglia e livelli

Quando si creano le regole di soglia nei test di carico, è necessario scegliere tra due tipi di regola:

Confronta costante&mdash;Consente di eseguire un confronto del valore del contatore delle prestazioni con un valore costante.

Confronta contatori&mdash;Consente di eseguire un confronto del valore del contatore delle prestazioni con un altro valore del contatore delle prestazioni.

Quando si creano le regole di soglia, è inoltre necessario impostare i livelli per la regola, ossia il valore soglia di avviso e il valore soglia critico. Quando si visualizza l'esecuzione di un test di carico, le violazioni dei valori soglia di avviso sono indicate da un simbolo giallo, mentre le violazioni dei valori soglia critici da un simbolo rosso.

## <a name="the-alert-if-over-property"></a>Proprietà Avvisa se supera

Impostare la proprietà **Avvisa se supera** su **True** per indicare che il superamento della soglia è un problema. Ad esempio, se la regola di soglia è impostata su **% tempo processore** e si vuole ricevere un avviso se il valore è maggiore di 90, usare il tipo di regola **Confronta costante**, impostare **Valore soglia critico** su 90 e impostare **Avvisa se supera** su **True**.

Impostare la proprietà **Avvisa se supera** su **False** per indicare che il non raggiungimento della soglia è un problema. Ad esempio, se la regola di soglia è impostata su **Richieste/sec** e si vuole ricevere un avviso se il valore è minore di 50, usare il tipo di regola **Confronta costante**, impostare **Valore soglia critico** su 50 e impostare **Avvisa se supera** su **False**.

## <a name="see-also"></a>Vedere anche

- [Procedura: Aggiungere una regola di soglia](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)