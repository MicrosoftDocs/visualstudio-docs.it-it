---
title: Gestione dei diritti di amministratore nel portale di amministrazione delle sottoscrizioni di Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Gestione dei diritti di amministratore nel portale di amministrazione delle sottoscrizioni di Visual Studio

## <a name="overview"></a>Panoramica 
Nel portale di gestione delle sottoscrizioni di Visual Studio (https://manage.visualstudio.com), sono disponibili due ruoli di gestione:

**Amministratori con privilegi elevati:** durante la prima configurazione di un'organizzazione, il contatto principale o per le comunicazioni diventa amministratore con privilegi elevati per impostazione predefinita. Il contatto principale o per le comunicazioni può scegliere di assegnare altri amministratori con privilegi elevati o amministratori. Oltre a gestire le sottoscrizioni per i singoli sottoscrittori, gli amministratori con privilegi elevati possono aggiungere e rimuovere altri amministratori e amministratori con privilegi elevati. Se nel sistema sono presenti più di due amministratori con privilegi elevati, è possibile eliminarli tutti tranne gli ultimi due per motivi di sicurezza. 

**Amministratori:** un amministratore può gestire i sottoscrittori nei contratti assegnati loro dall'amministratore con privilegi elevati.  Possono assegnare le sottoscrizioni a singoli utenti, modificare le sottoscrizioni e riassegnarle o rimuoverle.   (Gli amministratori vengono designati dagli amministratori con privilegi elevati.)  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Aggiunta di un amministratore **con** diritti di amministratore con privilegi elevati:

1. Accedere al [portale di amministrazione](https://manage.visualstudio.com) delle sottoscrizioni di Visual Studio con un account che dispone già di diritti di amministratore con privilegi elevati.

2. Fare clic sulla scheda **Gestisci amministratori** nella parte superiore della pagina. (Solo gli amministratori con privilegi elevati hanno accesso a questa scheda.  Gli amministratori senza i diritti di amministratore con privilegi elevati usano la scheda **Gestisci sottoscrittori** per gestire i singoli sottoscrittori.)

3. Fare clic su **Aggiungi** per creare un nuovo amministratore. 

4. Compilare tutti i dettagli richiesti nella finestra popup Aggiungi amministratore.
  - Se l'organizzazione è già registrata in Azure Active Directory (AAD), iniziare a digitare il nome nel campo **Nome** e selezionare l'elemento corretto nell'elenco a discesa. Con i nuovi utenti, digitare il nome completo e ignorare la notifica *Non sono state trovate identità*.
  - Dopo aver individuato l'utente corretto, il campo Indirizzo di posta elettronica di accesso verrà popolato automaticamente. Digitare l'indirizzo di posta elettronica del nuovo amministratore, se non è già specificato.

5. Selezionare il **PCN** che deve gestire il nuovo amministratore, facendo clic sull'elenco a discesa in **Contratti**. Se il PCN di cui si sta eseguendo l'onboarding include più contratti, è possibile consentire all'amministratore l'accesso a uno o a tutti i contratti. 

**Altre informazioni sul contratti:** l'elenco a discesa in Contratti è disabilitato se è disponibile un solo contratto.  Tutti i contratti vengono controllati automaticamente quando all'utente configurato vengono concessi i diritti di amministratore con privilegi elevati.

6. Fare clic sulla casella **Amministratore con privilegi elevati** per abilitare i diritti di amministratore con privilegi elevati per l'amministratore.  

7. Per completare l'aggiunta di questo amministratore, fare clic su **Aggiungi**.

**Potenziali errori ricevuti durante l'aggiunta di amministratori:** alcuni utenti potrebbero ricevere un messaggio di errore durante il tentativo di aggiungere l'amministratore. È probabile che ciò si verifichi se l'indirizzo di posta elettronica dell'amministratore con privilegi elevati da aggiungere non è elencato in AAD per la società. Per completare l'aggiunta del nuovo amministratore, è sufficiente ignorare l'errore e fare di nuovo clic su **Aggiungi**. 

8. Dopo aver creato un amministratore con privilegi elevati, esso comparirà nell'elenco degli amministratori e il relativo account verrà contrassegnato con segno di spunta verde per indicare lo stato di amministratore con privilegi elevati. 

### <a name="optional--add-a-different-notification-email"></a>Facoltativo: aggiungere un indirizzo di posta elettronica diverso per le notifiche.
Se l'organizzazione usa un indirizzo o account diverso per la ricezione dei messaggi di posta elettronica, è ora disponibile un'opzione per immettere un indirizzo "Comunicazione". Selezionare **Add a different notification email for receiving communication** (Aggiungi un indirizzo di posta elettronica di notifica diverso per la ricezione delle comunicazioni). 

*Esempio:* Rene usa l'indirizzo rene@contoso.com per l'accesso con le credenziali aziendali.  La società di Rene, tuttavia, usa questo indirizzo solo per gestire l'accesso alla directory.  Per l'invio e la ricezione di messaggi di posta elettronica, Rene usa rene.collado@contoso.com, pertanto il suo amministratore con privilegi elevati ha immesso un secondo indirizzo per assicurarsi che riceva i messaggi di posta elettronica di benvenuto.  Se la società non è configurata in questo modo, dovrebbe essere sufficiente immettere l'indirizzo di posta elettronica di accesso.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Aggiunta di un amministratore **senza** diritti di amministratore con privilegi elevati:

È possibile eseguire la stessa procedura descritta in precedenza per aggiungere amministratori senza diritti di amministratore con privilegi elevati, ma tenendo conto degli aspetti seguenti:
-  Quando si aggiungono amministratori senza diritti di amministratore con privilegi elevati, non è necessario aggiungere un ulteriore indirizzo di posta elettronica e la casella di controllo dell'amministratore con privilegi elevati rimane deselezionata.
-  Per gli utenti senza diritti di amministratore con privilegi elevati non viene visualizzata l'icona di segno di spunta verde nella voce di configurazione de profilo corrispondente in "Gestisci amministratori".
