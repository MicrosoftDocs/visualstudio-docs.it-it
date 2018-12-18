---
title: Sviluppare test da un modello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: db4fdcf6a672188ef00ab61cfdbb15395c596cec
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="develop-tests-from-a-model"></a>Sviluppare test da un modello
È possibile usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e altre parti interessate e consente di aggiornare rapidamente i test quando cambiano i requisiti. Se si usa [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], è anche possibile gestire i collegamenti tra i modelli e i test.

 Per le versioni di Visual Studio che supportano queste funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Test di sistema e di sottosistema
 *Test di sistema* noto anche come *test di accettazione*, significa test se vengono soddisfatte le esigenze degli utenti. Questi test riguardano il comportamento del sistema visibile esternamente piuttosto che la progettazione interna.

 I test di sistema sono molto utili quando è necessario estendere o riprogettare un sistema e permettono di evitare di introdurre bug quando si modifica il codice.

 Quando si pianifica una qualsiasi modifica o estensione di un sistema, è utile iniziare con un set di test di sistema da eseguire nel sistema esistente. È quindi possibile estendere o modificare i test per testare i nuovi requisiti, apportare le modifiche al codice e rieseguire il set di test completo.

 Quando si sviluppa un nuovo sistema, è possibile iniziare a creare i test contestualmente all'inizio dello sviluppo. Se i test vengono definiti prima di sviluppare ogni funzionalità, è possibile avviare discussioni sui requisiti in modo molto specifico.

 Il test di sottosistema applica gli stessi principi ai componenti principali di un sistema. Ogni componente viene testato separatamente dagli altri componenti. l test di sottosistema sono incentrati sul comportamento visibile nelle interfacce utente o nell'API del componente.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Derivazione dei test di sistema da un modello di requisiti
 È possibile creare e gestire una relazione tra i test di sistema e un modello di requisiti. Per stabilire questa relazione, si scrivono test che corrispondono agli elementi principali del modello di requisiti. Visual Studio facilita il mantenimento di tale relazione permettendo di creare collegamenti tra i test e le parti del modello. Per ulteriori informazioni sui modelli di requisiti, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Scrivere test per ogni caso di utilizzo
 Se si usa [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], è possibile creare un gruppo di test per ogni caso di utilizzo definito nel modello di requisiti. Se ad esempio si ha un caso di utilizzo Ordinazione pasto che include Creazione ordine e Aggiunta elemento all'ordine, è possibile creare i test sia per i casi di utilizzo in generale che per quelli più dettagliati.

 Le linee guida seguenti possono risultare utili:

-   Ogni caso di utilizzo deve avere diversi test, per i percorsi principali e i risultati eccezionali.

-   Quando si descrive un caso di utilizzo nel modello di requisiti, è più importante definire la postcondizione, ovvero l'obiettivo da raggiungere, che descrivere in dettaglio le procedure che l'utente segue per raggiungere l'obiettivo. Ad esempio, la postcondizione di Ordinazione pasto potrebbe essere che un ristorante stia preparando un pasto per un cliente e che il cliente abbia pagato. La postcondizione è il criterio che i test devono verificare.

-   Basare test distinti sulle clausole separate della postcondizione. Ad esempio, creare test distinti per notificare l'ordine al ristorante e per accettare il pagamento dal cliente. Questa separazione offre i vantaggi seguenti:

    -   Le modifiche dei diversi aspetti dei requisiti si verificano spesso indipendentemente. La creazione di test separati per i vari aspetti consente di aggiornare più facilmente i test se vengono modificati i requisiti.

    -   Se il piano di sviluppo implementa un aspetto del caso di utilizzo prima di un altro, è possibile abilitare i test separatamente in base all'avanzamento dello sviluppo.

-   Quando si progettano i test, separare la scelta dei dati di test dal codice o dallo script che determina se la postcondizione è stata raggiunta. Ad esempio, il test di una funzione aritmetica semplice, può essere: Input 4; verificare che l'output sia 2. Progettare invece lo script come: Scegliere un input; moltiplicare l'output per se stesso e verificare che il risultato sia l'input originale. Questo stile consente di variare gli input del test senza modificare il corpo principale del test.

#### <a name="linking-tests-to-use-cases"></a>Collegamento di test ai casi di utilizzo
 Se si utilizza [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] per progettare ed eseguire i test, è possibile organizzare i test in elementi di lavoro storia utente, requisito o caso d'uso. È possibile collegare questi elementi di lavoro ai casi di utilizzo del modello, in modo da tenere traccia rapidamente delle modifiche dei requisiti nei test, oltre che dello stato di avanzamento di ogni caso di utilizzo.

###### <a name="to-link-tests-to-a-use-case"></a>Per collegare i test a un caso di utilizzo

