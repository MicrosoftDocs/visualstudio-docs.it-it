---
title: Identità per i sottoscrittori di Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identità per i sottoscrittori di Visual Studio

Quando si attiva la sottoscrizione di Visual Studio, l'identità (o l'account di accesso) usata durante l'attivazione viene collegata alla sottoscrizione di Visual Studio. In questo modo, è possibile riconoscere l'utente nel [portale per i sottoscrittori Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in Visual Studio Team Services e in Azure.

In Visual Studio Team Services, lo stato della sottoscrizione di Visual Studio viene controllato a ogni accesso e vengono concesse automaticamente le funzionalità incluse per ogni account in cui si è membri. Poiché queste funzionalità sono incluse come vantaggio per i sottoscrittori, un utente può essere aggiunto gratuitamente come membro di qualsiasi account di Visual Studio Team Services quando si usa un'identità collegata alla sottoscrizione di Visual Studio.

In Azure, lo stato della sottoscrizione di Visual Studio viene controllato quando si attiva il [credito di Azure mensile](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) che è un vantaggio dei sottoscrittori.

All'interno del [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), potrebbe essere possibile aggiungere un'**identità alternativa** oltre a quella usata durante l'attivazione. Attualmente l'aggiunta di un'identità alternativa è consentita se è stato usato un account Microsoft per attivare la sottoscrizione. In questo modo è possibile aggiungere anche un account aziendale o dell'istituto di istruzione (usato per l'accesso a Visual Studio, Office 365 o alla rete aziendale o dell'istituto di istruzione), consentendo l'accesso a Visual Studio Team Services tramite l'account personale e l'account aziendale o dell'istituto di istruzione.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Come aggiungere un'identità alternativa alla sottoscrizione di Visual Studio

1. Accedere al [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Se viene richiesto di scegliere "account personale" o "account aziendale o dell'istituto di istruzione", scegliere "account personale" (l'account Microsoft).
  >
  > In alcuni casi è necessario scegliere perché l'account Microsoft e l'account aziendale o dell'istituto di istruzione condividono lo stesso indirizzo di posta elettronica. Anche se entrambe le identità usano lo stesso indirizzo di posta elettronica, sono comunque identità separate con profili, impostazioni di sicurezza e autorizzazioni diversi.
  >
  > A partire dal 30 marzo 2018 non sarà più possibile creare un account Microsoft con un indirizzo di posta elettronica che usa un dominio gestito in Azure Active Directory. È comunque possibile accedere usando questo indirizzo di posta elettronica come account aziendale.

2. Passare alla scheda **Sottoscrizioni**.

  ![Scegliere Sottoscrizioni](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. In **Collegamenti correlati** passare ad **Aggiungi un account alternativo**.

  ![In Collegamenti correlati passare ad Aggiungi un account alternativo](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Immettere l'account aziendale o dell'istituto di istruzione e scegliere **Aggiungi**.

  ![Immettere l'account aziendale o dell'istituto di istruzione](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Usare l'account aziendale o dell'istituto di istruzione per accedere all'account di VSTS (```https://{youraccount}.visualstudio.com```). Potrebbe esserci un leggero ritardo per la propagazione delle informazioni, quindi controllare di nuovo dopo 15 minuti. 

## <a name="faq"></a>Domande frequenti

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>D: perché VSTS non riconosce un utente come sottoscrittore di Visual Studio?
R: VSTS dovrebbe riconoscere automaticamente la sottoscrizione quando si esegue l'accesso con l'identità primaria o alternativa. In caso contrario, è possibile:

* Controllare di avere una sottoscrizione di Visual Studio attiva che [include VSTS come vantaggio](vs-vsts.md).

* Assicurarsi di usare un account di accesso o un'identità che rappresenta l'identità primaria o alternativa per la sottoscrizione di Visual Studio.

* Visitare il [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) almeno una volta prima di accedere a VSTS.

Se VSTS non riconosce ancora la sottoscrizione, [contattare il supporto tecnico](https://www.visualstudio.com/team-services/support/)

