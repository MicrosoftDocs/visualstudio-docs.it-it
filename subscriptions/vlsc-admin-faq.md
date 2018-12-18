---
title: Domande frequenti sulla migrazione dell'amministrazione di VLSC | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: Get-Started-Article
description: Domande frequenti sulla migrazione dell'amministrazione del Volume License Service Center
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 014564880dcc7587a1f94e3815d6f36edb36cee3
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Migrazione dell'amministrazione delle sottoscrizioni di Visual Studio

Nei prossimi mesi saranno introdotte modifiche che interesseranno la gestione delle sottoscrizioni di Visual Studio (in precedenza sottoscrizioni MSDN). Attualmente, le sottoscrizioni di Visual Studio possono essere acquistate tramite contratti multilicenza e vengono gestite nel portale del Volume License Service Center (VLSC). Nascerà un nuovo portale di gestione, nel quale saranno gestite le sottoscrizioni di Visual Studio. Oltre alle operazioni attualmente offerte da VLSC, il nuovo portale consentirà di eseguire l'assegnazione in blocco senza alcun limite, verificare e filtrare le sottoscrizioni e di usare Azure Active Directory (Azure AD) per gestire l'accesso. Il nuovo portale di amministrazione di Visual Studio sarà disponibile all'indirizzo: [https://manage.visualstudio.com](https://manage.visualstudio.com). 

> [!Note] 
> Questa migrazione non interesserà i clienti MPSA. 

## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="why-is-it-changing"></a>Perché cambia?
Il nuovo portale consentirà di ottimizzare l'esperienza di gestione delle sottoscrizioni di Visual Studio e di creare un'esperienza unica di gestione delle sottoscrizioni di Visual Studio, indipendentemente dal canale di acquisto. Il nuovo portale è costituito da una nuova piattaforma che consente di abilitare Azure AD ed essere usato in futuro. Avrà anche un'interfaccia utente aggiornata che risulterà più semplice da esplorare e usare per garantire massima efficienza all'amministratore.

### <a name="who-will-be-impacted"></a>Chi sarà interessato dalla modifica? 
La modifica interesserà tutti i clienti che sono in possesso di contratti multilicenza attivi e che hanno acquistato sottoscrizioni di Visual Studio tramite contratti multilicenza. 

### <a name="when-is-it-changing"></a>Quando avverrà il cambiamento?
Si tratta di una transizione molto importante e verrà completata in fasi fino quando sarà stata eseguita la migrazione di tutti i clienti con contratti multilicenza attivi per sottoscrizioni di Visual Studio al nuovo portale di gestione. La migrazione ha avuto inizio nel primo trimestre del 2017. Ai clienti con contratti multilicenza sarà anticipatamente comunicata la settimana pianificata in cui sarà eseguita la loro migrazione.  

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>È necessario iscrivere l'organizzazione ad Azure Active Directory (Azure AD)?
Non è necessario iscrivere l'organizzazione ad Azure AD. È comunque possibile eseguire tale operazione in qualsiasi momento. È possibile scegliere di caricare Azure AD senza alcun costo usando il livello gratuito per Azure AD. Azure Active Directory consente di proteggere l'organizzazione aumentando sicurezza, controllo e affidabilità a lungo termine. Se non si è pronti per Azure AD, sarà comunque possibile continuare a usare gli account Microsoft. 

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>In che modo l'organizzazione viene informata della migrazione?
Microsoft invierà un messaggio di posta elettronica ai contatti principali o per le comunicazioni invitandoli a completare il processo di caricamento una settimana prima della migrazione dell'organizzazione. Anche i gestori delle sottoscrizioni riceveranno un messaggio di posta elettronica per informarli che Microsoft ha contattato i contatti primari o per le comunicazioni e ha comunicato i dettagli necessari per eseguire correttamente il caricamento. Informazioni su come [individuare i contatti principali o per le comunicazioni dell'organizzazione](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?). 

### <a name="is-onboarding-different-from-migration"></a>L'operazione di caricamento è diversa dalla migrazione?
Sì.  Questo processo prevede due fasi. Se si esegue la configurazione (o il caricamento) dell'organizzazione prima della migrazione, le attività dell'amministratore non saranno interrotte. Dopo aver eseguito la migrazione delle informazioni dell'organizzazione, sarà possibile gestire le sottoscrizioni di Visual Studio nel nuovo portale. Se i contatti principali o per le comunicazione non si occupano del caricamento prima della migrazione, i gestori delle sottoscrizioni verranno bloccati e non sarà possibile gestire le sottoscrizioni fino al completamento del processo di caricamento. 

