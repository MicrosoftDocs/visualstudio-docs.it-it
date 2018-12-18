---
title: Progettazione e creazione di soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e43824ed3fa34a7cd22b98fb25f946f36cb8eab6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="designing-and-creating-office-solutions"></a>Progettazione e creazione di soluzioni Office
  Visual Studio fornisce modelli di progetto che è possibile utilizzare per creare diversi tipi di soluzioni Office. In questa sezione della documentazione vengono descritti i modelli di progetto e viene fornito materiale sussidiario sulla creazione di progetti di Office. Per informazioni su come implementare le personalizzazioni dell'interfaccia utente e del codice dopo aver creato il progetto, vedere [lo sviluppo di soluzioni Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="creating-office-projects"></a>Creazione di progetti Office  
 Prima di iniziare, è necessario stabilire i requisiti e individuare il tipo di soluzione più adatta alle proprie esigenze. Ad esempio, se la soluzione Office deve essere eseguita ogni volta che viene usata l'applicazione, un componente aggiuntivo VSTO è più adatto per soddisfare le esigenze. Se il codice è strettamente integrato con un unico documento, creare una personalizzazione a livello di documento. Questi tipi di progetto sono disponibili come modelli di progetto Visual Studio. Per ulteriori informazioni sui modelli di progetto di Office inclusi in Visual Studio, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md). Per ulteriori informazioni su come creare progetti di Office, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 I progetti Office presentano funzionalità ed elementi di progetto diversi da altri tipi di progetti in Visual Studio. Ad esempio, quando si crea un progetto a livello di documento, il documento o cartella di lavoro nel progetto può essere aperto e modificato in Visual Studio. Per ulteriori informazioni, vedere [progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choosing-a-net-framework-version"></a>Scelta di una versione di .NET Framework  
 Dopo aver selezionato il tipo di progetto che meglio soddisfa le proprie esigenze, è possibile scegliere quale versione di .NET Framework utilizzare nel processo di sviluppo. È possibile destinare le seguenti versioni di .NET Framework nei progetti di Office:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 Perché la soluzione funzioni è necessario che nei computer degli utenti finali sia installata la versione di .NET Framework di destinazione del progetto. Ad esempio, se il progetto è per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], sui computer degli utenti finali deve essere installato [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questo esempio, la soluzione non verrà eseguita se nei computer degli utenti finali è installato solo .NET Framework 3.5.  
  
 Se si esegue la migrazione di un progetto di componente aggiuntivo VSTO destinato a .NET Framework 3.5, Visual Studio modifica il framework di destinazione del progetto impostandolo su [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, a seconda della versione di Office installata.  
  
 Dopo la modifica del framework di destinazione, tuttavia, potrebbe essere necessario modificare parte del codice nel progetto se vengono utilizzate alcune funzionalità. Per ulteriori informazioni su come modificare il framework di destinazione, vedere [procedura: destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Per ulteriori informazioni sulle modifiche potrebbe essere necessario apportare al progetto, vedere [migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Se Visual Studio modifica .NET Framework di destinazione per il progetto e si utilizza ClickOnce per distribuire la soluzione, assicurarsi di selezionare anche la versione corrispondente di .NET Framework nel **prerequisiti** la finestra di dialogo. Questa selezione non viene modificata automaticamente quando si modifica il framework di destinazione per il progetto. Per ulteriori informazioni, vedere [procedura: installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Non è possibile usare .NET Framework 3.5 o versioni precedenti nei progetti Office creati tramite [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. I progetti di Office create mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] richiedono funzionalità che sono state introdotte in [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
### <a name="understanding-when-the-office-pias-are-required-on-end-user-computers"></a>Stabilire quando sono necessari gli assembly di interoperabilità primari di Office nei computer degli utenti finali  
 Per impostazione predefinita, assembly di interoperabilità primari Office (PIA) non è necessario sia installato nel computer dell'utente finale se il **incorpora tipi di interoperabilità** di ogni riferimento di interoperabilità primari di Office nel progetto è impostata su **True**, che è il valore predefinito. In questo scenario, le informazioni sul tipo per i tipi di assembly di interoperabilità primari utilizzati dalla soluzione vengono incorporate nell'assembly della soluzione quando si compila il progetto. In fase di esecuzione, le informazioni sul tipo incorporato viene utilizzati invece di assembly di interoperabilità primari per effettuare chiamate nel modello a oggetti basato su COM dell'applicazione di Office. Per ulteriori informazioni su come i tipi da assembly di interoperabilità primari vengono incorporati nella soluzione, vedere [equivalenza del tipo e i tipi di interoperabilità incorporati](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Se il **incorpora tipi di interoperabilità** di ogni riferimento di interoperabilità primari di Office nel progetto è impostata su **False**, primari di Office devono essere installati e registrati nella global assembly cache in ogni computer dell'utente finale che esegue la soluzione. Nella maggior parte dei casi, gli assembly di interoperabilità primari vengono installati per impostazione predefinita con Office, ma è anche possibile includere l'assembly di interoperabilità primario ridistribuibile come prerequisito per la soluzione. Per ulteriori informazioni, vedere [prerequisiti per la distribuzione di soluzioni Office](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understanding-the-client-profile"></a>Informazioni su Client Profile  
 .NET Framework Client Profile è un sottoinsieme della versione completa di .NET Framework. È possibile scegliere .NET Framework Client Profile se è necessario utilizzare solo le funzionalità client di .NET Framework e si desidera fornire l'esperienza di distribuzione più veloce per la soluzione Office. Per altre informazioni, vedere [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 Quando si crea un progetto Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)],  [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] è la destinazione predefinita. Se si desidera sviluppare soluzioni per la versione completa di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], è necessario impostare questa opzione dopo la creazione del progetto. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="creating-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Creazione di soluzioni per l'edizione a 64 bit di Microsoft Office  
 Microsoft Office è disponibile nelle edizioni a 64 bit e a 32 bit. Per creare soluzioni Office che possono essere eseguiti in tutte le edizioni, l'impostazione della piattaforma di destinazione per il progetto deve essere impostata su **qualsiasi CPU**. Questo è il valore predefinito per i progetti Office. Per ulteriori informazioni, vedere [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
 Sono disponibili versioni a 32 e 64 bit separate di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che vengono utilizzate per le edizioni a 64 bit e a 32 bit di Microsoft Office. Per altre informazioni, vedere [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Assembly nelle soluzioni Office  
 Quando si crea un progetto di Office mediante gli strumenti di sviluppo per Office in Visual Studio, il codice scritto viene compilato in un assembly. L'assembly viene in genere distribuito in un server condiviso o in una directory sul computer client.  
  
 Gli assembly nelle soluzioni Office vengono caricati da un'applicazione di Office. Dopo che l'assembly viene caricato, il codice nell’assembly può rispondere agli eventi generati nell'applicazione (ad esempio quando un utente fa clic su una voce di menu). Il codice nell’assembly può inoltre effettuare chiamate nel modello a oggetti per automatizzare ed estendere l'applicazione e può utilizzare una qualsiasi delle classi in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Per ulteriori informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md) e [aggiuntivi architettura di VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 Le soluzioni Office utilizzano i manifesti di distribuzione e di applicazione per identificare l'assembly. I manifesti contengono informazioni su nome, versione e percorso dell'assembly, per cui l'applicazione può trovare, collegare ed eseguire l'assembly corretto. Per altre informazioni, vedere [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 I progetti a livello di documento includono un documento oltre a un assembly. Il documento agisce come front-end dell'applicazione ed è il luogo in cui avviene l'interazione dell’utente. Ogni documento può avere un solo assembly principale del progetto associato. Tuttavia, più documenti possono puntare allo stesso assembly.  
  
 Gli assembly nei progetti a livello di documento non sono incorporati nel documento, ma vengono archiviati in una posizione diversa e sono identificati dal manifesto di applicazione del documento.  
  
## <a name="security-considerations-for-assemblies"></a>Considerazioni sulla sicurezza per gli assembly  
 Perché una soluzione Office venga eseguita in un computer, gli assembly utilizzati dalla soluzione devono essere attendibili per l'esecuzione. Per ulteriori informazioni sulla sicurezza, vedere [protezione di soluzioni Office](../vsto/securing-office-solutions.md).  
  
 Per impostazione predefinita, l'assembly della soluzione e tutti gli assembly di riferimento che si trovano nella cartella di output del progetto sono attendibili per l'esecuzione nel computer di sviluppo quando si compila il progetto. Per ulteriori informazioni, vedere [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
 Per motivi di sicurezza, è consigliabile creare progetti nel computer locale anziché svilupparli in un percorso condiviso. Per ulteriori informazioni, vedere [sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Assembly a cui viene fatto riferimento  
 L'assembly può fare riferimento ad altri assembly elencati nei riferimenti del progetto. Tuttavia, un assembly del progetto a livello di documento non può fare riferimento a un altro assembly del progetto a livello di documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md)   
 [Esecuzione di soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Procedura: impostare le informazioni di configurazione per una soluzione Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Utilizzo della funzionalità di Office in Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md)   
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  