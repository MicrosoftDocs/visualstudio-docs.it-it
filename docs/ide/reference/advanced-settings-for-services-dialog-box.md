---
title: Finestra di dialogo Impostazioni avanzate per i servizi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51d3b8b8353bae0b4c0d308150a8834a27848d51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-settings-for-services-dialog-box"></a>Finestra di dialogo Impostazioni avanzate per i servizi
I servizi delle applicazioni client offrono accesso semplificato a servizi di accesso, ruolo e profilo di [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] da applicazioni Windows Forms e Windows Presentation Foundation (WPF). Per configurare i servizi delle applicazioni client, è possibile usare la pagina **Servizi** in **Creazione progetti**. Per altre informazioni sulla pagina **Servizi**, vedere [Services Page, Project Designer](../../ide/reference/services-page-project-designer.md) (Pagina Servizi, Creazione progetti).  
  
 Per configurare le impostazioni avanzate dei servizi delle applicazioni client, usare la finestra di dialogo **Impostazioni avanzate per i servizi**  della pagina **Servizi** in **Creazione progetti**. Queste impostazioni consentono di eseguire l'override di alcuni comportamenti predefiniti di servizi di applicazioni e abilitare scenari meno comuni. Per altre informazioni, vedere [Servizi applicazioni client](/dotnet/framework/common-client-technologies/client-application-services).  
  
 Per accedere alla finestra di dialogo **Impostazioni avanzate per i servizi**, selezionare un nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** dal menu **Progetto**. Quando **Progettazione progetti** si apre, fare clic sulla scheda **Servizi** e premere il **Avanzate**. Questo pulsante rimarrà disabilitato fino all'abilitazione dei servizi delle applicazioni client.  
  
## <a name="task-list"></a>Elenco attività

- [Procedura: configurare i servizi delle applicazioni client](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Elenco UIElement

 **Salva hash della password localmente per consentire l'accesso offline**  
 Specifica se un modulo crittografato della password dell'utente sarà memorizzato nella cache locale per consentire all'utente di accedere quando l'applicazione è in modalità offline. Questa opzione è selezionata per impostazione predefinita.
  
 **Richiedi agli utenti di accedere di nuovo a ogni scadenza del cookie del server**  
 Specifica se gli utenti precedentemente autenticati vengono automaticamente riautenticati quando l'applicazione accede al servizio ruoli o profili e il cookie di autenticazione server è scaduto. Selezionare questa opzione per negare l'accesso ai servizi dell'applicazione e richiedere esplicitamente una nuova autenticazione se il cookie è scaduto. Questa opzione è utile per applicazioni distribuite in percorsi pubblici al fine di garantire che gli utenti che escono dall'applicazione non rimangano autenticati a tempo indeterminato mentre questa continua a essere eseguita. Per impostazione predefinita, questa opzione è deselezionata.  
  
 **Timeout cache servizio ruolo**  
 Specifica il tempo che il provider dei ruoli client userà per i valori del ruolo memorizzati nella cache anziché accedere al servizio ruoli. Impostare questo intervallo di tempo su un valore basso quando i ruoli vengono aggiornati di frequente o su un valore più alto quando i ruoli vengono aggiornati di rado. Il valore predefinito è un giorno.  
  
 Il provider di ruoli accede ai valori del ruolo memorizzati nella cache o al servizio dei ruoli quando si chiama il metodo <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Per cancellare la cache a livello di codice e forzare l'accesso di questo metodo al servizio remoto, chiamare il metodo <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Usa stringa di connessione personalizzata**  
 Specifica se i provider di servizi client useranno un archivio dati personalizzato per la cache locale. Per impostazione predefinita, i provider di servizi useranno il file system locale per la cache. Se si seleziona questa opzione, la casella di testo sarà automaticamente popolata con una stringa di connessione predefinita. È possibile mantenere la stringa di connessione predefinita per generare automaticamente e usare un database SQL Server Compact Edition oppure è possibile specificare una stringa di connessione a un database SQL Server esistente. Per altre informazioni, vedere [Procedura: Configurare i servizi delle applicazioni client](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Per impostazione predefinita, questa opzione è deselezionata.  
  
## <a name="see-also"></a>Vedere anche

[Servizi applicazioni client](/dotnet/framework/common-client-technologies/client-application-services)  
[Pagina Servizi, Creazione progetti](../../ide/reference/services-page-project-designer.md)  
[Procedura: Configurare i servizi delle applicazioni client](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)