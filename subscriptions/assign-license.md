---
title: Assegnare le sottoscrizioni di Visual Studio agli utenti | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/21/2021
ms.topic: conceptual
description: Informazioni su come gli amministratori possono assegnare le licenze ai sottoscrittori
ms.openlocfilehash: a1b68a45754e0fb466ae12b59d63fa14d50e9a3e
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776519"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio
In qualità di amministratore delle sottoscrizioni di Visual Studio, è possibile usare il portale di amministrazione per assegnare le sottoscrizioni a singoli utenti e gruppi di utenti.

Per i gruppi di utenti, è possibile scegliere la modalità di assegnazione delle sottoscrizioni.  
- È possibile assegnare le sottoscrizioni una alla volta.
- È anche possibile caricare in modo rapido e semplice elenchi di sottoscrittori e le relative informazioni di sottoscrizione usando la funzionalità di [aggiunta in blocco](assign-license-bulk.md) .
- Se l'organizzazione utilizza Microsoft Azure Active Directory (Azure AD), è possibile [utilizzare Azure ad gruppi per assegnare le sottoscrizioni](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) a gruppi di utenti.  


## <a name="add-a-single-subscriber"></a>Aggiungere un singolo sottoscrittore
Guardare il video o leggere per informazioni su come assegnare una sottoscrizione di Visual Studio a un nuovo utente in modo da poter accedere ai vantaggi della sottoscrizione.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Accedere al portale di [Amministrazione](https://manage.visualstudio.com).
2. Per assegnare una licenza a un singolo Sottoscrittore di Visual Studio, nella parte superiore della tabella selezionare **Aggiungi**, quindi scegliere **singolo Sottoscrittore**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere un singolo sottoscrittore](_img/assign-license-add/add-subscriber-individual.png "Selezionare Aggiungi, quindi scegliere singolo Sottoscrittore per assegnare una singola sottoscrizione.")
3. Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, il campo **Nome** funge da funzione di ricerca per trovare le persone nella directory corrente, in modo da selezionare l'utente corretto nei risultati della ricerca. Dopo aver selezionato la persona, vengono inseriti automaticamente il nome, l'indirizzo di posta elettronica di accesso e l'indirizzo di posta elettronica di notifica.  Se il Sottoscrittore non viene trovato nell'organizzazione, il messaggio di posta elettronica di notifica non verrà popolato automaticamente, ma sarà disponibile per l'aggiunta manuale di un indirizzo di posta elettronica diverso a cui verranno inviati i messaggi di posta elettronica relativi alla sottoscrizione.  Se il servizio di posta elettronica blocca i messaggi di posta elettronica in arrivo per gli indirizzi di posta elettronica di accesso, è importante specificare un indirizzo di posta elettronica di notifica diverso, in modo che i sottoscrittori e gli amministratori ricevano importanti messaggi di posta elettronica correlati alle sottoscrizioni
   > [!div class="mx-imgBorder"]
   > ![Dettagli sul sottoscrittore](_img/assign-license-add/subscriber-details.png "Immettere il nome del Sottoscrittore e altri dettagli oppure scegliere tra i membri del tenant.")

    > [!NOTE]
    > Affinché i membri di un tenant di Azure Active Directory siano visibili quando si immette un nome di Sottoscrittore, l'amministratore deve essere un membro del tenant. 


    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di attivazione/disattivazione dei download nella sezione delle **impostazioni di download**. Se si sceglie di disabilitare i download, l'utente non avrà accesso ai download del software.  Anche l'accesso ai codici Product Key verrà disabilitato.  Il Sottoscrittore avrà comunque accesso a tutti gli altri vantaggi inclusi nella sottoscrizione.
   > [!div class="mx-imgBorder"]
   > ![Accedere ai download](media/access-to-downloads.png "Scegliere "Consenti" per fornire al Sottoscrittore l'accesso ai download del software.")

    Se si vuole aggiungere le proprie note di riferimento alla sottoscrizione, è possibile aggiungerle nella sezione **Aggiungi riferimento**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere le proprie note di riferimento a ogni sottoscrizione](media/add-subscriber-reference-notes.png "Usare il campo riferimento per registrare eventuali note relative a questa sottoscrizione.")

    Dopo aver selezionato le opzioni e aver immesso i dati per il sottoscrittore, scegliere **Aggiungi** nella parte inferiore di **Aggiungi sottoscrittore**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere il pulsante Aggiungi](media/add-button.png "Selezionare Aggiungi per salvare le informazioni e assegnare la sottoscrizione al Sottoscrittore.")

## <a name="why-use-a-different-notification-email-address"></a>Perché usare un indirizzo di posta elettronica di notifica diverso?
Alcune organizzazioni configurano i servizi di posta elettronica per bloccare i messaggi di posta elettronica in arrivo da altri domini.  Il blocco di messaggi di posta elettronica in arrivo significa che i sottoscrittori e gli amministratori non hanno importanti comunicazioni:
- I Sottoscrittori non riceveranno una notifica a cui è stata assegnata una sottoscrizione.  In questo modo si impedirà anche di attivare alcuni dei vantaggi inclusi.  
- Gli abbonati a cui sono state assegnate sottoscrizioni di Visual Studio con GitHub Enterprise non riceveranno l'invito a partecipare all'organizzazione GitHub, ovvero non saranno in grado di accettare l'invito. **Devono accettare l'invito tramite posta elettronica** per ottenere l'accesso all'organizzazione github. 
- Gli amministratori non riceveranno alcuna notifica quando vengono aggiunti a un contratto, ricevono istruzioni amministrative mensili o notifiche delle modifiche delle funzionalità che influiscono sul modo in cui gestiscono le sottoscrizioni.

L'uso di un indirizzo di posta elettronica di notifica consente di consentire ai sottoscrittori di ricevere comunicazioni importanti sulle sottoscrizioni senza modificare la funzionalità degli indirizzi di posta elettronica di accesso.  

## <a name="resend-assignment-emails"></a>Invia nuovamente i messaggi di posta elettronica di assegnazione
Dopo l'aggiunta di un Sottoscrittore, un messaggio di posta elettronica di assegnazione verrà inviato automaticamente al nuovo Sottoscrittore con ulteriori istruzioni. È possibile inviare di nuovo il messaggio di posta elettronica di assegnazione in qualsiasi momento selezionando il Sottoscrittore e quindi selezionando il pulsante **Invia** di nuovo nel menu in alto.  Per inviare di nuovo i messaggi di posta elettronica a più utenti, tenere premuto il tasto **CTRL** mentre si selezionano i sottoscrittori.  Quando si seleziona il pulsante **Invia** di nuovo, viene visualizzata una finestra di dialogo in cui viene chiesto di confermare che si desidera inviare nuovamente a tali Sottoscrittori.  


## <a name="resources"></a>Risorse
- Serve aiuto?  Contattare il [supporto delle sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario aggiungere molti utenti,  vedere le informazioni su come assegnare sottoscrizioni a [più sottoscrittori](assign-license-bulk.md).
