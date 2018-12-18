---
title: Informazioni sulle lingue specifiche del dominio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9357c55b204d521eb5cd77af328636485c490ff4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="about-domain-specific-languages"></a>Informazioni sui linguaggi specifici del dominio

A differenza di un linguaggio di uso generale, ad esempio c# o UML, un linguaggio specifico di dominio (DSL) è progettato per le istruzioni in un dominio particolare area problematica, o express.  
  
DSL Well-Known includere espressioni regolari e SQL. Ogni linguaggio DSL è decisamente migliore rispetto a un linguaggio di uso generale per la descrizione di operazioni sulle stringhe di testo o un database, ma peggio per descrivere i concetti che si trovano all'esterno di un proprio ambito. Settori singoli inoltre disporre di proprie DSL. Ad esempio, nel settore telecomunicazioni, chiamare descrizione lingue vengono ampiamente utilizzate per specificare la sequenza degli stati in una chiamata telefonica e in modalità wireless viaggio settore standard che DSL viene utilizzato per descrivere le prenotazioni di volo.  
  
L'azienda e del progetto anche gestire speciale set di concetti che può essere descritto con un linguaggio DSL. Ad esempio, è possibile definire un linguaggio DSL per una di queste applicazioni:  
  
-   Piano di percorsi di navigazione in un sito Web.  
  
-   Cablaggio per componenti elettronici.  
  
-   Reti di nastri trasportatori e dispositivi per un aeroporto di gestione dei bagagli.  
  
Quando si progetta un linguaggio DSL, è necessario definire un *classe dominio* per ognuna delle principali nozioni nel dominio, ad esempio un banco check-in aeroporto, luce o pagina Web. Definire *relazioni di dominio* come collegamento ipertestuale, rete o un nastro trasportatore per collegare i concetti.  
  
Creano gli utenti di tale linguaggio DSL *modelli.* I modelli sono *istanze* della DSL. Ad esempio, descrivono un particolare sito Web o il collegamento di un determinato dispositivo o il sistema in un determinato aeroporto di gestione dei bagagli.  
  
Gli utenti possono visualizzare un modello come un diagramma o un Windows form. I modelli possono essere visualizzati anche in formato XML, che è una modalità di archiviazione. Quando si definisce un linguaggio DSL, si definiscono come le istanze di ogni classe di dominio e la relazione vengono visualizzati sullo schermo dell'utente. Un tipico DSL viene visualizzato come una raccolta di icone o rettangoli connessi dalle frecce.  
  
Nella figura seguente viene illustrato un modello piccolo in un linguaggio DSL di motivi:  
  
![Modello di albero genealogico Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Operazioni eseguibili con DSL  

Un'applicazione tipica di un linguaggio DSL consiste nel generare codice programma o altri elementi. Quando si definisce il modello DSL, è possibile definire *modelli di testo* che leggere un modello di DSL e generare i file di testo.  
  
Ad esempio, è possibile scrivere modelli che accettano un piano di aeroporto e generano parte del software per, nonché tra i documenti che descrivono il piano di gestione dei bagagli.  
  
Dopo aver definito un linguaggio DSL, è possibile distribuirlo ad altri utenti che possono installare nel proprio computer. Gli utenti di tale linguaggio DSL possono creare e modificare i modelli di Visual Studio.  
  
È inoltre possibile definire i comandi di menu e altri strumenti che consentono agli utenti di modificare del linguaggio DSL, vincoli di convalida per assicurare che il linguaggio DSL è utilizzato correttamente e i modelli di elementi che consentono agli utenti di creare nuove istanze. È possibile eseguire il wrapping di uno o più DSL con gli strumenti e altre estensioni di Visual Studio come un pacchetto integrato.  
  
In genere, un linguaggio specifico di dominio viene creato quando un team di sviluppo è necessario scrivere codice simile per diversi prodotti. Ad esempio, una società che è progettato per i sistemi di gestione dei bagagli potrebbe definire un linguaggio DSL traccia bagagli da cui è possibile generare parte del codice per ogni installazione. I vantaggi di DSL sono possibile riconosciute dai clienti, che il codice generato da quest'ultimo è affidabile, e che il sistema può essere aggiornato rapidamente se cambiano i requisiti dei clienti.  
  
[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Consente di creare un linguaggio specifico di dominio che dispone della finestra di progettazione grafica e la propria notazione diagramma e quindi utilizzare il linguaggio per generare codice sorgente appropriato per ogni progetto.  
  
## <a name="domain-specific-development"></a>Sviluppo di DSL

Lo sviluppo di specifico di dominio è il processo di identificazione le parti delle applicazioni che possono essere modellate utilizzando un linguaggio specifico di dominio e quindi creando la lingua e la distribuzione per gli sviluppatori di applicazioni. Gli sviluppatori di utilizzano il linguaggio specifico di dominio per creare i modelli che sono specifici per le applicazioni, utilizzare i modelli per generare codice sorgente e quindi utilizzare il codice sorgente per sviluppare le applicazioni.  

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspetti dello sviluppo specifico di dominio con interfaccia grafico

Un linguaggio specifico di dominio con interfaccia grafico deve includere le funzionalità seguenti:  
  
- Notation  
  
- Modello di dominio  
  
- Generazione di elementi  
  
- Serializzazione  
  
- Integrazione con Visual Studio  
  
### <a name="notation"></a>Notation

Un linguaggio specifico di dominio deve avere un set relativamente ridotto di elementi che possono essere facilmente definite ed estesi per rappresentare costrutti specifici di dominio. Una notazione è costituito da forme che rappresentano gli elementi, e connettori, che rappresentano le relazioni tra elementi, su una superficie del diagramma grafico. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], le forme possono essere estesi e migliorate per rappresentare gli elementi del linguaggio di specifico di dominio.  
  
### <a name="domain-model"></a>Modello di dominio

Un linguaggio specifico di dominio è necessario combinare i set di elementi e le relazioni tra loro in una grammatica coerente. Inoltre necessario definire se combinazioni di elementi e relazioni sono valide. Ad esempio, i linguaggi di programmazione in genere impediscono ereditarietà circolare, in cui una classe è derivata da una seconda classe e la seconda classe è derivata dalla classe prima. Vincoli possono essere utilizzati anche per esprimere la logica di business, ad esempio, un utente non può essere un dipendente di se stesso. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]utilizza i vincoli per esprimere i tipi di restrizioni che richiedono più linguaggi specifici di dominio.  
  
