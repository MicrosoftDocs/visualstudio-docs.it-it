---
title: Modelli di carico per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7a6d9054bb12290d29247c09263a3854f2ea0dad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Modificare i modelli di carico per definire le attività di utenti virtuali

Le proprietà del modello di carico specificano come il carico utenti simulato viene regolato durante un test di carico. Visual Studio offre tre modelli di carico predefiniti: costante, per passaggio e basato su obiettivo. La scelta del modello di carico e la regolazione delle proprietà avvengono per ottenere livelli appropriati in base agli obiettivi del test di carico.

Il modello di carico è un componente di uno scenario. Gli scenari con i rispettivi modelli di carico definiti comprendono un test di carico.

> [!NOTE]
> In tutti i modelli di carico il carico generato da Visual Studio è un carico simulato di utenti virtuali.

## <a name="load-patterns"></a>Modelli di carico

### <a name="constant"></a>Costante

 Il modello di carico costante viene usato per specificare il carico di un utente che resta invariato durante il test di carico. Quando, ad esempio, si esegue uno "smoke test" in un'applicazione Web, potrebbe essere utile impostare un carico costante ridotto di 10 utenti.

#### <a name="constant-load-pattern-considerations"></a>Considerazioni sul modello di carico costante

 Un modello di carico costante viene usato per eseguire lo stesso carico utente durante l'esecuzione di un test di carico. Prestare particolare attenzione quando si utilizza un modello di carico costante con un numero elevato di utenti, perché si potrebbe creare una confluenza di richieste irragionevole e non realistica sul server o sui server all'inizio del test di carico. Se nel test di carico è incluso, ad esempio, un test Web che inizia con una richiesta a una home page e si configura il test di carico con un carico costante di 1.000 utenti, le prime 1.000 richieste verranno inviate alla home page il più velocemente possibile. Questa può non essere una simulazione realistica di un vero accesso al sito Web. Per ovviare a questo inconveniente, considerare la possibilità di usare un modello di carico passaggio che consente di aumentare gradualmente il carico a 1.000 utenti o specificare un periodo di riscaldamento nelle impostazioni per l'esecuzione di test di carico. Se si specifica un periodo di riscaldamento, il carico del test di carico aumenterà automaticamente durante tale periodo. Per altre informazioni, vedere [Configurazione di ritardi di avvio di uno scenario](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Passaggio

 Il modello del test di carico per passaggio viene usato per specificare il carico di un utente che aumenta con il passare del tempo fino a raggiungere il carico utente massimo definito. Nei carichi per passaggio è necessario specificare il **Numero utenti iniziale**, il **Numero massimo utenti**, l'**Intervallo passaggi (secondi)** e il **Numero utenti per passaggio**.

 Ad esempio, un carico per passaggio con un **Numero utenti iniziale** di uno, un**Numero massimo utenti** di 100, un **Intervallo passaggi (secondi)** di 10 e un **Numero utenti per passaggio** di 1 crea un modello di carico utente che comincia a 1, aumenta di 1 ogni 10 secondi fino a raggiungere 100 utenti.

> [!NOTE]
>  Se la durata totale del test è inferiore al tempo necessario per raggiungere il carico massimo di utenti, il test si interrompe al termine della durata specificata e non raggiunge l'obiettivo del Numero massimo utenti.

 È possibile utilizzare l'obiettivo Passaggio per aumentare il carico finché il server raggiunge un punto in cui le prestazioni diminuiscono significativamente. Con l'aumentare del carico, le risorse del server potrebbero esaurirsi. Il carico per passaggio è un buon metodo per stabilire con quale numero di utenti ciò si verifica. Quando il carico è in esecuzione, è necessario monitorare attentamente anche le risorse degli agenti per accertarsi che siano in grado di generare il carico desiderato.

 In genere è consigliabile eseguire più test con durate e numero di utenti dei passaggi differenti in modo da ottenere misurazioni attendibili per un determinato carico. Spesso i carichi mostrano un sovraccarico iniziale per ogni passaggio, man mano che vengono aggiunti gli utenti. Mantenendo il carico a questo livello, è possibile misurare le prestazioni del sistema dopo il ripristino in seguito al sovraccarico iniziale.

