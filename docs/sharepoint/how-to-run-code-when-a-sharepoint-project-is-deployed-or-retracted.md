---
title: 'Procedura: eseguire codice quando un progetto SharePoint viene distribuito o ritratto | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c76d62751670e4fdd38c1ebb3042e5c403ee1ca6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Procedura: eseguire codice quando un progetto SharePoint viene distribuito o ritratto
  Se si desidera eseguire attività aggiuntive quando un progetto SharePoint viene distribuito o ritratto, è possibile gestire gli eventi generati da Visual Studio. Per ulteriori informazioni, vedere [estensione SharePoint e distribuzione di pacchetti](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Per eseguire codice quando un progetto SharePoint viene distribuito o ritratto  
  
1.  Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
    -   [Procedura: Creare un'estensione di elemento del progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Nell'estensione accesso il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per ulteriori informazioni, vedere [procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> gli eventi del servizio di progetto.  
  
4.  Nei gestori eventi, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> per ottenere informazioni relative alla sessione corrente di distribuzione. Ad esempio, è possibile determinare quale progetto si trova nella sessione corrente di distribuzione e se viene distribuito o ritratto.  
  
 Esempio di codice seguente viene illustrato come gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> gli eventi in un'estensione di progetto. Questa estensione scrive un messaggio aggiuntivo per il **Output** finestra quando la distribuzione viene avviata e completata per un progetto SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione ed estensione dei pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Procedura: Eseguire codice all'esecuzione dei passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  