---
title: 'Procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aea2dd600548d76d57d58c8cfc0313c92ccb9f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint
  È possibile aggiungere una voce di menu di scelta rapida per qualsiasi progetto SharePoint. La voce di menu viene visualizzata quando l'utente fa clic in un nodo di progetto **Esplora**.  
  
 I passaggi seguenti presuppongono che un'estensione di progetto è già stato creato. Per ulteriori informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Per aggiungere una voce di menu di scelta rapida per i progetti SharePoint  
  
1.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento del *projectService* parametro.  
  
2.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.  
  
3.  Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente fa clic sulla voce di menu di scelta rapida.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come aggiungere una voce di menu di scelta rapida ai nodi di progetto SharePoint in **Esplora**. Quando l'utente fa un nodo di progetto e sceglie il **scrivere messaggi nella finestra di Output** voce di menu, Visual Studio viene visualizzato un messaggio nel **Output** finestra. In questo esempio utilizza il servizio di progetto SharePoint per visualizzare il messaggio. Per ulteriori informazioni, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Procedura: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  