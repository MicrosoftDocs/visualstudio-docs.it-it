---
title: Acquisto di sottoscrizioni cloud di Visual Studio per i CSP
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: Information for Cloud Solution Providers on how to buy and manage Visual Studio cloud subscriptions for your customers.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e6bbaa7e84da44b53bc7cea0d0b0746e4680caf2
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Acquistare e gestire sottoscrizioni cloud di Visual Studio per i clienti

I partner inclusi nel programma [Cloud Solution Provider (CSP)](https://partner.microsoft.com/en-US/cloud-solution-provider) possono acquistare sottoscrizioni cloud di Visual Studio Enterprise e Visual Studio Professional per i loro clienti. 

[Confrontare le opzioni di sottoscrizione cloud](https://www.visualstudio.com/vs/pricing)

## <a name="prerequisites"></a>Prerequisiti
È prima di tutto necessario configurare il tenant del cliente nel Centro per i partner e creare una sottoscrizione di Azure per questo tenant. 
[Altre informazioni](https://docs.microsoft.com/vsts/billing/csp/set-up-csp-customer)

## <a name="how-to-buy"></a>Modalità di acquisto

<iframe src="//channel9.msdn.com/Shows/Visual-Studio-for-CSP-Partners/CSP-How-to-buy-Visual-Studio-Subscriptions/player" width="600" height="315" allowFullScreen="true" frameBorder="0"></iframe>

0. Accedere al [Centro per i partner Microsoft](https://partnercenter.microsoft.com).
0. Scegliere **Clienti** e selezionare un cliente per cui effettuare l'acquisto.
0. Scegliere **Gestione dei servizi**.
0. Scegliere **Visual Studio Marketplace**.
0. Assicurarsi che sia visualizzato il nome del cliente nell'angolo in alto a destra.
0. Scegliere **Sottoscrizioni**.
0. Scegliere Enterprise o Professional e scegliere mensile o annuale per Visual Studio.
0. Scegliere **Acquista**.
0. Scegliere la sottoscrizione di Azure per la fatturazione dell'acquisto.
0. Immettere il numero di utenti necessari per il cliente.
0. Rivedi l'ordine e **Conferma** esso.

>[!NOTE]
> È necessario seguire questa procedura ogni volta che si acquistano sottoscrizioni di Visual Studio come CSP. Al momento non è disponibile alcuna API per automatizzare l'acquisto.

Dopo aver confermato l'acquisto, è possibile scegliere **Gestisci** per assegnare le sottoscrizioni agli utenti finali del cliente.  È anche possibile accedere al portale di amministrazione delle sottoscrizioni dal Centro per i partner scegliendo **Gestione dei servizi**.  Da qui, vedere i passaggi o il video seguenti.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Come gestire le sottoscrizioni cloud di Visual Studio per il cliente

<iframe src="//channel9.msdn.com/Shows/Visual-Studio-for-CSP-Partners/CSP-How-to-manage-Visual-Studio-Subscriptions/player" width="600" height="315" allowFullScreen="true" frameBorder="0"></iframe>

0. Accedere al [Centro per i partner Microsoft](https://partnercenter.microsoft.com).
0. Scegliere **Clienti** e il nome del cliente.
0. Scegliere **Gestione dei servizi**.
0. Scegliere **Gestisci sottoscrizioni di Visual Studio**.

Se è disponibile più di una sottoscrizione di Azure per il cliente, usare il menu a discesa per scegliere la sottoscrizione di Azure tramite la quale sono stati effettuati gli acquisti.  In **Riepilogo licenze** viene visualizzato il numero di sottoscrizioni assegnate e disponibili per ogni opzione di sottoscrizione cloud di Visual Studio.  Il riepilogo consente anche di acquistare sottoscrizioni aggiuntive o ridurre il numero di sottoscrizioni.

Scegliere **Aggiungi** per assegnare una sottoscrizione a un nuovo utente.  Il conteggio visualizzato viene aggiornato e l'utente finale riceve una notifica tramite posta elettronica. L'utente finale può quindi accedere con l'indirizzo di posta elettronica fornito per attivare la sottoscrizione di Visual Studio nel [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Per riassegnare una sottoscrizione di Visual Studio a un altro utente, è possibile eliminare la sottoscrizione corrente e aggiungere un nuovo sottoscrittore. 

Se un sottoscrittore non ha ancora attivato la sottoscrizione di Visual Studio, è possibile che non abbia ricevuto il messaggio di posta elettronica di invito.  È possibile usare il portale di amministrazione di Visual Studio anche per richiedere un nuovo invio dell'invito per l'attivazione all'utente.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Visualizzare i prezzi di Visual Studio per i partner CSP

Per visualizzare i prezzi di Visual Studio per i partner CSP, accedere al [Centro per i partner](https://partnercenter.microsoft.com).  Scegliere **Prezzi e offerte** nella struttura di spostamento a sinistra.  Scegliere il file dei prezzi per il mese in corso in **servizi basati sull'utilizzo di servizi** in alto a destra. Nel foglio di calcolo di Excel scaricato passare al foglio **Azure Price List** (Listino prezzi di Azure) e selezionare **Visual Studio** per filtrare la colonna **Meter Category** (Categoria misuratore).

Di seguito viene illustrato come interpretare le informazioni disponibili in questo foglio di calcolo:
| Categoria misuratore    |   Nome                 |  Unità                                |           Contenuto                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Enterprise             |  Sottoscrizione                         | Sottoscrizione mensile di Visual Studio Enterprise   |
| Visual Studio     | Enterprise (annuale)    |  Sottoscrizioni annuali                 | Sottoscrizione annuale di Visual Studio Enterprise    |
| Visual Studio     | Professionale           |  Sottoscrizione                         | Sottoscrizione mensile di Visual Studio Professional |
| Visual Studio     | Professional (annuale)  |  Sottoscrizioni annuali                 | Sottoscrizione annuale di Visual Studio Professional  |

Offriamo uno sconto del 5% per la sesta unità acquistata (per un determinato cliente) mensilmente di ogni sottoscrizione di Visual Studio. Questo è il motivo per cui sono visualizzate due righe per ogni opzione di sottoscrizione. Una riga mostra un valore minimo pari a 0, da interpretare come prezzo di base per le unità da 1 a 5. L'altra riga mostra un valore minimo pari a 5, ovvero il prezzo scontato del % 5 che si applica dalle 6 unità in poi.


## <a name="faq"></a>Domande frequenti
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>D: come vengono elaborati gli addebiti per le sottoscrizioni cloud **mensili**?
R: al momento del primo acquisto, viene fatturata una quantità ripartita in base ai giorni rimanenti del mese corrente. Ad esempio, se si acquistano 10 sottoscrizioni cloud mensili di Visual Studio Professional il 15 aprile, vengono addebitate 5 unità perché rimangono 15 giorni del mese di 30 giorni, ovvero il 50%, quindi l'addebito delle unità viene ripartito al 50%. Il primo del mese di maggio e per ogni mese successivo fino all'annullamento, verranno fatturate tutte e 10 le unità.

Quando si aumenta la quantità a pagamento in un secondo momento, anche le unità aggiunte verranno ripartite in base ai giorni rimanenti del mese corrente. Pertanto, se si acquista un'altra sottoscrizione cloud mensile di Visual Studio Professional il 10 maggio, verranno fatturate approssimativamente 0,677 unità (21 giorni rimanenti nel mese di maggio di 31 giorni). 

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>D: come vengono elaborati gli addebiti per le sottoscrizioni cloud **annuali**?
R: a ogni acquisto viene fatturata immediatamente l'intera quantità acquistata. Gli addebiti non vengono distribuiti nell'anno e non è prevista alcuna ripartizione proporzionale. Se si acquistano sottoscrizioni cloud annuali in momenti diversi nell'anno, ci saranno sottoscrizioni con rinnovo in mesi diversi. Non viene allineata la data di scadenza di tutte le sottoscrizioni cloud annuali di un cliente come avviene comunemente con i contratti multilicenza Microsoft.

### <a name="q-how-do-cancelations-work"></a>D: come funzionano gli annullamenti?
R: quando si annulla una sottoscrizione cloud di Visual Studio, si annulla il rinnovo automatico. La sottoscrizione continua fino alla relativa data di rinnovo normale e poi semplicemente scade. Alla scadenza, il sottoscrittore di Visual Studio non può più usare Visual Studio o qualsiasi altro vantaggio dalla sottoscrizione.

Con le sottoscrizioni cloud mensili, gli annullamenti diventano effettivi a partire dal primo giorno del mese successivo. Se si annullano solo alcune delle sottoscrizioni cloud mensili del cliente, assicurarsi di rimuovere gli utenti il primo del mese successivo per assicurarsi che rimangano assegnate sottoscrizioni attive alle persone corrette.

Per le sottoscrizioni cloud annuali, gli annullamenti diventano effettivi il primo giorno del mese successivo a 12 mesi dall'acquisto originale o a 12 mesi dall'ultimo addebito per il rinnovo annuale. Ad esempio, se si acquista una sottoscrizione cloud annuale di Visual Studio Enterprise il 3 gennaio 2018, questa rimane attiva fino al 1 febbraio 2019 quando viene rinnovata automaticamente per un altro anno. Se si annulla la sottoscrizione in qualsiasi momento tra tale data e il 1 febbraio 2020, la scadenza sarà il 1 febbraio 2020. Non è previsto alcuno sconto in caso di annullamento di sottoscrizioni cloud annuali prima del termine dell'anno di validità.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>D: quali tipi di sconti per volume sono disponibili per le sottoscrizioni di Visual Studio?

R: viene offerto uno sconto del 5% oltre le 6 sottoscrizioni *per ogni tipo* di sottoscrizione:

* Visual Studio Professional (mensile)
* Visual Studio Professional (annuale)
* Visual Studio Enterprise (mensile)
* Visual Studio Enterprise (annuale)

Ad esempio quindi, se si acquistano 6 sottoscrizioni mensili di Visual Studio Professional e 5 sottoscrizioni mensili di Visual Studio Enterprise, si paga il prezzo normale per le 5 sottoscrizioni Professional, si ottiene uno sconto del 5% per la sesta sottoscrizione Professional e si paga il prezzo normale per tutte le 5 sottoscrizioni Enterprise.

Inoltre, lo sconto è valido solo per gli addebiti in un determinato periodo di fatturazione mensile. Pertanto, se si acquistano 5 sottoscrizioni annuali di Visual Studio Professional in un mese e quindi se ne acquistano altre 5 nel mese successivo, verrà applicato il prezzo normale per tutte le 10 sottoscrizioni.

Questi sconti sono indicati nei dati sui prezzi all'interno del [Centro per i partner](https://partnercenter.microsoft.com). 

### <a name="q-are-there-renewal-discounts"></a>D: sono previsti sconti per il rinnovo?

R: no, i prezzi per le sottoscrizioni di Visual Studio sono fissi. Lo stesso prezzo viene applicato per le nuove sottoscrizioni e per i rinnovi.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>D: esistono opzioni per i prezzi di Azure per sviluppo/test per i CSP?

R: non attualmente. I clienti possono sfruttare i [Prezzi di Azure per sviluppo/test](http://aka.ms/azuredevtestpricing), ma non è disponibile alcuna offerta specifica per i CSP.