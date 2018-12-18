---
title: VSTS per i sottoscrittori di Visual Studio | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Understand how you can use Visual Studio Team Services (VSTS) as a Visual Studio subscriber.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: d3287740daded32afa9b93e109a76b1804e82a75
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-team-services-vsts-benefit-in-visual-studio-subscriptions"></a>Vantaggio Visual Studio Team Services (VSTS) nelle sottoscrizioni di Visual Studio

## <a name="overview"></a>Panoramica 
Repository Git gratuiti, strumenti di pianificazione e build ospitate Agile, per qualsiasi linguaggio: il complemento perfetto per l'IDE. 
- Creare l'ambiente di sviluppo perfetto per il team. 
- Sempre connessi dall'idea al rilascio. 
- Migliorare la qualità del codice e rilevare subito i problemi.
- Automatizzare e semplificare le distribuzioni di Azure.
- Migliorare la produttività con funzionalità avanzate. 

## <a name="eligibility"></a>Idoneità
| Livello di sottoscrizione/Programma                                                  | Vantaggio               | Rinnovabile?                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | Accesso Advanced       |  Yes                                                               |
| Visual Studio Enterprise (annuale)                                               | Accesso Advanced       |  Yes                                                               |
| Visual Studio Enterprise (mensile)                                              | Accesso Advanced       |  Yes                                                               |
| Visual Studio Professional Standard                                           | Accesso Basic          |  Yes                                                               |
| Visual Studio Professional (annuale)                                             | Accesso Basic          |  Yes                                                               | 
| Visual Studio Professional (mensile)                                            | Accesso Basic          |  Yes                                                               |
| Visual Studio Test Pro                                                        | Accesso Advanced       |  Yes                                                               |
| MSDN Platforms                                                                | Accesso Advanced       |  Yes                                                               |
| Visual Studio Dev Essentials                                                  | Stakeholder           |  Yes                                                               |
| Visual Studio Enterprise - NFR<sup>1</sup>                                               | Accesso Advanced       |  Yes                                                               |
| Visual Studio Enterprise - FTE                                                | Accesso Advanced       |  Yes                                                               |
| Visual Studio Enterprise - Microsoft Partner Network                          | Accesso Advanced       |  Yes                                                               |
| Visual Studio Professional - Microsoft Partner Network                        | Accesso Basic          |  Yes                                                               |
| Visual Studio Enterprise - Imagine (Standard)                                 | Accesso Basic          |  Yes                                                               |
| Visual Studio Enterprise - Imagine (Premium)                                  | Accesso Basic          |  Yes                                                               |
| Visual Studio Enterprise - BizSpark                                           | Accesso Advanced       |  Yes                                                               |
| Microsoft Certified Trainer - Software & Services                             | Accesso Basic          |  Yes                                                               |
| Microsoft Certified Trainer - Developer Software & Services                   | Accesso Advanced       |  Yes                                                               |

<sup>1</sup>  *Include: Not for Resale (NFR), Microsoft Valued Partner (MVP), Region Director (RD), Visual Studio Industry Partner (VSIP)*  

Non si è certi della sottoscrizione in uso?  Connettersi a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) per visualizzare tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni. 

Quando si accede a Visual Studio Team Services usando la stessa identità usata per attivare la sottoscrizione di Visual Studio, l'identità viene riconosciuta automaticamente. Questo procedimento funziona sia per l'identità primaria usata quando si accede al Portale sottoscrittore, sia per eventuali identità alternative configurate per la sottoscrizione di Visual Studio. VSTS supporta sia gli account Microsoft (ad esempio @outlook.com), sia gli account aziendali o dell'istituto di istruzione (che usano Azure Active Directory gestito dall'organizzazione). È possibile usare sia l'identità primaria, sia le identità alternative in Visual Studio Team Services e unire qualsiasi numero di account VSTS come membri.

Per usare VSTS è necessario un account. È possibile accedere con un account esistente o crearne uno nuovo.  Per creare un nuovo account:
1.  Accedere a [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).
2.  Individuare il riquadro di Visual Studio Team Services nella sezione Strumenti e fare clic sul collegamento "Inizia subito" nella parte inferiore del riquadro del vantaggio.   

