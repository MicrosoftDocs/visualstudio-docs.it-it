---
title: 'Procedura: definire un tipo di elemento di progetto SharePoint | Documenti Microsoft'
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
ms.openlocfilehash: 4a0470e84b6c85fdb0786cdee27a2d208a594c0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procedura: definire un tipo di elemento di progetto SharePoint
  Quando si desidera creare un elemento di progetto SharePoint personalizzato, definire un tipo di elemento di progetto. Per ulteriori informazioni, vedere [tipi di elemento di definizione personalizzato SharePoint progetto](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Per definire un tipo di elemento di progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Alla classe, aggiungere gli attributi seguenti:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al costruttore dell'attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In una definizione di tipo elemento di progetto, questo attributo specifica l'identificatore di stringa per il nuovo elemento di progetto. È consigliabile utilizzare il formato *nome società*. *nome della funzionalità* per assicurarsi che tutti gli elementi di progetto hanno un nome univoco.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Questo attributo specifica l'icona da visualizzare per questo elemento di progetto in **Esplora**. Questo attributo è facoltativo. Se non si applica alla classe, Visual Studio visualizza un'icona predefinita per l'elemento di progetto. Se si imposta questo attributo, passare il nome completo di un'icona o bitmap incorporata nell'assembly.  
  
5.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo, utilizzare i membri del *projectItemTypeDefinition* parametro per definire il comportamento del tipo di elemento di progetto. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfacce. Per accedere a un'istanza specifica del tipo di elemento di progetto, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi, ad esempio <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come definire un tipo di elemento di progetto semplice. Questo tipo di elemento di progetto scrive un messaggio di **Output** finestra e **elenco errori** finestra quando un utente aggiunge un elemento di progetto di questo tipo a un progetto.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint in cui per scrivere il messaggio di **Output** finestra e **elenco errori** finestra. Per ulteriori informazioni, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>L'elemento del progetto di distribuzione  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento del progetto, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) del pacchetto per l'assembly, il modello e qualsiasi altro file che si desiderano distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  