#### <a name="step-load-pattern-considerations"></a>Considerazioni sul modello di carico passaggio

 Un modello di carico passaggio può essere usato per aumentare il carico sul server o sui server durante l'esecuzione dei test di carico, in modo da visualizzare la variazione delle prestazioni mentre aumenta il carico utente. Per verificare, ad esempio, le prestazioni del server o dei server mentre il carico utente aumenta a 2.000 utenti, è possibile eseguire un test di carico di 10 ore utilizzando un modello di carico passaggio con le proprietà seguenti:

-   Numero utenti iniziale: 100

-   Numero massimo utenti: 2.000

-   Intervallo passaggi (secondi): 1.800

-   Tempo di preparazione passaggio (secondi): 20

-   Numero utenti per passaggio: 100

 Queste impostazioni consentono l'esecuzione del test di carico per 30 minuti (1.800 secondi) a carichi utente di 100, 200, 300, fino a 2.000 utenti. Una nota particolare merita la proprietà **Tempo di preparazione passaggio**, essendo la sola tra queste proprietà che non è disponibile per la selezione nella Creazione guidata test di carico. Questa proprietà consente l'aumento graduale, anziché immediato, da un passaggio al successivo (ad esempio da 100 a 200 utenti). In questo esempio il carico utente aumenterebbe da 100 a 200 utenti in un intervallo di 20 secondi, ovvero un aumento di 5 utenti al secondo. Per altre informazioni, vedere [Procedura: Specificare la proprietà relativa al tempo di preparazione del passaggio per un modello di carico passaggio](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Basato su obiettivo

 Un modello di carico basato su obiettivo è simile a un modello di carico per passaggio, ma regola il carico degli utenti in base alle soglie dei contatori delle prestazioni rispetto alle regolazioni periodiche del carico di utenti. I carichi basati su obiettivi sono utili per vari scopi: 

-   Massimizzare l'output degli agenti: misurare la metrica di limitazione principale sull'agente per massimizzare l'output degli agenti. In genere è la CPU, ma potrebbe anche essere la memoria.

-   Raggiungere un livello di risorse prefissato, di solito nella CPU, sul server di destinazione, quindi misurare la velocità effettiva a quel livello. Ciò consente di eseguire confronti da esecuzione a esecuzione sulla velocità effettiva di uno stesso livello di utilizzo delle risorse sul server.

-   Raggiungere sul server un livello prefissato di velocità effettiva.

 Nell'esempio della tabella riportata di seguito viene illustrato un modello basato su obiettivo con le seguenti impostazioni delle proprietà:

|Gruppo di proprietà|Proprietà|Valore|
|--------------------|--------------|-----------|
|Contatore prestazioni|Category|Processore|
|Contatore prestazioni|Computer|ContosoServer1|
|Contatore prestazioni|Counter|% Tempo processore|
|Contatore prestazioni|Istanza|_Total|
|Intervallo di destinazione per il contatore delle prestazioni|Estremità superiore|90|
|Intervallo di destinazione per il contatore delle prestazioni|Estremità inferiore|70|
|Limiti numero utenti|Numero utenti iniziale|1|
|Limiti numero utenti|Numero massimo utenti|100|
|Limiti numero utenti|Decremento massimo numero utenti|5|
|Limiti numero utenti|Incremento massimo numero utenti|5|
|Limiti numero utenti|Numero minimo utenti|1|

 Con queste impostazioni, tramite l'**Analizzatore test di carico** il carico di utenti viene regolato tra 1 e 100 durante l'esecuzione dei test in modo che il **Contatore** per `% Processor Time` di WebServer01 sia compreso tra `70%` e `90%.`

 Le dimensioni di ogni regolazione del carico utente sono determinate dalle impostazioni di **Incremento massimo numero utenti** e **Decremento massimo numero utenti**. I limiti per il numero di utenti vengono impostati dalle proprietà **Numero massimo utenti** e **Numero minimo utenti**.

#### <a name="goal-based-load-pattern-considerations"></a>Considerazioni sul modello di carico basato su obiettivo

 Un modello di carico basato su obiettivo è utile quando si desidera determinare il numero di utenti che il sistema è in grado di supportare prima di raggiungere un certo livello di utilizzo delle risorse. Questa opzione fornisce i migliori risultati quando è già stata identificata la risorsa limitante, ovvero il collo di bottiglia nel sistema.

 Ad esempio, si supponga di sapere che la risorsa limitante nel sistema sia la CPU sul server di database e si desidera vedere quanti utenti possono essere supportati nel caso in cui venga utilizzato circa il 75% della CPU sul server di database. È possibile utilizzare un modello di carico basato su obiettivo il cui scopo è quello di mantenere il valore del contatore delle prestazioni "% Tempo processore" tra il 70% e l'80%.

 Prestare attenzione qualora la velocità effettiva del sistema sia limitata da altre risorse. Tali risorse possono compromettere l'obiettivo specificato dal modello di carico basato su obiettivo. Il carico utente continuerà anche ad aumentare finché non sarà raggiunto il valore specificato in **Numero massimo utenti**. Non si tratta in genere del carico desiderato, pertanto prestare attenzione nella scelta del contatore delle prestazioni nel modello di carico basato su obiettivo.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Specifica del modello di carico iniziale per il test di carico:** quando si crea un test di carico tramite la Creazione guidata test di carico, è necessario selezionare un modello di carico.|-   [Modifica del modello di carico](../test/edit-load-patterns-to-model-virtual-user-activities.md#EditingLoadPatternsChanging)|
|**Modifica del modello di carico per il test di carico:** dopo aver creato il test di carico, è possibile modificare il modello di carico tramite l'Editor test di carico.|-   [Procedura: Specificare la proprietà relativa al tempo di preparazione del passaggio per un modello di carico passaggio](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Specifica dell'eventuale inclusione di dati della cache Web da parte di utenti virtuali nello scenario di test di carico:** è possibile modificare la proprietà **Percentuale di nuovi utenti** affinché influisca sulla modalità di simulazione con cui il test di carico simula la memorizzazione nella cache Web che verrebbe eseguita da un Web browser per gli utenti virtuali.|-   [Procedura: Specificare la percentuale di utenti virtuali che usano i dati della cache Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Specifica del tempo di preparazione passaggio per un modello di carico passaggio**: la proprietà **Tempo di preparazione passaggio** consente l'aumento graduale, anziché immediato, da un passaggio al successivo (ad esempio da 100 a 200 utenti).|-   [Procedura: Specificare la proprietà relativa al tempo di preparazione del passaggio per un modello di carico passaggio](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="changing-the-load-pattern"></a>Modifica del modello di carico

 Dopo avere creato il test di carico tramite la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà del modelli di carico associate a uno scenario a livelli che soddisfino gli obiettivi di test prefissati.

> [!NOTE]
>  Per un elenco completo delle proprietà di scenari dei test di carico e delle relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

 Con il modello di carico viene specificato il numero di utenti virtuali attivi durante un test di carico e la frequenza con cui vengono aggiunti nuovi utenti. È possibile scegliere tra tre modelli disponibili: modello per passaggio, costante e basato su obiettivo. Per altre informazioni, vedere [Specifica del numero di utenti virtuali con i modelli di carico in uno scenario di test di carico](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
>  È possibile inoltre modificare le proprietà di carico a livello di codice utilizzando un plug-in di test di carico. Per altre informazioni, vedere [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Per cambiare il modello di carico

1.  Aprire un test di carico.

2.  Nella cartella Scenari dell'**Editor test di carico** espandere lo scenario di cui si vuole modificare il modello di carico e scegliere il modello.

    > [!NOTE]
    > Il testo del nodo del modello di carico, così come viene visualizzato nell'albero dello scenario del test di carico, riflette il profilo di carico scelto al momento della creazione del test di carico. Può essere un **profilo Carico costante** o un **profilo Carico per passaggio**.

3.  Premere **F4** per visualizzare la finestra Proprietà.

     Le categorie **Modello di carico** e **Parametri** saranno visualizzate nella finestra Proprietà.

4.  (Facoltativo) Modificare la proprietà **Modello** nella categoria **Modello di carico**.

     Le scelte disponibili per **Modello** sono **Passaggio**, **Costante** e **Basato su obiettivo**. Per altre informazioni sui tipi di modelli di carico, vedere [Specifica del numero di utenti virtuali con i modelli di carico in uno scenario di test di carico](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (Facoltativo) Modificare i valori nella categoria **Parametri**.

    > [!NOTE]
    > I valori che è possibile impostare in **Parametri** variano in base al valore selezionato per la proprietà **Modello**.

6.  Dopo avere apportato le modifiche alle proprietà, scegliere **Salva** nel menu **File**. A questo punto sarà possibile eseguire il test di carico con il nuovo modello di carico.

## <a name="see-also"></a>Vedere anche

- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura: Specificare la percentuale di utenti virtuali che usano i dati della cache Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Procedura: Specificare la proprietà relativa al tempo di preparazione del passaggio per un modello di carico passaggio](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)