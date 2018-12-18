---
title: "Responsabilità di amministratore | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn about responsibilities of subscriptions administrators.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 92dcfe8b975596fc2f137630f6acfead6b935508
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="administrator-overview"></a>Panoramica dell'amministratore
## <a name="roles--responsibilities"></a>Ruoli e responsabilità
In cambio di un prezzo scontato per i prodotti e i servizi Microsoft, l'organizzazione accetta di farsi carico di alcune responsabilità e limitazioni relativamente alle sottoscrizioni di Visual Studio. Un amministratore di Visual Studio ha quattro responsabilità principali:
1.  **Conoscere i vantaggi e le limitazioni delle sottoscrizioni di Visual Studio.** Una corretta comprensione dei vantaggi può favorire una riduzione dei costi dell'hardware grazie all'uso dei servizi cloud e dei costi del software con le licenze per utente per gli ambienti di preproduzione. 
2.  **Assegnare le sottoscrizioni di Visual Studio a utenti specifici e nominati incoraggiandone l'uso.** Il contratto prevede che le sottoscrizioni di Visual Studio vengano assegnate a utenti specifici e nominati. Mettersi in contatto con gli utenti destinatari dell'assegnazione per assicurarsi che abbiano accesso alla sottoscrizione di Visual Studio e possano usufruire di tutti i vantaggi inclusi.
3.  **Creare un inventario accurato dell'ambiente di preproduzione.** È essenziale assicurarsi che tutti gli utenti che interagiscono con il software concesso in licenza di Visual Studio dispongano di una licenza appropriata tramite la sottoscrizione di Visual Studio. 
4.  **Tenere traccia delle modifiche delle assegnazioni agli utenti e acquisire licenze aggiuntive in base alla pianificazione.** I contratti multilicenza Microsoft offrono flessibilità per l'uso e l'assegnazione delle sottoscrizioni di Visual Studio. In cambio, è necessario tenere traccia delle modifiche per l'utilizzo del software e le assegnazioni degli utenti, nonché elaborare gli ordini di licenze aggiuntive in base alla pianificazione stabilita nel contratto.

## <a name="benefits-and-limitations"></a>Vantaggi e limitazioni
Le sottoscrizioni di Visual Studio consentono ai membri di team di sviluppo di installare e usare il software per la progettazione, lo sviluppo, il testing, la valutazione e la dimostrazione di altro software. Il software incluso nelle sottoscrizioni di Visual Studio non è concesso in licenza per gli ambienti di produzione. 