### <a name="artifact-generation"></a>Generazione di elementi

Uno degli scopi principali di un linguaggio specifico di dominio consiste nel generare un elemento, ad esempio, il codice sorgente, file XML o alcuni altri dati utilizzabili. In genere, una modifica nel modello indica una modifica dell'elemento. È possibile utilizzare [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] per generare gli elementi e rigenerarli quando si modifica il modello.  
  
### <a name="serialization"></a>Serializzazione

Un linguaggio specifico di dominio deve essere resa persistente in una forma che può essere modificata, salvata, chiusi e ricaricata. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]utilizza un formato XML che consente di definire e personalizzare la modalità del linguaggio specifico di dominio viene serializzato o persistente.  
  
### <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio

Poiché [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] è ospitato in Visual Studio estende molte finestre di Visual Studio e i controlli. È anche possibile personalizzare il comportamento dei comandi di menu, elementi della casella degli strumenti e altri elementi dell'interfaccia utente.  
  
È anche possibile creare una scheda Bus modello per il linguaggio specifico di dominio. Questa scheda consente di un modello di riferimento e gli elementi all'interno di un modello e consente di scrivere codice che possono accedere e aggiornare un'istanza del linguaggio DSL. Utilizzando un meccanismo avanzato Bus di modelli, è possibile scrivere le estensioni di Visual Studio che funzionano con più modelli. È anche possibile scrivere applicazioni autonome che funzionano con i modelli. Per ulteriori informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Vantaggi di sviluppo specifico di dominio

Un linguaggio specifico di dominio può offrire i vantaggi seguenti:  
  
- Contiene costrutti che rientrano esattamente lo spazio dei problemi.  
  
     A differenza dei linguaggi di uso generale, un linguaggio specifico di dominio è costituito da elementi e relazioni che rappresentano direttamente la logica dello spazio dei problemi. Ad esempio, un'applicazione di polizza deve includere elementi per i criteri e le attestazioni. Un linguaggio specifico di dominio, è facile progettare l'applicazione e individuare e correggere gli errori di logica.  
  
- Consente di non sviluppatori e gli utenti che non conoscono il dominio comprendere la struttura complessiva.  
  
     Tramite un linguaggio specifico di dominio con interfaccia grafico, è possibile creare una rappresentazione visiva del dominio in modo che non sviluppatori di comprendere facilmente la progettazione dell'applicazione.  
  
- Rende più semplice creare un prototipo dell'applicazione finale.  
  
     Gli sviluppatori possono utilizzare il codice che genera il modello per creare un'applicazione di prototipo che consente di visualizzare ai client.  
  
## <a name="the-process-of-domain-specific-development"></a>Il processo di sviluppo specifico di dominio

La maggior parte dei team di sviluppo di software che utilizzano linguaggi specifici di dominio di eseguire la procedura per creare e usare i propri modelli:  
  
-   Il team di distingue le parti variabili del dominio dalle parti che non cambiano mai.  
  
-   Gli sviluppatori di scrivere codice per le parti fisse e lasciare i punti di estensione per le parti variabili.  
  
-   Il responsabile dello sviluppo di software o il progettista crea un linguaggio specifico di dominio che include i modelli di progettazione delle parti del dominio e i punti di estensione per le parti variabili fisse.  
  
-   Il responsabile dello sviluppo di software o il progettista distribuisce il linguaggio specifico di dominio per gli sviluppatori di varie applicazioni che produce il team.  
  
-   Ogni sviluppatore crea un modello che si applica all'applicazione specifica.