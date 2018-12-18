---
title: 'Procedura: gestire i conflitti di distribuzione | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c3bbd5bc7d69fbc48d2c754151a3ec6b5fcb612c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-handle-deployment-conflicts"></a>Procedura: gestire i conflitti di distribuzione
  È possibile fornire il proprio codice per gestire i conflitti di distribuzione per un elemento di progetto SharePoint. È possibile ad esempio, se già presente nel percorso di distribuzione, tutti i file nell'elemento di progetto corrente e quindi eliminare i file distribuiti prima di distribuita l'elemento del progetto corrente. Per ulteriori informazioni sui conflitti di distribuzione, vedere [estensione SharePoint e distribuzione di pacchetti](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Per gestire un conflitto di distribuzione  
  
1.  Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
    -   [Procedura: Creare un'estensione di elemento del progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Nell'estensione, gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> evento di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto (in un'estensione di elemento di progetto o l'estensione di progetto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto (in una definizione di un nuovo tipo di elemento di progetto).  
  
3.  Nel gestore eventi, determinare se si verifica un conflitto tra l'elemento di progetto che si sta distribuendo e la soluzione distribuita nel sito di SharePoint, in base ai criteri che si applicano al proprio scenario. È possibile utilizzare il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> proprietà del parametro di argomenti dell'evento per analizzare l'elemento del progetto che si sta distribuendo ed è possibile analizzare i file nel percorso di distribuzione chiamando un comando di SharePoint che definita per questo scopo.  
  
     Per molti tipi di conflitti, si potrebbe innanzitutto desidera determinare il passaggio di distribuzione è in esecuzione. È possibile farlo tramite il <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> proprietà del parametro di argomenti dell'evento. Anche se è in genere utile per rilevare conflitti durante predefinito <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> passaggio di distribuzione, è possibile verificare se è in conflitto durante un qualsiasi passaggio di distribuzione.  
  
4.  Se esiste un conflitto, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodo il <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> proprietà degli argomenti dell'evento per creare un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto. Questo oggetto rappresenta il conflitto di distribuzione. Nella chiamata al <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> (metodo), specificare anche il metodo viene chiamato per risolvere il conflitto.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato il processo di base per la gestione di un conflitto di distribuzione in un'estensione di elemento di progetto per gli elementi di progetto di definizione di elenco. Per gestire un conflitto di distribuzione per un tipo di elemento di progetto diverso, passare una stringa diversa per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per ulteriori informazioni, vedere [estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
 Per semplicità, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore dell'evento in questo esempio si presuppone che esista un conflitto di distribuzione (vale a dire, sempre aggiunto un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto) e il `Resolve` metodo restituisce semplicemente **true** per indicare che il conflitto è stato risolto. In uno scenario reale, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore dell'evento potrebbe determinare innanzitutto se esiste un conflitto tra un file nell'elemento di progetto corrente e un file nel percorso di distribuzione e quindi aggiungere un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto solo se esiste un conflitto. Ad esempio, è possibile utilizzare il `e.ProjectItem.Files` proprietà nel gestore eventi per analizzare i file nell'elemento di progetto e si potrebbe chiamare un comando di SharePoint per analizzare i file nel percorso di distribuzione. Analogamente, in uno scenario reale il `Resolve` metodo può chiamare un comando di SharePoint per risolvere il conflitto nel sito di SharePoint. Per ulteriori informazioni sulla creazione di comandi di SharePoint, vedere [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione e l'estensione dei pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procedura: eseguire codice quando la distribuzione esecuzione dei passaggi](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Procedura: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  