|                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Licenze basate su utenti                     | MSDN Platforms e tutti i livelli delle sottoscrizioni di Visual Studio sono concessi in licenza in base ai singoli utenti. Ogni membro del team di sviluppo che interagirà con il software incluso con questi prodotti e servizi (installazione, configurazione o accesso) dovrà disporre di una sottoscrizione di Visual Studio propria.                                                                                                                                                                                                                                                                                                                                  |
| Installazioni illimitate                  | Ogni utente con licenza può installare e usare il software su qualsiasi numero di dispositivi per la progettazione, lo sviluppo, il testing, la valutazione e la dimostrazione di altro software. L'unica eccezione è Microsoft Office, concesso in licenza per un solo desktop. Il software di Visual Studio concesso in licenza può essere installato e usato in ufficio, a casa, in ambiente scolastico e nei dispositivi presso l'ufficio di un cliente o su hardware dedicato ospitato da terze parti.                                                                                                                                                                                                                                  |
| Non è destinato agli ambienti di produzione | Il software incluso nelle sottoscrizioni di Visual Studio non è concesso in licenza per gli ambienti di produzione, inclusi gli ambienti a cui hanno accesso gli utenti finali per scopi diversi dai test di accettazione o dalla valutazione per commenti e suggerimenti, un ambiente che si connette a un database di produzione, ambienti per il supporto del ripristino di emergenza o come backup di produzione oppure ambienti usati per la produzione durante i periodi di picco delle attività. Fanno eccezione vantaggi specifici per determinati livelli di sottoscrizione, descritti nel [white paper sulle licenze per Visual Studio](http://aka.ms/vslicensing).                                                                                            |
| Riassegnazione di una licenza                     | Quando un utente lascia un team e non ha più bisogno di una licenza, è possibile riassegnarla dopo 90 giorni. Quando si riassegna una licenza, gli eventuali codici Product Key già usati non verranno sostituiti. Si tratta di una funzionalità diversa rispetto a quella offerta da Volume Licensing Service Center (VLSC). Gli eventuali vantaggi usati dall'utente originale, ad esempio corsi Pluralsight, verranno reimpostati.                                                                                                                                                                                                                                                 |
| Eccezione per gli utenti finali                  | Alla fine di un progetto di sviluppo software, gli utenti finali in genere esaminano un'applicazione e determinano se soddisfa i criteri necessari per il rilascio. Questo processo è denominato test di accettazione utente. I membri di un team, ad esempio uno sponsor aziendale o un responsabile del prodotto possono fungere da intermediari per gli utenti finali. Gli utenti finali che non hanno una sottoscrizione di Visual Studio possono accedere al software per i test di accettazione utente, se l'uso del software è comunque conforme a tutte le condizioni di licenza di Visual Studio. È raro che un utente che si occupa principalmente di progettazione, sviluppo o testing del software sia anche qualificato come "utente finale". |

## <a name="inventory-of-pre-production-environment"></a>Inventario dell'ambiente di preproduzione
Le sottoscrizioni di Visual Studio semplificano la gestione degli asset basandosi sul conteggio degli utenti piuttosto che dei dispositivi.

Gli amministratori di Visual Studio devono assegnare le sottoscrizioni di Visual Studio a **utenti specifici e nominati**. **Non sono consentite** convenzioni di denominazione come Dev1, Dev2 o Dev3.

Ecco alcuni modi per semplificare la creazione dell'inventario dell'ambiente di preproduzione:
- Verificare le assegnazioni degli utenti. Microsoft offre un sito Web denominato [portale di amministrazione di Visual Studio](https://manage.visualstudio.com/) per tenere traccia delle assegnazioni delle sottoscrizioni di Visual Studio.
- Usare il servizio Active Directory locale o basato sul cloud per elencare gli utenti. Se si usa Active Directory per gestire l'accesso degli utenti, si potrebbe riuscire a identificare gli utenti che si occupano di sviluppo e test in base all'appartenenza alla directory.
- Usare strumenti automatizzati per gestire gli inventari dei sistemi. Potrebbe anche essere necessario usare uno strumento di inventario software per facilitare la gestione degli asset software e distinguere gli ambienti di preproduzione da quelli di produzione. Molti clienti che usano Microsoft System Center creano convenzioni di denominazione per automatizzare questa parte del processo di inventario.
- Richiedere aiuto per la riconciliazione manuale. Coinvolgere il personale per semplificare le associazioni tra gli utenti di sviluppo e test e l'ambiente di sviluppo e test. 

## <a name="large-teams-and-external-contractors"></a>Team di grandi dimensioni e collaboratori esterni
Gli amministratori delle sottoscrizioni di Visual Studio sono responsabili di assicurarsi che ogni utente che interagisce con software di Visual Studio concesso in licenza disponga della licenza appropriata con la propria sottoscrizione di Visual Studio.
### <a name="internal-teams"></a>Team interni
In genere, le organizzazioni moderne che si occupano di sviluppo software includono stakeholder da più gruppi. Identificare i contatti per ogni gruppo che possono collaborare al monitoraggio dell'inventario degli utenti e delle relative modifiche. Ogni organizzazione è diversa, ma un elenco dei team di sviluppo tipico potrebbe includere:
- Team di progettazione del software. 
- Team aziendali, inclusi i proprietari del prodotto e gli analisti economici.
- Team di gestione dei progetti. 
- Team del controllo qualità, tra cui personale addetto al controllo di qualità QA e tester manuali.
- Team operativo IT, inclusi i responsabili dell'ambiente di preproduzione e dell'infrastruttura dei lab.

### <a name="external-contractors-and-partners"></a>Partner e collaboratori esterni
I collaboratori esterni possono disporre di licenze per interagire con l'ambiente di Visual Studio concesso in licenza. I Microsoft Certified Partner potrebbero ricevere alcune sottoscrizioni gratuite di Visual Studio per uso interno. Queste sottoscrizioni, tuttavia, non includono la copertura per attività che generano reddito, come lo sviluppo di software personalizzato per un cliente. Chiedere ai partner di inviare una lettera certificata con informazioni sulle licenze da loro fornite e quelle che occorre ottenere.

## <a name="track-user-assignment-and-process-orders"></a>Tenere traccia delle assegnazioni degli utenti ed elaborare gli ordini
Gli amministratori delle sottoscrizioni di Visual Studio devono tenere traccia dell'utilizzo di Visual Studio ed elaborare gli ordini per ogni aumento nell'utilizzo in base alla pianificazione stabilita nel contratto multilicenza o nel Contratto per i Prodotti e i Servizi Microsoft. Il nuovo portale di amministrazione delle sottoscrizioni di Visual Studio semplifica questa attività grazie a uno strumento di monitoraggio utile che mostra le licenze disponibili e quelle usate.
### <a name="high-water-mark-of-usage"></a>Limite massimo di utilizzo
**L'obbligo da parte della società all'acquisto di sottoscrizioni di Visual Studio diventa effettivo immediatamente quando:**
- Viene assegnata una licenza a un utente.
- Un utente interagisce con il software di Visual Studio.

L'obbligo all'acquisto completo è determinato dal **limite massimo di utilizzo**. Questo limite è il punto massimo di assegnazioni utente giornaliere o del numero di utenti che interagiscono con il software di Visual Studio, a seconda del valore maggiore.
1.  Gli amministratori delle sottoscrizioni di Visual Studio possono aumentare il limite massimo di utilizzo assegnando le sottoscrizioni di Visual Studio a singoli utenti.
2.  Gli amministratori delle sottoscrizioni di Visual Studio possono riassegnare le sottoscrizioni da un sottoscrittore a un altro se sono trascorsi 90 giorni dall'assegnazione originale. Per evitare di raggiungere il limite massimo in modo artificiale, eseguire sempre questa operazione rimuovendo la sottoscrizione esistente per poi aggiungere quella nuova.
3.  Gli amministratori delle sottoscrizioni di Visual Studio possono modificare il livello di sottoscrizione assegnato per un singolo e ciò costituisce la riduzione per un'assegnazione e l'incremento per un'altra. Quando si riduce il livello di sottoscrizione assegnato di un sottoscrittore, il singolo deve interrompere immediatamente l'uso e disinstallare qualsiasi componente incluso solo nel livello di sottoscrizione superiore. 

### <a name="open-license-and-open-value"></a>Open License e Open Value
Le sottoscrizioni possono essere assegnate anche tramite altri programmi multilicenza Microsoft, come Microsoft Open License o Open Value. In questo caso, è necessario elaborare l'ordine per gli altri utenti durante il mese in cui gli utenti (dipendenti o collaboratori esterni) iniziano a interagire con il software di Visual Basic concesso in licenza.
### <a name="enterprise-agreements"></a>Enterprise Agreement
I contratti Microsoft Enterprise Agreement (EA), MPSA e Select Plus offrono flessibilità per l'uso e la concessione in licenza del software di Visual Studio nel tempo. Gli amministratori di Visual Studio devono effettuare un ordine true-up annuale per portare le licenze software fino al limite massimo di utilizzo stabilito durante il periodo del contratto.