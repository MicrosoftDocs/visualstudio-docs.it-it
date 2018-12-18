---
title: Pagina Servizi, Creazione progetti | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f37d6b448ea7ce3a8662d0372cf61b35363f4648
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="services-page-project-designer"></a>Pagina Servizi, Progettazione progetti

I servizi delle applicazioni client consentono l'accesso semplificato ai servizi di accesso, ruolo e profilo di [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] da applicazioni di Windows Forms e Windows Presentation Foundation (WPF). È possibile usare la pagina **Servizi** di **Creazione progetti** per abilitare e configurare i servizi delle applicazioni client per il progetto.

Con i servizi delle applicazioni client è possibile usare un server centralizzato per autenticare gli utenti, determinare il ruolo o i ruoli assegnati a ogni utente e archiviare le impostazioni dell'applicazione per utente che possono essere condivise all'interno della rete. Per altre informazioni, vedere [Servizi applicazioni client](/dotnet/framework/common-client-technologies/client-application-services).

Per accedere alla pagina **Servizi**, selezionare un nodo di progetto in **Esplora soluzioni** e quindi fare clic su **Proprietà** nel menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Servizi**.

## <a name="task-list"></a>Elenco attività

[Procedura: configurare i servizi delle applicazioni client](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)  
  
## <a name="uielement-list"></a>Elenco UIElement

 **Configurazione**  
 Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Piattaforma**  
 Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Attiva servizi applicazione client**  
 Selezionare questa opzione per attivare i servizi dell'applicazione client. Per usare i servizi dell'applicazione client è necessario specificare i percorsi dei servizi nella pagina **Servizi**.  
  
 **Usa autenticazione di Windows**  
 Indica che il provider di autenticazione userà l'autenticazione basata su Windows, ovvero l'identità fornita dal sistema operativo Windows.  
  
 **Usa autenticazione basata su form**  
 Indica che il provider di autenticazione userà l'autenticazione basata su form. L'applicazione quindi deve fornire un'interfaccia utente per l'accesso. Per altre informazioni, vedere [Procedura: implementare l'accesso utente con i servizi dell'applicazione client](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).  
  
 **Percorso servizio di autenticazione**  
 Solo con l'autenticazione basata su form. Specifica il percorso del servizio di autenticazione.  
  
 **Facoltativo: provider di credenziali**  
 Solo con l'autenticazione basata su form. Indica l'implementazione <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> che il servizio di autenticazione userà per visualizzare una finestra di dialogo di accesso quando l'applicazione chiama il metodo `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> e passa stringhe vuote o `null` per i parametri. Se si lascia questa casella vuota, è necessario passare un nome utente valido e una password al metodo <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. È necessario specificare il provider di credenziali come nome di tipo completo dell'assembly. Per altre informazioni, vedere <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> e [Nomi degli assembly](/dotnet/framework/app-domains/assembly-names). Nella sua forma più semplice, un nome di tipo qualificato dall'assembly è simile all'esempio seguente: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Percorso servizi ruoli**  
 Specifica il percorso del servizio ruoli.  
  
 **Percorso servizi impostazioni Web**  
 Specifica il percorso del servizio profili (impostazioni Web).  
  
 **Avanzate**  
 Apre la [finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md), che è possibile usare per eseguire l'override del comportamento predefinito. Ad esempio, è possibile usare questa finestra di dialogo per specificare un database per l'archiviazione offline anziché usare il file system locale. Per altre informazioni, vedere [Finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche

[Servizi applicazioni client](/dotnet/framework/common-client-technologies/client-application-services)   
[Finestra di dialogo Impostazioni avanzate per i servizi](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
[Procedura: configurare i servizi delle applicazioni client](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)   
[Compilazione (pagina), Creazione progetti (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
[Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
