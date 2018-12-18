---
title: Definizione di tipi di elemento di progetto SharePoint personalizzato | Documenti Microsoft
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
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 271cc2227e7bfca38f98a7424a18b314d01c92c6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="defining-custom-sharepoint-project-item-types"></a>Definizione di tipi di elementi di progetto SharePoint
  Definire un nuovo tipo di elemento di progetto SharePoint quando si desidera creare un nuovo tipo di elemento di progetto SharePoint. Ad esempio, Visual Studio non include elementi di progetto SharePoint per l'aggiunta di campi o azioni personalizzate a un sito di SharePoint. È possibile definire i propri tipi di elementi di progetto SharePoint per la creazione di campi, le azioni personalizzate o altri tipi di componenti di SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Attività per la definizione di tipi di elemento di progetto SharePoint  
 Per definire un tipo di elemento di progetto personalizzati, compilare un assembly di estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Quando si definisce un tipo di elemento di progetto personalizzati, è anche possibile aggiungere le funzionalità seguenti per l'elemento del progetto:  
  
-   Aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora** chiavi facendovi clic sopra l'elemento del progetto o selezionandolo e quindi premendo MAIUSC + F10. Per ulteriori informazioni, vedere [procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Aggiungere una proprietà personalizzata per l'elemento del progetto. La proprietà viene visualizzata nel **proprietà** finestra quando si sceglie l'elemento del progetto in **Esplora**. Per ulteriori informazioni, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto in Visual Studio, creare un file con estensione spdata e creare un modello di elemento o un modello di progetto che è associato l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>Le relazioni tra tipi di elemento di progetto e istanze di elementi di progetto  
 Quando si definisce un tipo di elemento di progetto SharePoint, Visual Studio consente di caricare l'estensione quando viene aggiunto un elemento di progetto del tipo associato a un progetto SharePoint. Ad esempio, se si definisce un nuovo **l'azione personalizzata** tipo di elemento di progetto, Visual Studio consente di caricare l'estensione quando un utente aggiunge un **l'azione personalizzata** elemento di progetto per un progetto. Visual Studio Usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo **l'azione personalizzata** dell'elemento di progetto al progetto, la stessa istanza dell'estensione viene utilizzata per personalizzare il secondo elemento di progetto.  
  
 Per accedere a un'istanza specifica del tipo di elemento di progetto, gestire uno del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> gli eventi del *projectItemTypeDefinition* parametro nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Per determinare quando un elemento di progetto del tipo personalizzato viene aggiunto a un progetto, ad esempio, è consigliabile gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creazione di modelli di progetto e modelli di elemento per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  