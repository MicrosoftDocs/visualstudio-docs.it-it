---
title: Gestire più account utente
description: Informazioni su come aggiungere tutti gli account Microsoft a Visual Studio in modo che sia possibile accedere alle risorse da qualsiasi account senza dover accedere separatamente.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 689b1fb47c137059f3aef7b7a20fd614a9058ec4
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296027"
---
# <a name="work-with-multiple-user-accounts"></a>Gestire più account utente

Se si dispone di più account Microsoft e/o di account aziendali o dell’istituto di istruzione è possibile aggiungerli tutti a Visual Studio in modo che le risorse di tutti gli account siano accessibili Da tutti gli account senza dover autenticarsi separatamente. Azure, Application Insights, Azure DevOps e i servizi Microsoft 365 supportano tutti l'esperienza di accesso semplificata.

Dopo aver aggiunto più account in un computer, tale set di account effettua il roaming insieme all'utente se quest'ultimo accede a Visual Studio in un altro computer.

> [!NOTE]
> Viene effettuato il roaming dei nomi account e non delle credenziali. Verrà quindi richiesto di immettere le credenziali degli altri account la prima volta che si tenta di usare le rispettive risorse in un nuovo computer.

Questo articolo illustra come aggiungere più account a Visual Studio. Spiega anche come visualizzare le risorse accessibili da tali account da alcune posizioni, come ad esempio dalla finestra di dialogo **Aggiungi servizio connesso**, da **Esplora server** e **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Accedi a Visual Studio

Accedere a Visual Studio con un account Microsoft o un account aziendale. Il nome utente dovrebbe essere visualizzato nell'angolo superiore della finestra, come illustrato nella figura seguente:

