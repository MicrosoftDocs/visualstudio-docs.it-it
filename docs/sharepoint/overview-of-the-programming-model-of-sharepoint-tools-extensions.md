---
title: Panoramica del modello di programmazione di SharePoint di estensioni degli strumenti | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a52d05dd22ae88deecc2d79d3ab3de7d3c3b6344
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Cenni preliminari sul modello di programmazione delle estensioni degli strumenti di SharePoint
  Quando si crea un'estensione per gli strumenti di SharePoint in Visual Studio, si inizia implementando una o più interfacce di estendibilità che vengono esposte dagli strumenti di SharePoint. Nella maggior parte dei casi, si useranno anche altri tipi forniti dagli strumenti di SharePoint per implementare le funzionalità nell'estensione. In alcuni scenari è possibile usare anche tipi in altri modelli a oggetti forniti da Visual Studio e SharePoint. È necessario comprendere lo scopo di ciascuno di questi modelli a oggetti e sapere come usarli con l'altro per creare estensioni per gli strumenti di SharePoint.  
  
## <a name="extending-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Estensione degli strumenti di SharePoint mediante l'implementazione di interfacce di estendibilità  
 Visual Studio usa Managed Extensibility Framework (MEF) in .NET Framework 4 per fornire il modello di estendibilità per gli strumenti di SharePoint. MEF è un'API (implementata nell'assembly System.ComponentModel.Composition) che consente alle applicazioni di esporre i punti di estendibilità e individuare e caricare le estensioni in fase di esecuzione. Per altre informazioni su MEF, vedere [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).  
  
 Per estendere gli strumenti di SharePoint, è necessario implementare una o più interfacce di estendibilità che vengono esposte da Visual Studio. È inoltre necessario applicare l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> e, se necessario, gli altri attributi specifici degli strumenti di SharePoint all'implementazione dell'interfaccia. Nella tabella seguente vengono elencate le interfacce che è possibile implementare per estendere gli strumenti di SharePoint.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementare questa interfaccia per definire un nuovo tipo di elemento di progetto SharePoint. Per un esempio, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementare questa interfaccia per estendere un tipo di elemento di progetto SharePoint già installato in Visual Studio. Per un esempio, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementare questa interfaccia per estendere i progetti SharePoint. Per un esempio, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementare questa interfaccia per definire un nuovo passaggio di distribuzione che può essere eseguito quando un elemento di progetto SharePoint viene distribuito o ritratto. Per un esempio, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementare questa interfaccia per estendere un nodo esistente nel **connessioni di SharePoint** nodo il **Esplora Server** finestra. Per un esempio, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementare questa interfaccia per definire un nuovo tipo di nodo sotto il **connessioni di SharePoint** nodo il **Esplora Server** finestra. Per un esempio, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementare questa interfaccia per definire una regola di convalida della funzionalità personalizzata. Per un esempio, vedere [procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementare questa interfaccia per definire una regola di convalida del pacchetto personalizzata. Per un esempio, vedere [procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Dopo aver implementato un'estensione degli strumenti di SharePoint, è necessario distribuire l'assembly dell'estensione in un pacchetto di Visual Studio Extension (VSIX) per consentire a Visual Studio di individuare e caricare l'estensione. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="understanding-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Informazioni sui modelli a oggetti usati nelle estensioni degli strumenti di SharePoint  
 È possibile usare vari modelli a oggetti quando si creano estensioni per gli strumenti di SharePoint:  
  
-   *Modello a oggetti degli strumenti di SharePoint*. Questo modello a oggetti fornisce le interfacce di estendibilità implementate per creare le estensioni degli strumenti di SharePoint e altri tipi correlati.  
  
-   *Visual Studio automazione e integrazione modelli a oggetti*. Usare questi modelli a oggetti per accedere alle funzionalità di Visual Studio che esulano dall'ambito del modello a oggetti degli strumenti di SharePoint.  
  
    > [!NOTE]  
    >  È possibile convertire alcuni oggetti nel modello a oggetti degli strumenti di SharePoint in oggetti del modello a oggetti di automazione e integrazione di Visual Studio e viceversa, tramite il servizio di progetto SharePoint. Per ulteriori informazioni, vedere [la conversione tra sistema di tipi di progetto SharePoint e altri tipi di progetto da Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Modelli a oggetti SharePoint server e client*. Usare questi modelli a oggetti per modificare un sito di SharePoint o per recuperare dati da un sito di SharePoint dal contesto di un'estensione degli strumenti di SharePoint.  
  
### <a name="sharepoint-tools-object-model"></a>Modello a oggetti degli strumenti di SharePoint  
 Ogni estensione degli strumenti di SharePoint usa dei tipi nel modello a oggetti degli strumenti di SharePoint per definire il comportamento e le funzionalità principali dell'estensione. Nella tabella seguente vengono descritti gli spazi dei nomi inclusi in questo modello a oggetti.  
  
|Assembly|Spazio dei nomi|Descrizione|  
|--------------|---------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Contiene i tipi che consentono di estendere e automatizzare il sistema di progetto SharePoint. Ad esempio, è possibile estendere i progetti e gli elementi del progetto SharePoint predefiniti oppure crearne di personalizzati. Per ulteriori informazioni, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contiene i tipi usati per estendere il processo di distribuzione per i progetti SharePoint, ad esempio la creazione di configurazioni di distribuzione e di fasi di distribuzione personalizzati. Per ulteriori informazioni, vedere [estensione SharePoint e distribuzione di pacchetti](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contiene i tipi che consentono di estendere i nodi sotto il **connessioni di SharePoint** nodo il **Esplora Server** finestra, o per definire nuovi tipi di nodi. Per ulteriori informazioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Contiene i tipi usati per accedere alle definizioni di funzionalità in un progetto SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contiene i tipi usati per accedere alla definizione di un pacchetto in una soluzione SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contiene i tipi usati per personalizzare il comportamento della convalida della funzionalità e del pacchetto per i progetti SharePoint. Per ulteriori informazioni, vedere [procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contiene i tipi che è possibile utilizzare per la creazione personalizzata *i comandi di SharePoint*. Un comando di SharePoint è un metodo che chiama il modello a oggetti server di SharePoint da un'estensione degli strumenti di SharePoint. Per ulteriori informazioni, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contiene i tipi che è possibile utilizzare per ottenere informazioni sul integrato **Esplora Server** i nodi che rappresentano singoli componenti in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto. Per ulteriori informazioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### <a name="visual-studio-automation-object-model"></a>Modello a oggetti di automazione di Visual Studio  
 Il modello a oggetti di automazione di Visual Studio fornisce API che è possibile usare per automatizzare i progetti di Visual Studio e l'IDE. Usare il modello a oggetti Visual Studio per eseguire attività correlate al progetto che non sono specifiche dei progetti di SharePoint o per eseguire altre attività di automazione generali in Visual Studio. In genere, questo modello a oggetti viene spesso usato nelle macro e nei componenti aggiuntivi di Visual Studio, ma è possibile usarlo anche nelle estensioni degli strumenti di SharePoint.  
  
 La parte principale del modello a oggetti di automazione di Visual Studio è definita nell'assembly EnvDTE.dll. Il EnvDTE*versione*assembly DLL forniscono funzionalità aggiuntive che è stata introdotta in versioni specifiche di Visual Studio. Questi assembly sono inclusi in Visual Studio.  
  
 Per ulteriori informazioni sul modello a oggetti di automazione, vedere [riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
### <a name="visual-studio-integration-object-model"></a>Modello a oggetti di integrazione di Visual Studio  
 Modello a oggetti di integrazione fornisce le API che consente di aggiungere funzionalità a Visual Studio creando un *VSPackage*. Un VSPackage è un modulo che consente di estendere l'IDE di Visual Studio fornendo funzionalità personalizzate quali le finestre degli strumenti, gli editor, le finestre di progettazione, i servizi e i progetti.  
  
 Se si desidera aggiungere una nuova funzionalità di Visual Studio che verrà usata con gli strumenti predefiniti di SharePoint, è possibile usare il modello a oggetti di integrazione. Ad esempio, se si crea un elemento di progetto SharePoint personalizzato che rappresenta un'azione personalizzata per un sito di SharePoint, è possibile creare un VSPackage che implementa una finestra di progettazione per l'azione personalizzata. È possibile associare la finestra di progettazione con l'azione personalizzata aggiungendo una voce di menu di scelta rapida per l'elemento di progetto che rappresenta l'azione personalizzata in **Esplora**. È possibile aprire la finestra di progettazione aprendo il relativo menu di scelta rapida (uno facendo clic con il progetto azione personalizzata o di elemento selezionandolo e quindi premendo MAIUSC + F10 chiavi) e quindi scegliendo **aprire**.  
  
 Questo modello a oggetti è definito in un set di assembly inclusi in Visual Studio SDK. Alcuni degli assembly principali di questo modello a oggetti includono Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll e Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Per ulteriori informazioni sul modello a oggetti di integrazione, vedere [Cenni preliminari sul modello di automazione](/visualstudio/extensibility/internals/automation-model-overview) e [riferimenti di Visual Studio SDK](/visualstudio/extensibility/visual-studio-sdk-reference).  
  
### <a name="sharepoint-object-models"></a>Modelli a oggetti di SharePoint  
 Le estensioni degli strumenti di SharePoint possono usare le API di SharePoint per modificare un sito di SharePoint o per recuperare dati da un sito di SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] forniscono due modelli a oggetti diversi: un modello a oggetti del server e un modello a oggetti del client.  
  
 È possibile usare le API in entrambi i modelli a oggetti in un'estensione degli strumenti di SharePoint, ma ogni modello a oggetti presenta alcuni vantaggi e svantaggi nel contesto delle estensioni degli strumenti di SharePoint. Per ulteriori informazioni, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Modello a oggetti|Descrizione|  
|------------------|-----------------|  
|Modello a oggetti del server|Il modello a oggetti del server fornisce l'accesso a tutte le funzionalità esposte da [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] a livello di codice. Questo modello a oggetti è progettato per essere usato dalle soluzioni di SharePoint eseguibili nel server di SharePoint. La maggior parte di questo modello a oggetti è definita nell'assembly Microsoft.SharePoint.dll. Per ulteriori informazioni sul modello a oggetti server, vedere [utilizzando il modello a oggetti lato Server SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Modello a oggetti del client|Il modello a oggetti del client è un subset del modello a oggetti del server che può essere usato per interagire con dati di SharePoint da un client remoto o dal server. È progettato per ridurre al minimo il numero di round trip che devono essere eseguiti per le attività comuni. La maggior parte del modello a oggetti del client è definita negli assembly Microsoft.SharePoint.Client.dll e Microsoft.SharePoint.Client.Runtime.dll. Per ulteriori informazioni sul modello a oggetti client, vedere [modello a oggetti Client gestito](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Uso del servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
  
  