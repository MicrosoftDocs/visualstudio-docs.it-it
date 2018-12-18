---
title: Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/2/2018
Ms.topic: Get-Started-Article
Description: Sign-in may fail if aliases or friendly names are used.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 8c07bc8d3cf674d86c2152ff80f20e4fac003fc3
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-with-aliases"></a>Possibili errori di accesso alle sottoscrizioni di Visual Studio con alias

A seconda del tipo di account usato per l'accesso, le sottoscrizioni disponibili potrebbero non essere visualizzate correttamente quando si accede a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una delle possibili cause è l'uso di "alias" o "nomi descrittivi" al posto dell'identità di accesso a cui è assegnata la sottoscrizione. Questa situazione viene chiamata "aliasing". 

## <a name="what-is-aliasing"></a>Il termine "aliasing"

indica utenti che usano identità diverse per accedere a Windows (o al servizio Active Directory) e per accedere alla posta elettronica.

L'aliasing può esistere quando un'azienda usa un servizio Microsoft Online per l'accesso alla directory, ad esempio JohnD@contoso.com, ma gli utenti accedono agli account di posta elettronica tramite alias o nomi descrittivi, ad esempio John.Doe@contoso.com.  Per molti clienti che gestiscono le sottoscrizioni tramite Volume Licensing Service Center (VLSC), questo può causare errori durante l'esperienza di accesso perché l'indirizzo di posta elettronica fornito (John.Doe@contoso.com) non corrisponde all'indirizzo della directory (JohnD@contoso.com) richiesto per completare l'autenticazione tramite l'opzione "Account aziendale o dell'istituto di istruzione".

## <a name="as-an-administrator-what-options-do-i-have"></a>Opzioni per l'amministratore

