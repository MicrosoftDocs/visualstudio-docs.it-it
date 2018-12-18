---
title: Messaggi di posta elettronica personali visualizzati In VLSC
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori? 

Man mano che le società completano la migrazione da Volume Licensing Service Center (VLSC) al nuovo [portale di amministrazione delle sottoscrizioni](https://manage.visualstudio.com) di Visual Studio, gli amministratori potrebbero notare con sorpresa che per l'indirizzo di posta elettronica di accesso per alcuni sottoscrittori sono indicati indirizzi di posta elettronica di terze parti come Hotmail, Gmail o Yahoo!.

## <a name="cause"></a>Causa

Questo scenario si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati MSDN. La migrazione degli utenti da VLSC al nuovo portale è stata completata senza modifiche. Alcuni amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della sottoscrizione loro assegnati. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore:
1. Era necessario un account Microsoft per accedere.
2. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio John@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente.
3. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE] 
> La nuova esperienza per i sottoscrittori in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) supporta sia i tipi di identità con account aziendale o dell'istituto di istruzione che con account Microsoft.

Infine, poiché per la migrazione degli amministratori vengono recuperati i dati dell'indirizzo di posta elettronica di accesso del sottoscrittore da VLSC per popolare la nuova esperienza di gestione dei sottoscrittori, gli amministratori di cui è stata eseguita la migrazione di recente potrebbero notare questi account personali passati inosservati in precedenza a causa di modifiche all'interfaccia utente che rendono più visibili queste informazioni.

## <a name="solution"></a>Soluzione

Per risolvere il problema, è necessario modificare le informazioni sui sottoscrittori per aggiornare i relativi indirizzi di posta elettronica di accesso.  È possibile apportare le modifiche per singoli sottoscrittori o in blocco. Per informazioni complete, vedere [Modificare una sottoscrizione](/visualstudio/subscriptions/edit-license).  

Dopo aver aggiornato gli indirizzi di posta elettronica dei Sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  