Queste funzionalità di VSTS sono incluse nelle sottoscrizioni seguenti: 
- Visual Studio Enterprise: [Basic](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web), [Gestione pacchetti](https://marketplace.visualstudio.com/items?itemName=ms.feed)
- Visual Studio Professional: [Basic](https://www.visualstudio.com/team-services/compare-features/)
- Piattaforme MSDN: [Basic](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)
- Visual Studio Test Professional: [Basic](https://www.visualstudio.com/team-services/compare-features/), [Test Manager](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)

3.  Immettere un nome per il sito del progetto VSTS.  

4.  Scegliere se usare **Git** o il **controllo della versione di Team Foundation** per gestire il progetto.  Questa è una scelta permanente per ogni progetto team creato, ma si possono usare progetti team TFVC e Git nella stessa raccolta di progetti team.  In caso di incertezze: 
    - Git: Git è un sistema di controllo della versione decentralizzato. Ogni sviluppatore ha una copia dell'intero repository di origine nel computer di sviluppo. Gli sviluppatori possono eseguire il commit di ciascun insieme di modifiche nel computer di sviluppo ed eseguire operazioni di controllo della versione quali la cronologia e il confronto senza connessione di rete.  [Altre informazioni](https://www.visualstudio.com/docs/git/gitquickstart) su Git.
    - Controllo della versione di Team Foundation: il controllo della versione di Team Foundation è un sistema di controllo della versione centralizzato. In genere, i membri del team hanno una sola versione di ogni file nel computer di sviluppo. I dati cronologici vengono gestiti solo sul server. I branch sono basati sul percorso e creati nel server. [Altre informazioni](https://www.visualstudio.com/docs/tfvc/overview) sul controllo della versione di Team Foundation.

 
5.  Fare clic su **Modifica dettagli** per personalizzare le opzioni relative al nome del progetto, alla modalità di organizzazione del lavoro (Agile, Scrum, CMMI), alla posizione in cui ospitare i progetti e alla modalità di condivisione del lavoro con altri utenti.  Fare clic su "Continua".

# <a name="create-your-vsts-account"></a>Creare il proprio account VSTS

6.  La creazione dell'account richiede un attimo. Subito dopo verrà visualizzata la pagina di VSTS per il primo progetto con il nome specificato.  A questo punto è tutto pronto per iniziare a usare Visual Studio Team Services.

Si riceverà anche un messaggio di posta elettronica di conferma della creazione dell'account  con l'URL e i dati di accesso dell'account e gli indirizzi di posta elettronica preferiti.  

![Messaggio di benvenuto del vantaggio VSTS](_img\vs-vsts\vs-vsts-welcome.png)


## <a name="faq"></a>Domande frequenti
### <a name="q--what-is-the-difference-between-free-basic-access-and-advanced-access"></a>D: quali sono le differenze tra i livelli di accesso gratuito, Basic e Advanced?
R: le funzionalità disponibili variano in base al livello di accesso.  Qui è possibile trovare informazioni dettagliate sui [livelli di accesso](/vsts/security/access-levels). 

### <a name="q--how-do-i-add-users-to-my-vsts-account-or-team-project"></a>D: qual è la procedura per aggiungere utenti a un account o a un progetto team VSTS?
R: informazioni su come [gestire gli utenti e l'accesso](/vsts/accounts/add-account-users-from-user-hub) in VSTS.

## <a name="support-resources"></a>Risorse di supporto
-  Per assistenza per le vendite, le sottoscrizioni, gli account e la fatturazione per le sottoscrizioni di Visual Studio, contattare il [servizio di supporto per le sottoscrizioni](https://www.visualstudio.com/subscriptions/support/) di Visual Studio.
-  Per domande sull'IDE di Visual Studio, Visual Studio Team Services o altri prodotti e servizi Visual Studio,  visitare il [sito del supporto di Visual Studio](https://www.visualstudio.com/support/). 
-  Per la documentazione completa di Visual Studio Team Services, visitare /vsts/.
Per usare Visual Studio Team Services, è necessario creare un account o essere aggiunti come membri in un account di proprietà di un altro utente. La creazione di un account VSTS è gratuita ed è possibile creare più account VSTS. 

[Come iscriversi per Visual Studio Team Services](/vsts/accounts/index)
