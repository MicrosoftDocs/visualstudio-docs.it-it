---
title: Assegnare licenze alle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Informazioni su come gli amministratori possono assegnare licenze ai sottoscrittori
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: b035f748f6d99595bc2570b54a4d6413cab72af5
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Assegnazione di licenze nel portale di amministrazione delle sottoscrizioni di Visual Studio

Come amministratore di sottoscrizioni di Visual Studio, è possibile usare il portale per gli amministratori delle sottoscrizioni di Visual Studio per assegnare le sottoscrizioni a singoli utenti.  
È possibile assegnare le sottoscrizioni una alla volta oppure usare la funzionalità di aggiunta in blocco per caricare elenchi di sottoscrittori con le relative informazioni di sottoscrizione in modo semplice e rapido. 

## <a name="assigning-a-single-user"></a>Assegnazione di un singolo utente
Se sono disponibili licenze per le sottoscrizioni di Visual Studio, è possibile assegnare queste licenze a nuovi utenti per consentire loro di accedere ai vantaggi delle sottoscrizioni. 
1.  Accedere al [portale per gli amministratori](https://manage.visualstudio.com)

2.  Per assegnare un singolo sottoscrittore di Visual Studio, nella parte superiore della tabella, fare clic su **Aggiungi**.

    ![Aggiungi sottoscrittore](_img\assign-license-add\assign-license-add.png)

3.  Immettere le informazioni nei campi del modulo per il nuovo sottoscrittore. Se l'organizzazione usa Azure Active Directory, questo campo funge da funzione di ricerca per trovare i contatti nella directory corrente per poter selezionare l'utente corretto nei risultati della ricerca. Una volta selezionata la persona, vengono compilati automaticamente i campi relativi a nome, indirizzo di posta elettronica di accesso e per le notifiche, come visualizzato di seguito. 

    Se l'organizzazione ha un indirizzo di posta elettronica diverso per ricevere gli email rispetto a quello da utilizzare per l'accesso, l'utente ha la possibilità di indicarlo qui. Selezionare il collegamento ipertestuale che indica "L'indirizzo di posta elettronica per le comunicazioni è diverso da quello per l'accesso?". 

    Se si vuole che il sottoscrittore possa accedere ai download software quando accede al [portale delle sottoscrizioni di Visual Studio](https:/my.visualstudio.com?wt.mc_id=o~msft~docs), assicurarsi di lasciare selezionata la casella di controllo Download. Se si sceglie di deselezionare questa casella, l'utente non avrà accesso ai download del software, ma potrà comunque accedere a tutti gli altri vantaggi inclusi nella sottoscrizione. Al termine, fare clic su **Aggiungi**.

    ![Immettere le informazioni sul sottoscrittore](_img\assign-license-add\add-subscriber-1.png)

    ![Immettere le informazioni sul sottoscrittore](_img\assign-license-add\add-subscriber-2.png)

4.  Dopo aver aggiunto il sottoscrittore, viene inviato automaticamente al nuovo sottoscrittore un messaggio di posta elettronica di assegnazione, con altre istruzioni. È possibile inviare nuovamente il messaggio di posta elettronica di assegnazione in qualunque momento selezionando il sottoscrittore e facendo clic sul pulsante **Invia di nuovo** nel menu superiore.

    ![Sottoscrittore aggiunto](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Assegnazioni in blocco
1.  Per aggiungere contemporaneamente più sottoscrittori, passare alla scheda **Sottoscrittori**. Nella barra multifunzione in alto, fare clic su **Aggiungi in blocco**. 

    ![Aggiungi in blocco](_img\assign-license-add\bulk-assign-add.png)

2. L'assegnazione in blocco usa un modello di Microsoft Excel per caricare i sottoscrittori. Nella finestra di dialogo Upload Multiple Subscriber (Carica più sottoscrittori), fare clic su **Download** per scaricare il modello. Scaricare sempre la versione più recente del modello. Se si usa una versione precedente, il caricamento in blocco potrebbe non riuscire.

    ![Carica più sottoscrittori](_img\assign-license-add\bulk-assign-upload.png)

3.  Nel foglio di calcolo Excel, compilare i campi con le informazioni per gli utenti a cui si desidera assegnare le sottoscrizioni. Il riferimento è un campo facoltativo. Se una parte del modello è stata compilata in modo errato, si dovrebbe visualizzare un messaggio di errore che descrive il problema. Salvare il file sul disco rigido al termine dell'operazione.
**Per garantire un caricamento senza errori, osservare le procedure consigliate seguenti:**
    - Verificare che nessuno dei campi modulo contenga virgole.
    - Rimuovere gli spazi prima e dopo i campi del modulo, ad esempio i nomi degli utenti.
    - Assicurarsi che i nomi degli utenti non contengano spazi aggiuntivi tra i nomi e cognomi composti da due parti (ad esempio il nome composto "Maria Giovanna" non deve essere digitato come "Maria  Giovanna" perché il sistema non annullerà lo spazio aggiuntivo)

    ![Modello di aggiunta in blocco](_img\assign-license-add\bulk-template.png)

4.  Tornare al portale di amministrazione delle sottoscrizioni di Visual Studio e nella finestra di dialogo Upload Multiple Subscribers (Carica più sottoscrittori), fare clic su **Sfoglia**. Andare al file di Excel salvato e fare clic su **OK**. Lo stato di avanzamento del caricamento verrà visualizzato sullo schermo. 

    ![Caricamento di utenti in blocco](_img\assign-license-add\bulk-assign-upload-2.png)

Se il modello contiene errori, il caricamento avrà esito negativo e verranno visualizzati gli errori in modo da poter correggere il modello e tentare nuovamente il caricamento in blocco.

   ![Caricamento non riuscito](_img\assign-license-add\bulk-assign-upload-fail.png)

Quando il caricamento ha esito positivo, viene visualizzato l'elenco di sottoscrittori e un messaggio di conferma.

   ![Caricamento completato](_img\assign-license-add\bulk-assign-upload-complete.png)