Come amministratore esistono due opzioni per assicurarsi che l'esperienza di accesso dei sottoscrittori a [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) sia positiva. 
1. La prima opzione (scelta consigliata) consiste nell'usare l'account della directory come indirizzo assegnato in Volume Licensing Service Center (VLSC). Fare riferimento alla sezione [Assegnazione dei sottoscrittori a un account della directory](#assigning-subscribers-to-a-directory-account) in questo articolo per altri dettagli.
2. La seconda opzione (meno sicura) prevede di consentire ai sottoscrittori di associare l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione a un account personale (ovvero un account Microsoft o MSA). Fare riferimento alla sezione [Definizione di un account aziendale o dell'istituto di istruzione come account personale](#defining-a-work-or-school-account-as-a-personal-account ) in questo articolo per altri dettagli.

> [!NOTE]
> Dopo il completamento della migrazione dell'azienda al nuovo [portale di gestione](https://manage.visualstudio.com) delle sottoscrizioni di Visual Studio, sarà possibile sfruttare la nuova esperienza di amministrazione che consente di specificare sia indirizzi di posta elettronica della directory che personali come parte del profilo del sottoscrittore.  Altre informazioni sulla [migrazione](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Opzioni per i sottoscrittori

Dal punto di vista dei sottoscrittori, è prima di tutto importante collaborare con l'amministratore per comprendere la configurazione delle identità della società.  Se necessario, l'amministratore potrebbe dover aggiornare le impostazioni dell'account dal portale di amministrazione o potrebbe essere necessario creare un account Microsoft (MSA) usando l'indirizzo di posta elettronica aziendale.  Prima di eseguire i passaggi per creare un account Microsoft, contattare l'amministratore per verificare se esistono criteri o problemi per questa azione.  Fare riferimento alla sezione [Definizione di un account aziendale o dell'istituto di istruzione come account personale](#defining-a-work-or-school-account-as-a-personal-account ) in questo articolo per altri dettagli.  

## <a name="assigning-subscribers-to-a-directory-account"></a>Assegnazione dei sottoscrittori a un account della directory 

In tutti i casi, il gestore delle sottoscrizioni all'interno di Volume Licensing Service Center (VLSC) dovrà usare l'indirizzo della directory per i nuovi sottoscrittori oppure aggiornare l'indirizzo di posta elettronica per i sottoscrittori esistenti.  È importante sottolineare che l'uso dell'indirizzo della directory comporta che i nuovi sottoscrittori non riceveranno un messaggio di posta elettronica di benvenuto e l'amministratore dovrà notificare il sottoscrittore dell'assegnazione di una sottoscrizione.  Dopo avere eseguito la procedura di seguito, è possibile usare il [modello](#notifying-your-subscribers-with-directory-addresses) di messaggio di posta elettronica per informare i sottoscrittori e facilitare il processo di accesso.

### <a name="adding-new-subscribers"></a>Aggiunta di nuovi sottoscrittori
Seguire questa procedura per aggiungere un nuovo sottoscrittore con un account della directory.

1. Visitare [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e accedere.
2. Dalla pagina di amministrazione di VLSC fare clic su **Sottoscrizioni** e quindi su **Sottoscrizioni di Visual Studio**.

    ![Menu Sottoscrizioni](_img//vlsc/vlsc-subscriptions.png)

3. Fare clic sul **numero di contratto** associato alla sottoscrizione di Visual Studio.

    ![Selezionare il contratto](_img/vlsc/vlsc-agreement.png)

4. Fare clic su **Assegna sottoscrizione**.

    ![Assegna sottoscrizione](_img/vlsc/vlsc-assign.png)

5. Selezionare il **livello di sottoscrizione** desiderato.

    ![Livello di sottoscrizione](_img/vlsc/vlsc-subscription-level.png)
    
6. Verificare che siano disponibili sottoscrizioni da assegnare e fare clic su **Avanti**.
7.  Immettere i dettagli del sottoscrittore e l'indirizzo della directory nel campo dell'indirizzo di posta elettronica, quindi fare clic su **Avanti**.

    ![Indirizzo di posta elettronica](_img/vlsc/vlsc-email-address.png)
    
8. Verificare le informazioni del sottoscrizione e fare clic su **Fine**.

9. Inviare notifica al sottoscrittore del provisioning della sottoscrizione usando il [modello](#notifying-your-subscribers-with-directory-addresses) di seguito.

### <a name="updating-an-existing-subscriber"></a>Aggiornamento di un sottoscrittore esistente
Seguire questa procedura per aggiornare un sottoscrittore esistente con un account della directory.

1. Visitare [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e accedere.

2. Dalle pagine di amministrazione di VLSC fare clic su **Sottoscrizioni** e quindi su **Sottoscrizioni di Visual Studio**.

3. Fare clic sul **numero di contratto** associato alla sottoscrizione di Visual Studio.

4. Fare clic sulla **freccia in giù** nella barra di ricerca.

5. Cercare il sottoscrittore usando il campo dell'indirizzo di posta elettronica.

6. Nell'elenco dei risultati fare clic sul **cognome** del sottoscrittore.

7. Fare clic su **Modifica**.

8. Modificare il campo Indirizzo di posta elettronica specificando l'indirizzo della directory desiderato e fare clic su **Salva**.

9. Inviare notifica al sottoscrittore del provisioning della sottoscrizione usando il modello di messaggio di posta elettronica riportato di seguito.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Informare i sottoscrittori degli indirizzi della directory
Dato che il messaggio di posta elettronica di benvenuto non raggiungerà correttamente il sottoscrittore, copiare e incollare il testo seguente in un messaggio di posta elettronica e inviarlo al sottoscrittore. Sostituire %PAROLA% con le informazioni appropriate per ogni sottoscrittore.

----------- Copiare il testo seguente (CTRL+C) -----------

Salve %NOME SOTTOSCRITTORE%

È stata assegnata una sottoscrizione di Visual Studio.  Visitare https://my.visualstudio.com e accedere con l'indirizzo %INDIRIZZO DIRECTORY% per attivare la sottoscrizione e accedervi. 

In caso di problemi, contattare il team di supporto (https://www.visualstudio.com/subscriptions/support/).

Nella parte inferiore della pagina selezionare gli elementi seguenti:
   - Account, sottoscrizioni e supporto di fatturazione
   - Scegliere il supporto per l'accesso alla sottoscrizione come problema
   - Scegliere il paese corretto
   - Selezionare l'opzione di supporto assistito desiderata

----------- Fine copia -----------



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definizione di un account aziendale o dell'istituto di istruzione come account personale 
Riutilizzare le istruzioni riportate nella sezione [Assegnazione dei sottoscrittori a un account della directory](#assigning-subscribers-to-a-directory-account) per aggiungere un nuovo utente o aggiornare l'indirizzo di posta elettronica di un utente in Volume Licensing Service Center (VLSC).  Nei casi in cui l'indirizzo di posta elettronica non è riconosciuto dalla directory, l'utente dovrà eseguire la procedura per creare un nuovo account per definire l'indirizzo di posta elettronica come account personale.  Per un breve periodo, il team delle sottoscrizioni di Visual Studio ha garantito un'esenzione per i criteri di identità definiti di seguito, ma sono in corso attività per sviluppare le funzionalità necessarie per rimuovere il criterio.

> [!WARNING]
> Microsoft non consiglia la combinazione di identità aziendale o dell'istituto di istruzione con identità personale.  Con questa azione, l'organizzazione perde la proprietà e il controllo dell'account e il dipendente può continuare ad accedere a prodotti o servizi specifici anche dopo aver lasciato la società.  Per altre informazioni, fare riferimento a questo [post di blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/) dal team di Microsoft Identity.

### <a name="defining-an-email-address-as-a-personal-account"></a>Definizione di un indirizzo di posta elettronica come account personale
Dopo l'assegnazione di una sottoscrizione al sottoscrittore, quest'ultimo riceverà un messaggio di posta elettronica che richiede d visitare https://my.visualstudio.com per sfruttare i vantaggi della sottoscrizione.  Durante il tentativo di accesso, l'accesso alla sottoscrizione di Visual Studio avrà esito negativo con un errore indicante che l'account non è stato riconosciuto.  Prima di accedere all'esperienza https://my.visualstudio.com, chiedere al sottoscrittore di seguire queste istruzioni.  Se necessario, è possibile usare questo [modello](#notifying-your-subscribers-using-personal-accounts) per inviare notifica al sottoscrittore dopo aver assegnato una sottoscrizione.

1. Passare a https://my.visualstudio.com e fare clic su **Crea un account Microsoft**.

2. Completare i campi:
    - Immettere l'indirizzo di posta elettronica che ha ricevuto il messaggio di benvenuto nella casella Someone@example.com
    - Creare la password
    - Scegliere le impostazioni promozionali
    - Fare clic su **Avanti**.

3. Completare i passaggi di convalida e fare clic su **Avanti**.

4. I nuovi utenti potrebbero dover compilare il profilo di Visual Studio.

5. La sottoscrizione e i vantaggi dovrebbero essere ora visibili.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Informare i sottoscrittori che usano account personali

Nello scenario illustrato in precedenza, il sottoscrittore riceverà un messaggio di posta elettronica di benvenuto, ma a causa dell'aliasing potrebbe risultare impossibile l'accesso.  È possibile usare il testo seguente per informare il sottoscrittore delle istruzioni precedenti e consigliare opzioni di supporto, se necessario.  Sostituire %PAROLA% con le informazioni appropriate per ogni sottoscrittore.

----------- Copiare il testo seguente (CTRL+C) -----------

Salve %NOME SOTTOSCRITTORE%

Ti è stata assegnata una sottoscrizione di Visual Studio ed è possibile che tu abbia ricevuto indicazione di accedere a https://my.visualstudio.com in base al messaggio di posta elettronica di benvenuto.  Anche se questo è il sito Web corretto per usufruire dei vantaggi, l'organizzazione richiede l'esecuzione di alcuni passaggi aggiuntivi prima di poter accedere al sito.  Seguire le istruzioni seguenti per creare un account Microsoft associato all'indirizzo di posta elettronica aziendale.  Dopo aver completato questa procedura, sarà possibile usare l'indirizzo di posta elettronica per accedere ai vantaggi della sottoscrizione.
1. Visitare https://my.visualstudio.com

2. Fare clic su Crea un account Microsoft sul lato destro

3. Compilare il modulo: 
    - Usare l'indirizzo di posta elettronica aziendale nella casella someone@example.com
    - Immettere una password
    - Selezionare la preferenza per le promozioni
    - Fare clic su Avanti

4. Completare i passaggi di convalida dell'account

5. Se necessario, completare il profilo di Visual Studio

6. I vantaggi dovrebbero essere ora visibili

Nota: in occasione delle visite future di https://my.visualstudio.com, potrebbe essere richiesto di selezionare l'account che si vuole usare (ad esempio "Account aziendale o dell'istituto di istruzione" o "Account personale").  Dopo aver completato i passaggi precedenti, sarà necessario usare l'opzione "Account personale".

In caso di problemi, contattare il team di supporto (https://www.visualstudio.com/subscriptions/support/).

Nella parte inferiore della pagina selezionare gli elementi seguenti:
   - Account, sottoscrizioni e supporto di fatturazione
   - Scegliere il supporto per l'accesso alla sottoscrizione come problema
   - Scegliere il paese corretto
   - Selezionare l'opzione di supporto assistito desiderata

----------- Fine copia -----------