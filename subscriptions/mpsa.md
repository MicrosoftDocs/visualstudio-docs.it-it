---
title: Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement) | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a18565a97c0cd85ce42109961592a57c490d92a1
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)

Se sono state acquistate sottoscrizioni di Visual Studio tramite il programma MPSA, è necessario tenere presente alcuni aspetti prima di poter diventare un amministratore di sottoscrizioni di Visual Studio e assegnare le sottoscrizioni agli utenti. Se si è già stati configurati come amministratore, è possibile passare direttamente al [portale di amministrazione](https://manage.visualstudio.com/) delle sottoscrizioni di Visual Studio. 

I clienti MPSA vengono indirizzati a un portale in cui è possibile gestire gli asset acquistati tramite MPSA. Il nuovo portale è chiamato [Business Center](https://businessaccount.microsoft.com/) e supporta alcune delle nuove funzionalità disponibili in Volume Licensing Service Center (VLSC). Queste funzionalità includono la visualizzazione di Riepilogo licenze, Ordini, Download, Chiavi, Utenti e così via. Tuttavia, le sottoscrizioni di Visual Studio in MPSA sono simili ai Servizi cloud. Anche in Business Center l'accesso viene eseguito tramite gli account aziendali anziché gli account Microsoft. Se l'organizzazione usa servizi cloud come Office 365 o Azure Active Directory e la posta elettronica è inclusa in uno di questi due servizi, l'account è già un account aziendale. Di conseguenza, sarà possibile eseguire la registrazione in Business Center con la password già assegnata dalla propria organizzazione. Se l'organizzazione non usa servizi cloud e l'indirizzo di posta elettronica non è un account aziendale, è comunque possibile usarlo per eseguire la registrazione in Business Center.

Inoltre, dopo essere stati configurati come amministratori di Visual Studio è possibile usare il [portale di amministrazione](https://manage.visualstudio.com/) delle sottoscrizioni di Visual Studio per assegnare le sottoscrizioni ai sottoscrittori. In MPSA è necessario eseguire il provisioning delle sottoscrizioni di Visual Studio nel portale di gestione corrispondente, ovvero nel portale di amministrazione delle sottoscrizioni di Visual Studio. A tale scopo, associare l'account di acquisto a un tenant, ad esempio contoso.onmicrosoft.com. 

Si noti che sono disponibili due tipi di tenant: un tenant gestito e un tenant non gestito. Un tenant gestito è un tenant già gestito dall'organizzazione che include amministratori. 

Un tenant non gestito è un tenant senza amministratori e non può essere usato per i servizi online come Office 365. I tenant non gestiti vengono creati anche quando la registrazione in Business Center viene eseguita con un indirizzo di posta elettronica che non è un account aziendale. Se viene richiesto di creare una password durante la registrazione in Business Center, significa che l'indirizzo di posta elettronica specificato non è un account aziendale e viene creato un tenant non gestito.

Per essere configurato come amministratore delle sottoscrizioni di Visual Studio sono necessari i requisiti e i passaggi seguenti prima di completare l'associazione del tenant.

## <a name="pre-tenant-association-managed-tenant"></a>Associazione pre-tenant (tenant gestito)
-   È necessario essere un utente registrato in Business Center.
-   È necessario essere un amministratore utenti (requisito minimo) o un amministratore globale all'interno del tenant cui si appartiene. (Questo requisito si applica se la società usa già i Servizi cloud). Ogni ruolo deve essere un amministratore delle sottoscrizioni di Visual Studio.
-   È necessario essere un amministratore globale nel tenant cui si appartiene per poter associare l'account di acquisto al tenant.
-   È necessario essere un amministratore account o un account manager in Business Center.
-   Il campo "Paese o area geografica" all'interno del proprio profilo utente o di un altro utente in [Azure](https://portal.azure.com/) deve essere popolato correttamente in base all'area geografica (ad esempio US, CA e così via). 

> [!NOTE]
> Gli utenti che si vuole configurare come amministratori delle sottoscrizioni di Visual Studio non devono essere utenti in Business Center ma solo soddisfare i criteri dei passaggi 2 e 5.

Dopo aver soddisfatto i criteri dei 5 passaggi precedenti è possibile associare l'account di acquisto al tenant eseguendo la procedura che segue.
1.  Accedere a [Business Center](https://businessaccount.microsoft.com/).
2.  Fare clic sulla scheda **Account** e scegliere **Associa dominio**.
3.  Selezionare l'**account di acquisto** se sono disponibili più account.
4.  Selezionare il **tenant**, ad esempio contoso.onmicrosoft.com.
5.  Fare clic su **Associa dominio**.

Solitamente, trascorsi pochi minuti dall'associazione, tutti gli utenti che soddisfano i criteri necessari eseguono il provisioning come amministratori delle sottoscrizioni di Visual Studio. In alcuni casi, tuttavia, potrebbe essere necessario attendere fino a 24 ore. Dopo il provisioning sarà possibile accedere al portale di amministrazione delle sottoscrizioni di Visual Studio. Se l'operazione richiede più di 24 ore, contattare il supporto MPSA.

> [!NOTE]
> Se sono presenti nuovi utenti che, dopo l'associazione, soddisfano i criteri dei passaggi 2 e 5, è necessario contattare il supporto MPSA. Il supporto MPSA offrirà assistenza per eseguire il provisioning dei nuovi amministratori delle sottoscrizioni di Visual Studio.

## <a name="tenant-association-unmanaged"></a>Associazione del tenant (non gestito)

Se è stata eseguita la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale (non registrato in Azure Active Directory "Azure AD"), come descritto nel quinto paragrafo precedente, l'associazione del tenant sarà leggermente diversa. Sarà necessario eseguire un "take-over del dominio". Durante questo processo sarà necessario configurare se stessi come amministratore globale e modificare il tenant da non gestito a gestito.

Per una descrizione più dettagliata di questo processo,vedere le [guide rapide](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Scaricare la guida denominata *"Setup and Use Your Online Services"* (Configurare e usare i servizi online) per istruzioni su come eseguire il take-over di un dominio. Al termine, anche l'account di acquisto risulterà associato al tenant.

> [!NOTE]
> Dopo aver completato il processo di take-over del dominio, è necessario soddisfare i criteri dei cinque passaggi della sezione Associazione pre-tenant (tenant gestito). Dopo aver soddisfatto i criteri, sarà necessario contattare il supporto MPSA per eseguire il provisioning di altri amministratori delle sottoscrizioni di Visual Studio.

Per assistenza o domande, è possibile contattare il supporto tramite telefono o posta elettronica.

Supporto MPSA: **1-866-200-9611**, disponibile dal lunedì al venerdì dalle 5:30 alle 17:30 (Ora del Pacifico)

Posta elettronica: ngvlsup@microsoft.com