1.  In [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] creare un requisito e usarlo come base per un gruppo di test.

     Il requisito creato è un elemento di lavoro in [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Può essere un elemento di lavoro Storia utente, Requisito o Caso di utilizzo, a seconda del modello di processo usato dal progetto con [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Per ulteriori informazioni, vedere [tenere traccia del lavoro tramite Visual Studio Team Services o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2.  Collegare l'elemento di lavoro requisito a uno o più casi di utilizzo del modello.

     In un diagramma caso d'uso, fare doppio clic su un caso d'uso e quindi fare clic su **Collega a elemento di lavoro**.

3.  Aggiungere al gruppo di test i test case che verificano i casi di utilizzo.

 In genere, ogni elemento di lavoro storia utente o requisito viene collegato a diversi casi di utilizzo del modello e ogni caso di utilizzo viene collegato a diverse storie utente o diversi requisiti. Ogni storia utente o requisito riguarda infatti un set di attività che sviluppano diversi casi di utilizzo. Ad esempio, in una prima iterazione del progetto, è possibile sviluppare la storia utente di base in cui un cliente può scegliere gli elementi da un catalogo e richiederne la consegna. In un'iterazione successiva la storia potrebbe essere sviluppata in modo tale che l'utente paghi al completamento dell'ordine e il fornitore riceva il denaro dopo avere inviato i prodotti.  Ogni storia aggiunge una clausola alla postcondizione del caso di utilizzo Ordinazione prodotti.

 È possibile creare collegamenti separati dai requisiti alle clausole della postcondizione scrivendo le clausole in commenti separati nel diagramma caso di utilizzo. È possibile collegare ogni commento a un elemento di lavoro requisito e collegare il commento al caso di utilizzo nel diagramma.

### <a name="base-tests-on-the-requirements-types"></a>Creare test in base ai tipi di requisiti
 I tipi, ovvero classi, interfacce ed enumerazioni, di un modello di requisiti descrivono i concetti e le relazioni delineando cosa pensano gli utenti dell'azienda e come comunicano la propria idea. Sono esclusi i tipi riguardanti solo la progettazione interna del sistema.

 Progettare i test in base a questi tipi di requisiti. In questo modo, quando vengono discusse le modifiche ai requisiti, sarà più facile correlare le modifiche alle modifiche necessarie nei test. È anche possibile discutere dei test e dei risultati previsti direttamente con gli utenti finali e le altre parti interessate. Questo significa che le esigenze degli utenti possono essere gestite al di fuori del processo di sviluppo, evitando la progettazione accidentale di test sui possibili difetti di progettazione.

 Per i test manuali questa procedura implica il rispetto del vocabolario del modello di requisiti negli script di test. Per i test automatizzati questa procedura comporta l'uso di diagrammi classi di requisiti come base per il codice del test e la creazione di funzioni di accesso e di aggiornamento per collegare il modello di requisiti al codice.

 Ad esempio, un modello di requisiti potrebbe includere i tipi Menu, Elemento menu, Ordine e le associazioni tra di essi. Questo modello rappresenta le informazioni archiviate e gestite dal sistema di ordinazione dei pasti, ma non rappresenta le complessità dell'implementazione. Nel sistema lavorativo potrebbero esserci diverse realizzazioni di ogni tipo, nei database, nelle interfacce utente e nelle API. In un sistema distribuito potrebbero esserci diverse varianti di ogni istanza archiviata contemporaneamente in diverse parti del sistema.

 Per testare un caso di utilizzo quale Aggiunta elemento all'ordine, un metodo di test potrebbe includere codice simile al seguente:

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Si noti che questo metodo di test usa le classi del modello di requisiti. Le associazioni e gli attributi sono rappresentati come proprietà .NET.

 Perché questo sia possibile, è necessario che le proprietà delle classi siano definite come funzioni di sola lettura o funzioni di accesso a cui il sistema accede per recuperare le informazioni sullo stato corrente. I metodi che simulano i casi di utilizzo, come AddItemToOrder, devono usare il sistema tramite l'API o tramite un livello sottostante l'interfaccia utente. I costruttori di oggetti di test, come Order e MenuItem, devono usare il sistema anche per creare gli elementi corrispondenti all'interno del sistema.

 Molte delle funzioni di accesso e di aggiornamento saranno già disponibili tramite la normale API dell'applicazione. È possibile però che sia necessario scriverne alcune aggiuntive per abilitare i test. Queste funzioni di accesso e di aggiornamento aggiuntive sono talvolta note come "strumentazione del test". Poiché dipendono dalla progettazione interna del sistema, è responsabilità degli sviluppatori del sistema fornirle, mentre i tester scrivono il codice dei test in relazione al modello di requisiti.

 Quando si scrivono i test automatizzati, è possibile usare test generici per eseguire il wrapping delle funzioni di accesso e di aggiornamento.

### <a name="tests-for-business-rules"></a>Test per le regole di business
 Alcuni requisiti non sono direttamente correlati a un caso di utilizzo. Ad esempio, l'azienda DinnerNow consente ai clienti di scegliere da molti Menu, ma richiede che in ogni Ordine tutti gli Elementi scelti appartengano a un solo Menu. È possibile esprimere questa regola di business come invariante per le associazioni tra Ordini, Menu ed Elementi del modello di classe requisiti.

 Una regola invariante di questo tipo gestisce non solo tutti i casi di utilizzo definiti al momento, ma anche tutti quelli che saranno definiti successivamente. È quindi utile scriverla separatamente dai casi di utilizzo e testarla separatamente dagli stessi.

## <a name="deriving-subsystem-tests-from-models"></a>Derivazione dei test di sottosistema dai modelli
 Nella progettazione di alto livello di un sistema di grandi dimensioni è possibile identificare componenti o sottosistemi. Rappresentano le parti che possono essere progettate separatamente, che risiedono in computer diversi o che sono moduli riutilizzabili da ricombinare in vari modi.

 A ciascun componente principale è possibile applicare gli stessi principi usati per il sistema completo. In un progetto di grandi dimensioni, ogni componente può avere il proprio modello di requisiti. Nei progetti più piccoli è possibile creare un modello architetturale o una progettazione di alto livello per mostrare i componenti principali e le relative interazioni. Per ulteriori informazioni, vedere [modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md).

 In entrambi i casi è possibile stabilire una relazione tra gli elementi del modello e i test di sottosistema, in modo analogo all'operazione eseguita per stabilire una relazione tra il modello di requisiti e i test di sistema.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isolare i componenti con interfacce fornite e richieste
 È utile identificare tutte le dipendenze che un componente ha con altre parti del sistema o con servizi esterni e rappresentarle come interfacce richieste. Questo esercizio comporta in genere una riprogettazione che lascia il componente molto più disaccoppiato e facilmente separabile dal resto della progettazione.

 Un vantaggio costituito da questa separazione è la possibilità di eseguire il test del componente sostituendo i servizi usati generalmente con oggetti fittizi. Si tratta di componenti configurati a scopo di test. Un componente fittizio fornisce l'interfaccia richiesta dal componente, rispondendo alle query con dati simulati. I componenti fittizi fanno parte di un test harness completo che è possibile connettere a tutte le interfacce del componente.

 Un vantaggio del test fittizio è rappresentato dalla possibilità di sviluppare un componente mentre gli altri componenti di cui saranno usati i servizi sono ancora in fase di sviluppo.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Gestire le relazioni tra test e modello
 In un progetto tipico che esegue un'iterazione a intervalli di poche settimane viene effettuata una verifica dei requisiti quasi all'inizio di ogni iterazione. Nella riunione vengono illustrate le funzionalità che devono essere distribuite nell'iterazione successiva. È possibile usare un modello di requisiti per illustrare i concetti, gli scenari e le sequenze di azioni da sviluppare. Le parti interessate dell'azienda impostano le priorità, gli sviluppatori preparano le stime e i tester garantiscono che il comportamento previsto di ogni funzionalità sia acquisito correttamente.

 La scrittura di test è il modo più efficace per definire un requisito ed è anche un modo efficace per assicurare che una persona abbia una chiara comprensione delle esigenze. Tuttavia, mentre la scrittura di test richiede troppo tempo per essere eseguita durante un workshop, la creazione di modelli può essere effettuata molto più rapidamente.

 Da un punto di vista del test, un modello di requisiti può essere considerato un metodo abbreviato per i test. È quindi importante gestire la relazione tra i test e il modello in tutto il progetto.

##  <a name="Attaching"></a> Collegare Test case a elementi di modello
 Se il progetto usa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], è possibile collegare i test agli elementi del modello. In questo modo è possibile trovare rapidamente i test interessati da una modifica ai requisiti e tenere traccia dell'ambito di applicazione di un requisito.

 È possibile collegare i test a tutti i tipi di elemento. Ecco alcuni esempi:

-   Collegare un caso di utilizzo ai test che ne eseguono la verifica.

-   Scrivere le clausole di una postcondizione del caso di utilizzo, o obiettivo, nei commenti collegati al caso di utilizzo, quindi collegare i test a ogni commento.

-   Scrivere regole invarianti in commenti nei diagrammi classi o nei diagrammi di attività e collegarli ai test.

-   Collegare i test a un diagramma di attività o a singole attività.

-   Collegare un gruppo di test al componente o al sottosistema sottoposto a test.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Per collegare i test a una relazione o a un elemento del modello

1.  In [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] creare un requisito e usarlo come base per un gruppo di test.

     Il requisito creato è un elemento di lavoro in [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Può essere un elemento di lavoro Storia utente, Requisito o Caso di utilizzo, a seconda del modello di processo usato dal progetto con [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Per ulteriori informazioni, vedere [tenere traccia del lavoro tramite Visual Studio Team Services o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2.  Collegare l'elemento di lavoro requisito a uno o più elementi del modello.

     In un diagramma di modellazione, fare doppio clic su un elemento, commento o una relazione e quindi fare clic su **Collega a elemento di lavoro**.

3.  Aggiungere al gruppo di test i test case che verificano il requisito espresso nell'elemento del modello.

## <a name="see-also"></a>Vedere anche

- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)
- [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)