### <a name="what-is-the-onboarding-process"></a>Che cos'è il processo di caricamento?
Un messaggio di posta elettronica viene inviato ai contatti principali o per le comunicazione invitandoli a completare il processo di caricamento. Per istruzioni sul processo, leggere quanto riportato di seguito. 
1.  **Individuazione del PCN e accesso:**

    a.  I contatti principali e per le comunicazioni ricevono un messaggio di posta elettronica contenente un collegamento univoco e le ultime tre cifre del numero PCN.* 

    b.  Per ottenere il PCN completo, il contatto principale deve accedere a VLSC (le istruzioni per l'individuazione del PCN sono disponibili di seguito). 

    c.  Dopo aver ottenuto il PCN, sarà necessario selezionare il collegamento univoco richiesto per accedere. Sarà possibile accedere usando un account di lavoro o dell'istituto di istruzione (se l'organizzazione si trova in Azure AD) o un account Microsoft se l'organizzazione non è presente in Azure AD. 

    d.  Successivamente, sarà richiesto di immettere il PCN. 

2.  **Configurare gli amministratori.**

    Dopo aver immesso il PCN, si aprirà la pagina in cui sarà possibile aggiungere amministratori e amministratori con privilegi elevati (precedentemente noti come gestori delle sottoscrizioni). Sarebbe buona norma completare tale operazione prima della data di migrazione dell'organizzazione. In questo modo si evitano interruzioni nella gestione delle sottoscrizioni. 

3.  **Accesso al nuovo portale di gestione delle sottoscrizioni:** dopo aver eseguito la migrazione dell'organizzazione, gli amministratori e gli amministratori con privilegi elevati riceveranno dei messaggi di posta elettronica per eseguire l'accesso al nuovo portale e iniziare a gestire le sottoscrizioni. 

> [!NOTE] 
> Se il contatto principale o per le comunicazioni riceve più di un messaggio di posta elettronica, significa che ha più PCN. È necessario completare il processo usando il collegamento univoco per il PCN a cui si fa riferimento in ogni messaggio di posta elettronica. 

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>Che differenza c'è tra amministratore e amministratore con privilegi elevati?
Quando il contatto principale o per le comunicazioni accede per la prima volta, viene automaticamente impostato come amministratore con privilegi elevati. Gli amministratori con privilegi elevati possono gestire l'accesso dell'amministratore alle sottoscrizioni aggiungendo o eliminando altri amministratori o amministratori con privilegi elevati e possono anche gestire le sottoscrizioni. L'amministratore con privilegi elevati può scegliere di assegnare altri amministratori con privilegi elevati oltre a sé.

