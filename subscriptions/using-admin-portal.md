---
title: Uso del portale per gli amministratori | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
mescription: Learn how to manage your organization's Visual Studio subscriptions with the Administrator Portal.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 22351b94923777d5eb1fe40cd2e43e9dc20f2449
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Uso del portale di amministrazione delle sottoscrizioni di Visual Studio

Tenere a mente quanto segue durante l'uso del Portale di amministrazione delle sottoscrizioni di Visual Studio:
 
- **Le sottoscrizioni di Visual Studio sono concesse in licenza ai singoli utenti.** Ogni abbonato può usare il software su un numero indefinito di computer in base alle esigenze di sviluppo e test. 
- **Assegnare solo un livello di sottoscrizione per ogni sottoscrittore,** in base alla sottoscrizione di Visual Studio acquistata dall'organizzazione. Qualora esistano abbonati a cui sono stati assegnati più livelli di abbonamento, modificare le impostazioni in modo che ne abbiano solo uno. 
- **Sarà necessario aggiornare il livello di abbonamento di un individuo** nel momento in cui l'abbonamento viene aggiornato (successivamente all'acquisto di una licenza "step-up") o rinnovato a un livello inferiore. 
- **Non condividere gli abbonamenti tra più abbonati.** Assegnare una sottoscrizione per chiunque usi uno o tutti i vantaggi dell'abbonamento (software per sviluppo e test, Microsoft Azure, e-learning e così via). 

## <a name="adminstrator-roles"></a>Ruoli degli amministratori

Esistono due diversi ruoli nel nuovo Portale di amministrazione delle sottoscrizioni di Visual Studio per i clienti con contratti multilicenza. Questi ruoli sono, ad esempio, il ruolo di contatto principale/per le comunicazioni e il ruolo di gestione di sottoscrizioni in VLSC. 

**Amministratori con privilegi elevati:** durante la prima configurazione di un'organizzazione, il contatto principale o per le comunicazioni diventa amministratore con privilegi elevati per impostazione predefinita. Il contatto principale o per le comunicazioni può scegliere di assegnare altri amministratori con privilegi elevati o amministratori. Un amministratore con privilegi elevati può aggiungere e rimuovere altri amministratori e sottoscrittori. Se nel sistema sono presenti più di due amministratori con privilegi elevati, è possibile eliminarli tutti tranne gli ultimi due per motivi di sicurezza. 

**Amministratori:** un amministratore può essere configurato solo da un amministratore con privilegi elevati. Gli amministratori possono gestire i sottoscrittori negli accordi che l'amministratore con privilegi elevati assegna loro. 

## <a name="getting-started"></a>Per iniziare

Per usare il portale per gli amministratori per gestire le sottoscrizioni dell'organizzazione, è necessario caricare l'organizzazione nel portale.  Dopo aver completato il caricamento, acquisire familiarità con le pagine dei sottoscrittori e dei dettagli, che contengono gli strumenti e le informazioni necessarie per eseguire le attività di gestione delle sottoscrizioni.  

### <a name="onboarding"></a>Onboarding

Quando l'organizzazione è pronta per il processo di onboarding nel portale di amministrazione di Visual Studio, i contatti principali e per le comunicazioni riceveranno una e -mail con una richiesta per il completamento del processo. I dettagli riportati di seguito rappresentano i passaggi necessari per l'onboarding nel nuovo portale. Per una procedura dettagliata del processo, vedere il [video per l'oboarding degli amministratori](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) oppure [l'articolo del supporto tecnico relativo al ](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Processo di migrazione per gli amministratori delle sottoscrizioni di Visual Studio").   
1.  **Individuazione del PCN e accesso:**
    - I contatti principali e per le comunicazioni ricevono un messaggio di posta elettronica un collegamento e le ultime tre cifre del numero PCN. * 
    - Per ottenere il PCN completo, il contatto principale deve accedere a VLSC (le istruzioni per l'individuazione del PCN sono reperibili qui). 
    - Dopo aver ottenuto il PCN, sarà necessario selezionare il collegamento univoco richiesto per accedere. Potranno accedere usando un account di lavoro o dell'istituto di istruzione (se l'organizzazione si trova in Azure AAD) o con un Account Microsoft (MSA) se l'organizzazione non è presente in AAD. 
    - Successivamente, sarà necessario immettere il PCN. 
2.  **Impostare gli amministratori.** Dopo aver immesso il PCN, saranno registrati come amministratori con privilegi elevati nel nuovo sistema e saranno in grado di aggiungere altri amministratori con privilegi elevati e amministratori (precedentemente noti come gestori degli abbonamenti). Per evitare di perdere l'accesso,il processo deve essere completato prima della data di migrazione dell'organizzazione. 
3.  **Accesso al nuovo portale per la gestione delle sottoscrizioni.**  Una volta eseguita la migrazione dell'organizzazione, i nuovi amministratori e amministratoti con privilegi elevati registrati, riceveranno dei messaggi di posta elettronica per effettuare l'accesso al nuovo portale e iniziare a gestire le sottoscrizioni.  

> [!NOTE]
> Se il contatto principale o per le comunicazioni riceve più di un messaggio di posta elettronica, significa che ha più PCN. È necessario completare il processo usando il collegamento univoco per il PCN a cui si fa riferimento in ogni messaggio di posta elettronica.*

Se è necessario essere aggiunti al nuovo Portale di amministrazione delle sottoscrizioni di Visual Studio e non si è certi di chi sia il contatto principale/per le comunicazioni di riferimento, è possibile trovare queste informazioni dopo l'accesso a [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Vedere l'argomento [Trova il contatto principale](/find-primary-contact/) per la procedura per individuare il contatto principale o per le comunicazioni nel Volume Licensing Service Center.
Se si è già stati configurati come amministratore, è possibile passare direttamente al [portale di amministrazione delle sottoscrizioni di Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Informazioni sulla pagina dei sottoscrittori
Dopo aver assegnato le sottoscrizioni, la scheda Subscribers (Sottoscrittori) offre informazioni dettagliate sui sottoscrittori, tra cui:
- Nome e cognome di ogni sottoscrittore.
- L'indirizzo e-mail per questo utente.
- Il livello di sottoscrizione assegnato.
- La data in cui è stata assegnata la sottoscrizione. 
- La data di scadenza della sottoscrizione.
- Una descrizione facoltativa in formato testo.
- Indicazione relativa all'abilitazione/disabilitazione del download per il sottoscrittore. 
- Il paese in cui si trovano.
- Le preferenze della lingua per la posta elettronica per le comunicazioni relative all'assegnazione da parte del portale degli amministratori.
- Un campo facoltativo per un altro indirizzo e-mail usato per le comunicazioni di accesso. 

Sul lato sinistro della pagina è possibile visualizzare informazioni aggiuntive sul numero di licenze acquistate, assegnate e ancora disponibili nella propria organizzazione per ogni contratto.

   ![Pagina relativa ai sottoscrittori del portale di amministrazione sottoscrizioni di Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Informazioni sulla pagina relativa ai dettagli
Per altre informazioni sul contratto visualizzato, selezionare la scheda dettagli. Visualizza lo stato del contratto, dell'account di acquisto, i dettagli dell'organizzazione, i contatti principali (VLSC), gli amministratori con privilegi elevati (se disponibile) e altre informazioni di acquisto.

   ![Pagina relativa ai dettagli del portale di amministrazione delle sottoscrizioni di Visual Studio](_img/using-admin-portal/details-page.png)