![Utente attualmente connesso](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Accedere all'account Azure in Esplora server

Per aprire Esplora server, scegliere **Visualizza**  >  **Esplora server** (o, se si usano le [impostazioni di ambiente](../ide/environment-settings.md)"generale", premere **CTRL** + **ALT** + **S**). Espandere il nodo **Azure**. Si noti che contiene le risorse disponibili nell'account Azure associato all'account usato per accedere a Visual Studio. È simile alla figura riportata di seguito:

![Nodo Azure espanso in Esplora server](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

La prima volta che si usa Visual Studio in un qualsiasi dispositivo specifico, la finestra di dialogo visualizza solo le sottoscrizioni registrate con l'account con il quale è stato eseguito accesso. Per poter accedere a tutte le risorse degli altri account direttamente da **Esplora server**, fare clic con il pulsante destro del mouse sul nodo **Azure**, scegliere **Gestisci e filtra sottoscrizioni** e aggiungere gli account dal controllo selezione account. È possibile scegliere un altro account, se necessario, facendo clic sulla freccia giù, sceglierlo dall'elenco di account collegati. Dopo aver scelto l'account, è possibile personalizzare le sottoscrizioni di tale account che devono essere visualizzate in **Esplora server**.

![Finestra di dialogo Gestisci sottoscrizioni Microsoft Azure](../ide/media/vs2015_manage_subs.png)

Alla successiva apertura di **Esplora server** verranno visualizzate le risorse di tale sottoscrizione.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Accedere all'account Azure tramite la finestra di dialogo Aggiungi servizio connesso

1. Aprire un progetto esistente o crearne un nuovo.

1. Scegliere il nodo del progetto in **Esplora soluzioni**, quindi fare clic con il pulsante destro del mouse su **Aggiungi** > **Servizio connesso**.

   Sarà visualizzata la procedura guidata **Aggiungi servizio connesso** con l'elenco dei servizi dell'account Azure associato all'account di accesso di personalizzazione di Visual Studio. Non è necessario accedere separatamente ad Azure. Tuttavia, è necessario accedere ad altri account la prima volta che si tenta di accedere alle rispettive risorse da un computer diverso.

### <a name="access-azure-active-directory-in-a-web-project"></a>Accedere ad Azure Active Directory in un progetto Web

In Azure Active Directory (AAD) viene abilitato il supporto per l'autenticazione Single Sign-On per utenti finali in app Web MVC ASP.NET o per il servizio Autenticazione di Azure AD in servizi Web API. L'autenticazione di dominio è diversa dall'autenticazione dei singoli account utente. Gli utenti che hanno accesso al dominio di Active Directory possono usare i propri account AAD esistenti per connettersi alle applicazioni Web. Microsoft 365 app possono anche usare l'autenticazione del dominio.

::: moniker range="vs-2017"

Per vedere come funziona, creare un nuovo progetto **Applicazione Web ASP.NET Core**. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** scegliere il modello **Applicazione Web** e quindi scegliere **Modifica autenticazione**.

::: moniker-end

::: moniker range=">=vs-2019"

Per verificarlo, creare un nuovo progetto di **app Web ASP.NET Core** . Nella pagina **Crea una nuova applicazione Web ASP.NET Core** scegliere **ASP.NET Core 3,1** dall'elenco a discesa, scegliere il modello **applicazione Web** e quindi scegliere **modifica** in **autenticazione**.

::: moniker-end

Verrà visualizzata la finestra di dialogo **Modifica autenticazione** in cui è possibile scegliere il tipo di autenticazione da usare nell'applicazione.

![Finestra di dialogo Modifica autenticazione per ASP.NET](../ide/media/vs2015_change_authentication.png)

Per altre informazioni sui diversi tipi di autenticazione in ASP.NET, vedere [Creare progetti Web ASP.NET in Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Accedere all'organizzazione di Azure DevOps

Dal menu principale scegliere **Team**  >  **Manage Connections** per aprire la finestra **Team Explorer-Connect** . Scegliere **Gestisci connessioni**  >  **Connetti a un progetto**. Nella finestra di dialogo **Connetti a un progetto** selezionare un progetto dall'elenco (oppure selezionare **Aggiungi server TFS** e immettere l'URL del server). Selezionando l'URL, l'utente esegue l'accesso senza dover immettere nuovamente le credenziali.

Per altre informazioni, vedere [Connettersi a progetti in Team Explorer](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Aggiungere un altro account a Visual Studio

Per aggiungere un altro account a Visual Studio:

1. Scegliere   >  **Impostazioni account** file.

1. In **Tutti gli account** scegliere **Aggiungi un account**.

1. Nella pagina **Accesso all'account** selezionare l'account o scegliere **Usa un altro account**. Seguire i prompt visualizzati per immettere le credenziali del nuovo account.

(Facoltativo) A questo punto è possibile passare a **Esplora server** e visualizzare i servizi di Azure associati all'account appena aggiunto. In **Esplora server** fare clic con il pulsante destro del mouse sul nodo **Azure** e scegliere **Gestisci e filtra sottoscrizioni**. Scegliere il nuovo account facendo clic sulla freccia a discesa vicino all'account corrente, quindi scegliere le sottoscrizioni da visualizzare in **Esplora server**. Verranno visualizzati tutti i servizi associati alla sottoscrizione specificata. Ci si connette ai servizi e alle risorse del secondo account, anche se non si è attualmente connessi a Visual Studio con tale account. Lo stesso vale per l'   >  **aggiunta del servizio connesso** al progetto e la connessione del **Team**  >  **a Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Aggiungere un account usando il flusso del codice del dispositivo

In alcuni casi non è possibile eseguire l'accesso o aggiungere un account in modo normale, ad esempio se Internet Explorer è per qualche motivo bloccato o se la rete è protetta da firewall. In questi casi, come soluzione alternativa, è possibile abilitare il *flusso del codice del dispositivo* per aggiungere un account o ripetere l'autenticazione dell'account. Il flusso del codice del dispositivo consente di accedere usando un browser diverso o di accedere a un computer diverso, fisico o virtuale (VM).

Per eseguire l'accesso tramite il flusso del codice del dispositivo:

1. Aprire la pagina [**Account**](reference/accounts-environment-options-dialog-box.md) in **Strumenti** > **Opzioni** > **Ambiente** e selezionare **Abilita il flusso del codice del dispositivo durante l'aggiunta o la riautenticazione di un account**. Scegliere **OK** per chiudere le pagine delle opzioni.

1. Scegliere **file**  >  **Impostazioni account** per aprire la pagina Gestione account.

1. In **Tutti gli account** scegliere **Aggiungi un account**.

   In una finestra di dialogo vengono visualizzati un URL e un codice da incollare in un Web browser.

   ![URL e codice del flusso del codice del dispositivo](media/work-with-multiple-user-accounts/device-login-code.png)

1. Premere **CTRL** + **C** per copiare il testo della finestra di dialogo, quindi scegliere **OK** per chiudere la finestra di dialogo. Incollare il testo copiato in un editor di testo, ad esempio Blocco note. In questo modo sarà più semplice copiare il codice nel passaggio successivo.

1. Passare all'URL di accesso dispositivo nel computer o nel Web browser da usare per accedere a Visual Studio, quindi incollare o immettere il codice copiato nella casella **Codice**.

   Il nome dell'app **Visual Studio** sarà visualizzato nella parte inferiore della pagina.

1. In **Visual Studio** scegliere **Continua**.

   ![Screenshot della pagina di accesso del dispositivo che mostra l'opzione continua.](media/work-with-multiple-user-accounts/device-login-page.png)

1. Seguire i prompt per immettere le credenziali dell'account.

   La pagina visualizzata informerà che è stato eseguito l'accesso a Visual Studio nel dispositivo e che è possibile chiudere la finestra del browser.

   ![Accesso a Visual Studio tramite browser completato](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Tornare alla pagina di gestione account in Visual Studio. Si noterà che l'account appena aggiunto è elencato in **Tutti gli account**. Scegliere **Chiudi**.

::: moniker range=">=vs-2019"

### <a name="add-a-github-account-to-visual-studio"></a>Aggiungere un account GitHub a Visual Studio

A partire dalla versione 16,8, sarà possibile aggiungere gli account GitHub e GitHub Enterprise al keychain. Potrai aggiungerli e usarli come con gli account Microsoft, il che significa che avrai a disposizione un momento più semplice per accedere alle risorse di GitHub in Visual Studio.

Per istruzioni dettagliate, vedere [usare gli account github in Visual Studio](work-with-github-accounts.md).
::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
- [Accesso a Visual Studio per Mac](/visualstudio/mac/signing-in)
