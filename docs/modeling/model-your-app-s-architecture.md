---
title: Modellare l'applicazione&#39;architettura s
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f7da241dc6090339bd5d9d9e6f731041a27fe84
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="model-your-app39s-architecture"></a>Modellare l'applicazione&#39;architettura s
Per garantire che il sistema software o l'applicazione soddisfa degli utenti è necessario, è possibile creare modelli in Visual Studio come parte della descrizione della struttura complessiva e il comportamento di sistema software o dell'applicazione. Usando gli schemi è anche possibile descrivere modelli usati durante la progettazione. Questi modelli consentono di comprendere l'architettura esistente, discutere le modifiche e comunicare chiaramente le intenzioni.

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Lo scopo di un modello è ridurre l'ambiguità che si verifica nelle descrizioni in linguaggio naturale e consentono all'utente e ai colleghi di visualizzare la progettazione e discutere le progettazioni alternative. Un modello deve essere usato insieme ad altri documenti o discussioni. Un modello di per sé non rappresenta una specifica completa dell'architettura.

> [!NOTE]
>  In questo argomento, il termine "sistema" indica il software che si sta sviluppando. Potrebbe essere un'ampia raccolta di molti componenti hardware e software oppure una singola applicazione o una parte di un'applicazione.

 L'architettura di un sistema può essere suddivisa in due aree:

-   [Progettazione di alto livello](#Structure). Descrive i componenti principali e la loro modalità di interazione per soddisfare ogni requisito. Se il sistema è di grandi dimensioni, ogni componente può disporre del proprio progetto di alto livello che mostra come è costituito da componenti più piccoli.

-   [Schemi progettuali](#Patterns) e le convenzioni utilizzate in tutte le progettazioni dei componenti. Un modello descrive un particolare approccio per realizzare un obiettivo di programmazione. Usando gli stessi schemi in tutta una progettazione, il team può ridurre il costo delle modifiche e dello sviluppo di nuovo software.

##  <a name="Structure"></a> Progettazione di alto livello
 Un progetto di alto livello descrive i componenti principali del sistema e il modo in cui interagiscono tra loro per raggiungere gli obiettivi della progettazione. Le attività nell'elenco seguente sono coinvolte nello sviluppo della progettazione di alto livello, anche se non necessariamente in una determinata sequenza.

 Se si sta aggiornando il codice esistente, è possibile iniziare descrivendo i componenti principali. Verificare di comprendere le modifiche ai requisiti dell'utente e quindi aggiungere o modificare le interazioni tra i componenti. Se si sta sviluppando un nuovo sistema, iniziare individuando le funzionalità principali di esigenze degli utenti. È possibile esplorare le sequenze di interazioni per i casi di utilizzo principali e quindi consolidare le sequenze in una progettazione del componente.

 In ogni caso, è utile per sviluppare le diverse attività in parallelo e sviluppare il codice e i test in una fase iniziale. Evitare di tentare di completare uno di questi aspetti prima di avviarne un altro. In genere, i requisiti e la comprensione del modo migliore per progettare il sistema verrà modificato durante la scrittura e il test del codice. Di conseguenza, è necessario iniziare a individuare e codificare le funzionalità principali dei requisiti e della progettazione. Inserire i dettagli nelle iterazioni successive del progetto.

-   [Informazioni sui requisiti](#Requirements). Il punto di partenza di qualsiasi progettazione è una chiara comprensione delle esigenze degli utenti.

-   [I modelli di architettura](#BigDecisions). Le scelte effettuate sulle tecnologie principali e gli elementi architettonici del sistema.

-   Modello di dati dei componenti e le interfacce. È possibile creare diagrammi classi per descrivere le informazioni passate tra componenti e archiviate all'interno dei componenti.

##  <a name="Requirements"></a> Informazioni sui requisiti
 La progettazione di alto livello di un'applicazione completa viene sviluppata più efficacemente con un modello requisiti o altra descrizione delle esigenze degli utenti. Per ulteriori informazioni sui modelli di requisiti, vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).

 Se il sistema che si sta sviluppando è un componente in un sistema più grande, parte o tutti i requisiti potrebbero essere incorporati nelle interfacce di programmazione.

 Il modello requisiti fornisce queste informazioni essenziali:

-   Interfacce fornite. Un'interfaccia fornita fornisce un elenco dei servizi o operazioni che il sistema o il componente deve fornire ai propri utenti, che siano utenti o altri componenti software.

-   Interfacce necessarie. Un'interfaccia richiesta fornisce un elenco di servizi o operazioni che possono essere usate dal sistema o dal componente. In alcuni casi, sarà possibile progettare tutti questi servizi come parte del proprio sistema. In altri casi, specialmente se si sta sviluppando un componente che può essere combinato con altri componenti in molte configurazioni, l'interfaccia richiesta verrà impostata da considerazioni esterne.

-   Requisiti di qualità del servizio. Le prestazioni, la sicurezza, l'affidabilità e altri obiettivi e vincoli che il sistema deve soddisfare.

 Il modello requisiti viene scritto dal punto di vista degli utenti del sistema, siano essi persone o altri componenti software. Questi non conoscono i meccanismi interni del sistema. Al contrario, l'obiettivo in un modello architettonico è descrivere i meccanismi interni e mostrare come soddisfano le esigenze degli utenti.

 Se si mantengono i requisiti e modelli architettonici separati, diventa più semplice illustrare i requisiti con gli utenti. In tal modo vengono agevolati anche il refactoring di progettazione e la considerazione di architetture alternative mentre i requisiti restano invariati.

 La quantità di dettagli che devono essere inseriti in un modello di requisiti o architettonico dipende dalla scala del progetto e dalle dimensioni e dalla distribuzione del team. Un piccolo team su un progetto breve non po' andare oltre il disegno di un diagramma classi dei concetti aziendali e alcuni schemi progettuali; un progetto di grandi dimensioni distribuito su più aree ha bisogno di più dettagli.

##  <a name="BigDecisions"></a> Modelli di architettura
 Nelle prime fasi di sviluppo è necessario scegliere le principali tecnologie e gli elementi da cui dipende la progettazione. Le aree in cui devono essere apportate queste scelte includono quanto segue:

-   Scelte di tecnologia di base, ad esempio la scelta tra un database e un file system e la scelta tra un'applicazione di rete e un client Web e così via.

-   Scelte di framework, ad esempio una scelta tra Windows Workflow Foundation o ADO.NET Entity Framework.

-   Scelte dei metodi di integrazione, ad esempio tra un bus di servizio aziendale o un canale Point to Point.

 Queste scelte vengono frequentemente determinate dai requisiti di qualità del servizio, ad esempio la scala e la flessibilità e possono essere effettuate prima che siano noti i requisiti dettagliati. In un sistema di grandi dimensioni, la configurazione di hardware e software sono fortemente correlati.

 Le selezioni effettuate influiscono sulla modalità di utilizzo e di interpretazione del modello architettonico. Ad esempio, in un sistema che usa un database, le associazioni in un diagramma classi potrebbero rappresentare relazioni o chiavi esterne nel database, mentre in un sistema basato su file XML, le associazioni potrebbero indicare riferimenti incrociati che usano XPath. In un sistema distribuito i messaggi in un diagramma di sequenza possono rappresentare messaggi su una connessione; in un'applicazione indipendente, possono rappresentare chiamate di funzione.

##  <a name="Patterns"></a> Modelli di progettazione
 Uno schema progettuale è una struttura sulla modalità di progettazione di un particolare aspetto del software, specialmente uno che ricorre in parti diverse del sistema. Adottando un approccio uniforme nel progetto, è possibile ridurre il costo di progettazione, garantire la coerenza nell'interfaccia utente e ridurre i costi di comprensione e modifica del codice.

 Alcuni schemi progettuali generali, ad esempio Observer sono ben conosciuti e ampiamente applicabili. Sono anche disponibili modelli che possono essere applicati solo al progetto. Ad esempio, in un sistema di vendite Web, saranno disponibili diverse operazioni nel codice dove vengono apportate modifiche all'ordine del cliente. Per assicurarsi che lo stato dell'ordine venga visualizzato in modo accurato in ogni fase, tutte queste operazioni devono seguire un particolare protocollo per aggiornare il database.

 Parte del lavoro dell'architettura software consiste nel determinare quali schemi devono essere adottati nella progettazione. In genere si tratta di un'attività in corso, poiché i nuovi modelli e miglioramenti a modelli esistenti verranno individuati nel corso del progetto. È utile organizzare il piano di sviluppo in modo da esercitarsi con ognuno degli schemi progettuali principali in una fase iniziale.

 La maggior parte degli schemi progettuali può essere parzialmente incorporata nel codice del framework. Parte del modello può essere ridotto per richiedere agli sviluppatori di usare particolari classi o componenti, ad esempio un livello di accesso ai database che assicura che il database venga gestito correttamente.

 Uno schema progettuale viene descritto in un documento e in genere include le seguenti parti:ne viene descritto in un documento e in genere include le seguenti parti:

-   Nome.

-   Descrizione del contesto in cui è applicabile. In base a quali criteri uno sviluppatore deve pensare di applicare questo modello?

-   Breve spiegazione del problema da risolvere.

-   Modello delle parti principali e relative relazioni. Potrebbe trattarsi di classi o componenti e interfacce, con associazioni e dipendenze tra di loro. Gli elementi in genere rientrano in due categorie:

-   Convenzioni di denominazione.

-   Descrizione di come il modello risolve il problema.

-   Descrizione delle variazioni che gli sviluppatori potrebbero essere in grado di adottare.

## <a name="see-also"></a>Vedere anche

- [Visualizzare il codice](../modeling/visualize-code.md)
- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)
- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)