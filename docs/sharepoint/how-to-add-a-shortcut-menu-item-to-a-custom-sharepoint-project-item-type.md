---
title: 'Procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1fa954c2f24daa17ce4f1ed9aeb90df9f4566e58
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzata quando l'utente fa clic l'elemento del progetto in **Esplora**.  
  
 I passaggi seguenti presuppongono che sia già stata definita proprio tipo di elemento di progetto SharePoint. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Per aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzati  
  
1.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del *projectItemTypeDefinition* parametro.  
  
2.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.  
  
3.  Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente sceglie la voce di menu di scelta rapida.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta per un tipo di elemento di progetto personalizzati. Quando l'utente apre il menu di scelta rapida dall'elemento del progetto in **Esplora** e sceglie il **scrivere messaggi nella finestra Output** voce di menu, Visual Studio viene visualizzato un messaggio nel **Output**  finestra.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint in cui per scrivere il messaggio di **Output** finestra. Per ulteriori informazioni, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>L'elemento del progetto di distribuzione  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento del progetto, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) del pacchetto per l'assembly, il modello e qualsiasi altro file che si desiderano distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definizione di tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  