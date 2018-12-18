---
title: Messaggi di posta elettronica personali visualizzati In VLSC
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: cfe035d82976e3df683f4e3a35bd9d7f3c8cf9e2
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori? 

Man mano che le società completano la migrazione da Volume Licensing Service Center (VLSC) al nuovo [portale di amministrazione delle sottoscrizioni](https://manage.visualstudio.com) di Visual Studio, gli amministratori potrebbero notare con sorpresa che per l'indirizzo di posta elettronica di accesso per alcuni sottoscrittori sono indicati indirizzi di posta elettronica di terze parti come Hotmail, Gmail o Yahoo!.

## <a name="cause"></a>Causa

Questo scenario si verifica a causa dei processi di accesso associati all'esperienza legacy dei sottoscrittori msDN. La migrazione degli utenti da VLSC al nuovo portale è stata completata senza modifiche. Alcuni amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della sottoscrizione loro assegnati. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore: veniva richiesto un account Microsoft per eseguire l'accesso. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio John@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE] 
> La nuova esperienza per i sottoscrittori in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) supporta sia i tipi di identità con account aziendale o dell'istituto di istruzione che con account Microsoft.

Infine, poiché per la migrazione degli amministratori vengono recuperati i dati dell'indirizzo di posta elettronica di accesso del sottoscrittore da VLSC per popolare la nuova esperienza di gestione dei sottoscrittori, gli amministratori di cui è stata eseguita la migrazione di recente potrebbero notare questi account personali passati inosservati in precedenza a causa di modifiche all'interfaccia utente che rendono più visibili queste informazioni.

## <a name="solution"></a>Soluzione

Per risolvere il problema, è necessario modificare le informazioni sui sottoscrittori per aggiornare i relativi indirizzi di posta elettronica di accesso.  È possibile apportare le modifiche per singoli sottoscrittori o in blocco. Per informazioni complete, vedere [Modificare una sottoscrizione](/visualstudio/subscriptions/edit-license).  

Dopo aver aggiornato gli indirizzi di posta elettronica dei Sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  