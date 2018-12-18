---
title: 'Procedura: recuperare il servizio di progetto SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint project service
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b1abdf4a48d05285a7394469dd391caf48981f9f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Procedura: recuperare il servizio di progetto SharePoint
  È possibile accedere al servizio di progetto SharePoint in tipi di soluzioni seguenti:  
  
-   Un'estensione del sistema del progetto SharePoint, ad esempio un'estensione di progetto, l'estensione di elemento di progetto o definizione di tipo di elemento di progetto. Per ulteriori informazioni su questi tipi di estensioni, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Un'estensione del **connessioni di SharePoint** nodo **Esplora Server**. Per ulteriori informazioni su questi tipi di estensioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Un altro tipo di estensione di Visual Studio, ad esempio un pacchetto VSPackage.  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>Recupero del servizio nelle estensioni del sistema di progetto  
 In qualsiasi estensione del sistema del progetto SharePoint, è possibile accedere al servizio di progetto utilizzando il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto.  
  
 È anche possibile recuperare il servizio di progetto tramite le procedure seguenti.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Per recuperare il servizio in un'estensione di progetto  
  
1.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo.  
  
2.  Utilizzare il *projectService* parametro per accedere al servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto in cui per scrivere un messaggio di **Output** finestra e **elenco errori** in un'estensione di progetto semplice.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Per ulteriori informazioni sulla creazione di estensioni di progetto, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Per recuperare il servizio in un'estensione di elemento di progetto  
  
1.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo.  
  
2.  Utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> proprietà del *projectItemType* parametro per recuperare il servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto per scrivere un messaggio per il **Output** finestra e **elenco errori** in una semplice estensione della finestra il **definizionedielenco** elemento del progetto.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Per ulteriori informazioni sulla creazione di estensioni di elemento di progetto, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Per recuperare il servizio in una definizione di tipo di elemento di progetto  
  
1.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo.  
  
2.  Utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> proprietà del *typeDefinition* parametro per recuperare il servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto in cui per scrivere un messaggio di **Output** finestra e **elenco errori** finestra in una definizione di tipo di elemento di progetto semplice.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Per ulteriori informazioni sulla definizione di tipi di elemento di progetto, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>Recupero del servizio nelle estensioni di Esplora Server  
 In un'estensione del **connessioni di SharePoint** nodo **Esplora Server**, è possibile accedere al servizio di progetto utilizzando il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Per recuperare il servizio in un'estensione di Esplora Server  
  
1.  Ottenere un <xref:System.IServiceProvider> dall'oggetto di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto nell'estensione.  
  
2.  Utilizzare il <xref:System.IServiceProvider.GetService%2A> metodo per richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto in cui per scrivere un messaggio di **Output** finestra e **elenco errori** finestra dal menu di scelta rapida che consente di aggiungere l'estensione per i nodi elenco **Esplora server**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Per ulteriori informazioni sull'estensione di **connessioni di SharePoint** nodo **Esplora Server**, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>Recupero del servizio nelle altre estensioni di Visual Studio  
 È possibile recuperare il servizio di progetto in un pacchetto VSPackage o in qualsiasi estensione di Visual Studio che ha accesso a un <xref:EnvDTE80.DTE2> oggetto nel modello a oggetti di automazione, ad esempio la creazione guidata modello di progetto che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
 In un pacchetto VSPackage, è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto utilizzando uno dei metodi seguenti:  
  
-   Il <xref:System.IServiceProvider.GetService%2A> metodo di un VSPackage gestito da cui deriva il <xref:Microsoft.VisualStudio.Shell.Package> classe. Per ulteriori informazioni, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md).  
  
-   Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo. Per ulteriori informazioni, vedere [usare GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 In un'estensione di Visual Studio che ha accesso a un <xref:EnvDTE80.DTE2> oggetto, è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto utilizzando il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo di un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> oggetto. Per ulteriori informazioni, vedere [il recupero di un servizio dall'oggetto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo del servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)   
 [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  