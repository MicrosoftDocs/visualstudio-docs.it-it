---
title: Configurazione degli amministratori per le sottoscrizioni cloud | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/28/2018
ms.topic: Get-Started-Article
description: Configurazione degli amministratori per le sottoscrizioni cloud
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 861862d964d5ccd8e926730f648a41bc790bc64d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283444"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Configurare gli amministratori per le sottoscrizioni cloud di Visual Studio

Le sottoscrizioni cloud di Visual Studio sono gestite dagli amministratori. Gli amministratori possono assegnare le sottoscrizioni, modificare le assegnazioni, aggiungere o eliminare le sottoscrizioni ed eseguire altre attività di gestione delle sottoscrizioni.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Il proprietario della sottoscrizione di Azure è il primo amministratore

Quando si acquistano sottoscrizioni cloud di Visual Studio, il proprietario della sottoscrizione di Azure usata per effettuare gli acquisti viene configurato automaticamente come amministratore delle sottoscrizioni.

È possibile acquistare sottoscrizioni cloud tramite [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) o contattando un Cloud Solution Provider. Se si acquista tramite Visual Studio Marketplace, al termine dell'esperienza di acquisto, viene offerta la possibilità di gestire gli utenti. Se si sceglie questa opzione, viene visualizzato il portale di gestione delle sottoscrizioni di Visual Studio - [https://manage.visualstudio.com](https://manage.visualstudio.com).

Dopo aver acquistato le sottoscrizioni, è possibile visitare il [portale di gestione](https://manage.visualstudio.com) in qualsiasi momento. È sufficiente accedere al portale e selezionare la sottoscrizione di Azure appropriata nell'angolo superiore sinistro.

Il proprietario della sottoscrizione di Azure usata per l'acquisto delle sottoscrizioni cloud può anche assegnare altri amministratori.

## <a name="add-administrators"></a>Aggiungere gli amministratori

Per aggiungere gli amministratori:

1. Connettersi al portale di Azure all'indirizzo [portal.azure.com](https://portal.azure.com).
2. Accedere con l'account usato per acquistare le sottoscrizioni cloud di Visual Studio.
3. Nel riquadro di spostamento di sinistra scorrere verso il basso su **Gestione costi + Fatturazione**.
4. Nell'elenco **Sottoscrizioni personali** scegliere la sottoscrizione di Azure usata per effettuare l'acquisto.
5. Fare clic su **Controllo dell'accesso** nella parte superiore dell'elenco nel riquadro di spostamento di sinistra.
6. Fare clic sulla scheda **Aggiungi** nella parte superiore della pagina.
7. Nel riquadro di uscita a destra fare clic sul nome del sottoscrittore che si vuole configurare come amministratore.
8. Fare clic sull'elenco a discesa **Ruolo** nella parte superiore del riquadro, scorrere verso il basso e selezionare **Amministratore Accesso utenti**.
9. Fare clic su **Salva**.

Il sottoscrittore designato viene visualizzato al centro della pagina con il ruolo "Amministratore Accesso utenti".

Il nuovo amministratore potrà ora accedere al [portale di gestione](https://manage.visualstudio.com), selezionare la stessa sottoscrizione di Azure usata per l'acquisto delle sottoscrizioni cloud dall'elenco nell'angolo superiore sinistro della pagina e iniziare a gestire le sottoscrizioni.


> [!NOTE]
> Se si visualizzano utenti con autorizzazioni per la modifica delle sottoscrizioni cloud dell'utente che l'utente stesso non ha impostato come amministratori, è possibile che tali utenti abbiano ruoli nella sottoscrizione di Azure sottostante che consentono loro la gestione delle sottoscrizioni. Tali ruoli includono: proprietario, collaboratore, amministratore dei servizi o coamministratore. Per altre informazioni, visitare [Billing management](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts) (Gestione della fatturazione).

Per informazioni sulle sottoscrizioni cloud di Visual Studio, vedere [Panoramica](vscloud-overview.md) in Acquisto di sottoscrizioni cloud. Per acquistare sottoscrizioni cloud di Visual Studio, visitare Visual Studio Marketplace all'indirizzo [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).