Gli amministratori (precedentemente noti come gestori delle sottoscrizioni) possono solo gestire le sottoscrizioni, non possono controllare chi ha accesso alla gestione delle sottoscrizioni. 

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>In che modo un amministratore può eseguire il caricamento al nuovo portale?
I contatti principali e per le notifiche dell'organizzazione riceveranno un messaggio di posta elettronica contenente un collegamento univoco a una pagina che consentirà loro di accedere usando un account di lavoro o dell'istituto di istruzione supportato da Azure Active Directory (Azure AD) o un account Microsoft personale. Dopo aver eseguito l'accesso, sarà necessario immettere il numero PCN dell'organizzazione o il numero di autorizzazione per verificare i contratti. Questi contatti saranno poi configurati come amministratori con privilegi elevati che potranno aggiungere altri amministratori per gestire le sottoscrizioni di Visual Studio. 

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>In che punto è possibile gestire le sottoscrizioni se l'organizzazione è stata caricata, ma non è ancora stata eseguita la migrazione? 
Si continuerà a gestire le sottoscrizioni tramite VLSC fino al ricevimento del messaggio di posta elettronica dalle sottoscrizioni di Visual Studio in cui si avvisa l'organizzazione che è stata eseguita la migrazione ed è pronta per essere gestita nel nuovo portale. 

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>Dove può essere individuato il numero PCN o il numero di autorizzazione?
Accedere a [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e selezionare il percorso seguente: **Sottoscrizioni** > **Sottoscrizioni di Visual Studio**. Il PCN si trova sotto **Agreement/Public Customer Number Results** (Contratti/Risultati numero cliente pubblico). Seguire la procedura dettagliata sull'individuazione del numero PCN riportato in questo [articolo della Guida](/find-pcn/). 

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>In che modo si stabilisce chi è il contatto principale o per le comunicazioni?
Accedere a [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e selezionare percorso seguente: **Licenze > Riepilogo relazione** Selezionare **Licensing ID > Contacts** (ID di licenza > Contatti). Seguire la procedura dettagliata sull'individuazione del contatto principale o per le comunicazioni in questo [articolo della Guida](/find-primary-contact/). 

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>Cosa accade se il contatto principale o per le comunicazioni ha lasciato o non lavora più per la società oppure non è disponibile per completare il caricamento?
È necessario [contattare l'assistenza](https://www.visualstudio.com/subscriptions/support/#talktous) e comunicare il messaggio di posta elettronica usato in VLSC per la gestione delle sottoscrizioni. Dopo aver eseguito la verifica, l'assistenza offrirà supporto per eseguire il processo di caricamento. 

### <a name="what-will-happen-with-renewing-customers"></a>Cosa accade ai clienti che eseguono il rinnovo? 
I clienti che eseguono il rinnovo continueranno a rinnovare le sottoscrizioni come di consueto. I processi di rinnovo non sono infatti interessati dalla migrazione. 

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>È necessario che l'organizzazione attenda prima di configurare un nuovo contratto nel nuovo sistema, anziché rinnovare un contratto esistente? 
No.  La migrazione non condizionerà la creazione o il rinnovo dei contratti. 

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>Cosa accade se il contratto dell'organizzazione si trova in un periodo di tolleranza durante la transizione? Sarà comunque eseguita la migrazione?
Sì. Se il contratto è ancora attivo, sarà eseguita la migrazione dell'organizzazione. 

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>Cosa accade se per l'organizzazione sono presenti richieste in eccedenza nel sistema corrente? Sarà comunque eseguita la migrazione al nuovo sistema? 
Sì. Verrà comunque eseguita la migrazione dell'organizzazione al nuovo sistema. Per i tipi di contratto che lo consentono, il nuovo sistema offrirà la possibilità di gestire richieste in eccedenza. 

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>Cosa accade se l'organizzazione ha più di una sottoscrizione assegnata a un unico utente o indirizzo di posta elettronica?
Verrà comunque eseguita la migrazione dell'organizzazione.  Non sarà tuttavia possibile assegnare sottoscrizioni aggiuntive dello stesso livello, ad esempio Enterprise, Professional, e così via, a tale utente o indirizzo di posta elettronica. Tutte le sottoscrizioni dello stesso livello che hanno il medesimo indirizzo di posta elettronica al momento della migrazione saranno ancora visibili. Gli amministratori dovranno tuttavia modificare gli indirizzi di posta elettronica in modo che siano univoci. Non sarà possibile assegnare più sottoscrizioni dello stesso livello a un solo utente o indirizzo di posta elettronica nel nuovo portale.

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>Dove è possibile trovare le informazioni più aggiornate relative alla migrazione? 
Per informazioni aggiornate sulla migrazione, visitare la [pagina Web](https://aka.ms/vs-admin) dell'amministratore delle sottoscrizioni di Visual Studio. Per assistenza, visitare la [pagina di supporto](http://www.visualstudio.com/subscriptions/support/#!collections/962-subscriptions) di Visual Studio che contiene informazioni per risolvere i problemi autonomamente e informazioni per contattare l'assistenza. Per facilitare questo processo di transizione, nei prossimi mesi continueranno a essere aggiunti aggiornamenti nella pagina Web di amministrazione e inviati tramite posta elettronica. 

## <a name="resources-and-support-information"></a>Risorse e informazioni per assistenza
- [Pagina Web di amministrazione](https://www.visualstudio.com/subscriptions-administration/)

- [Supporto](https://www.visualstudio.com/subscriptions/support/) per le sottoscrizione di Visual Studio e la gestione 

- [Come individuare il numero PCN](/find-pcn/)

- [Come individuare il contatto principale o per le comunicazioni](/find-primary-contact/) 

- [Video](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) su caricamento dell'organizzazione e amministratori di gestione 
