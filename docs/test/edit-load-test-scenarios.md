---
title: Modifica di uno scenario di test di carico in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 69416ed6a4e06cccd606e705d97bef94d0825bd7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-test-scenarios"></a>Modificare gli scenari di test di carico

Uno *scenario* di test di carico consente di specificare il modello di carico, la combinazione di test, la combinazione di browser e la combinazione di reti. Gli scenari sono importanti perché consentono di configurare test con i quali simulare carichi di lavoro complessi e realistici.

È possibile, ad esempio, testare un sito di e-commerce con un front-end Internet usato da centinaia di clienti contemporaneamente, con diverse velocità di connessione e browser differenti. Lo stesso sito potrebbe anche essere dotato di funzioni di amministrazione, usate dai dipendenti interni per aggiornare i prodotti e visualizzare le statistiche. Generalmente questi utenti interni accedono al sito mediante lo stesso browser e una connessione LAN ad alta velocità. Sarebbe utile incapsulare le proprietà di questi due diversi gruppi di utenti in scenari distinti. Ogni scenario può contenere un tipo di utente virtuale. In questo caso può essere creato uno scenario di test di carico per rappresentare i clienti virtuali e può esserne creato un altro per rappresentare gli utenti interni virtuali di un sito Web.

## <a name="scenario-components"></a>Componenti di uno scenario

Tutte le opzioni e le impostazioni di configurazione iniziali specificate durante la creazione un test di carico possono essere modificate in un secondo momento nell'Editor test di carico. A un test di carico è anche possibile aggiungere nuovi scenari, impostazioni di esecuzione e insiemi di contatori.

![Scenari di test di carico](../test/media/loadtesteditinscenarios.png)

Gli scenari contengono i seguenti componenti:

|||
|-|-|
|Termine|Definizione|
|Combinazione di browser|Simula l'accesso di utenti virtuali a un sito Web tramite una serie di browser Web.|
|Modello di carico|Specifica il numero di utenti virtuali attivi durante un test di carico e la velocità con cui vengono avviati i nuovi utenti, ad esempio: modello per passaggio, costante e basato su obiettivo.|
|Modello di combinazione di test|Specifica la percentuale di probabilità che un utente virtuale esegua un determinato test in uno scenario di test di carico, ad esempio 20% di possibilità che venga eseguito il TestA e 80% che venga eseguito il TestB. Il modello di combinazione di test deve riflettere gli obiettivi del test per un determinato scenario.|
|Combinazione di test|La combinazione di test è la selezione dei test delle prestazioni Web e degli unit test che costituiscono lo scenario e la distribuzione di tali test.|
|Combinazione di reti|Simula l'accesso di utenti virtuali a un sito Web tramite una serie di connessioni di rete. La combinazione di reti offre diverse opzioni di connessione, tra cui LAN, modem via cavo e altre opzioni.|

Uno scenario è costituito anche da molte altre proprietà che è possibile modificare tramite l'Editor test di carico. Per altre informazioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Aggiungere pause di interazione umana artificiali nello scenario:** il tempo interazione utente consente di simulare il comportamento umano rispetto alle attese tra le interazioni con un sito Web. I tempi interazione utente intercorrono tra le richieste in un test Web e tra le interazioni test in uno scenario di test di carico. L'uso dei tempi interazione utente in un test di carico può essere utile per creare simulazioni di carico più accurate.|-   [Modifica dei tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md)|
|**Specificare il numero di utenti virtuali per lo scenario:** è possibile configurare le proprietà del modello di carico per specificare come viene regolato il carico utente simulato durante un test di carico. Sono disponibili tre modelli di carico incorporati: costante, per passaggio e basato su obiettivo. La scelta del modello di carico e la regolazione delle proprietà avvengono per ottenere livelli appropriati in base agli obiettivi del test di carico.|-   [Modifica dei modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Configurare la probabilità che un utente virtuale esegua un test nello scenario:** è possibile usare la combinazione di test per specificare la probabilità che un utente virtuale esegua un test specifico in uno scenario di test di carico. In questo modo, è possibile simulare un carico in maniera più realistica. Anziché avere un unico flusso di lavoro nelle applicazioni, è possibile avere più flussi di lavoro in modo da ottenere una migliore approssimazione della modalità di interazione degli utenti finali con le applicazioni.|-   [Modifica di modelli di combinazione di test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Aggiungere o rimuovere un test delle prestazioni Web o uno unit test da uno scenario di test di carico:** è possibile aggiungere o rimuovere un test delle prestazioni Web o uno unit test da un test di carico di uno scenario. Un test di carico contiene uno o più scenari, ciascuno dei quali contiene uno o più test delle prestazioni Web o unit test.|-   [Modifica della combinazione di test](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurare la combinazione di reti necessaria per lo scenario:** usando la combinazione di reti, è possibile simulare più realisticamente il carico di rete in uno scenario di test di carico. Il carico viene generato usando una combinazione di reti eterogenea anziché un solo tipo di rete. Viene creata una maggiore approssimazione dell'interazione degli utenti finali con le applicazioni. Il modello di combinazione di reti deve riflettere gli obiettivi di quello scenario.|-   [Specifica dei tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Selezionare la combinazione di Web browser appropriata per lo scenario:** usando la combinazione di browser, è possibile simulare più realisticamente il carico Web in uno scenario di test di carico. Il carico viene generato usando una combinazione eterogenea di browser anziché un solo browser. Viene quindi creata una migliore approssimazione dei browser che saranno usati nelle applicazioni.|-   [Specifica dei tipi di Web browser](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurare le impostazioni delle interazioni del test per lo scenario**: usando l'Editor test di carico e la finestra Proprietà, è possibile modificare uno scenario di test di carico per configurare le impostazioni delle iterazioni del test. Per impostazione predefinita, un scenario viene configurato senza il numero massimo di iterazioni. facoltativamente, è possibile configurare il numero massimo di iterazioni nello scenario e l'intervallo tra un'iterazione e l'altra.|-   [Configurazione di iterazioni di test in uno scenario](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Configurare le impostazioni di ritardo per lo scenario:** usando l'Editor test di carico e la finestra Proprietà, è possibile specificare un ritardo prima di avviare uno scenario in un test di carico. La proprietà **Ritarda ora di inizio** può ad esempio essere utile quando è necessario che in uno scenario venga avviata la produzione di articoli usati in un altro scenario. È possibile ritardare il secondo scenario per consentire al primo di popolare i dati.|-   [Configurazione di ritardi di avvio di uno scenario](../test/configure-scenario-start-delays.md)|
|**Specificare computer remoti da usare in uno scenario di test di carico:** dopo aver creato un test di carico, è possibile modificare le proprietà dello scenario di test di carico e indicare gli agenti di test da includere. Per altre informazioni, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).|-   [Procedura: Specificare agenti di test da usare](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Vedere anche

- [Modifica di un test di carico](../test/edit-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)