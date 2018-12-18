---
title: Estensione di elementi di progetto SharePoint | Documenti Microsoft
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e990896720916048ab449c7ccb5a927577861256
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-project-items"></a>Estensione di elementi di progetto SharePoint
  Creare un'estensione di elemento di progetto quando si desidera aggiungere funzionalità a un tipo di elemento di progetto SharePoint che è già installato in Visual Studio. Ad esempio, è possibile creare un'estensione per l'elemento predefinito **ricevitore di eventi** o **definizione di elenco** gli elementi di progetto in Visual Studio o è possibile creare un'estensione per un tipo di elemento di progetto personalizzati. È anche possibile creare un'estensione per tutti i tipi di elementi di progetto SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Attività per l'estensione di elementi di progetto SharePoint  
 Per estendere un elemento di progetto, creare un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Per ulteriori informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Quando si estende un elemento di progetto, è anche possibile aggiungere le funzionalità seguenti per l'elemento del progetto:  
  
-   Aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora**. Aprire il menu di scelta rapida facendo clic con l'elemento del progetto o selezionandolo e quindi premendo MAIUSC + F10 le chiavi. Per ulteriori informazioni, vedere [procedura: aggiungere una voce di Menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Aggiungere una proprietà personalizzata per l'elemento del progetto. La proprietà viene visualizzata nel **proprietà** finestra quando si sceglie l'elemento del progetto in **Esplora**. Per ulteriori informazioni, vedere [procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Per una procedura dettagliata viene illustrato come creare, distribuire e testare un'estensione di elemento di progetto, vedere [procedura dettagliata: estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Informazioni sulla relazione tra le estensioni di elemento di progetto e istanze di elementi di progetto  
 Quando si crea un'estensione di elemento di progetto, Visual Studio consente di caricare l'estensione quando viene aggiunto un elemento di progetto del tipo associato a un progetto SharePoint. Ad esempio, se si crea un'estensione per **ricevitore di eventi** gli elementi di progetto Visual Studio consente di caricare l'estensione quando un utente aggiunge un **ricevitore di eventi** elemento di progetto per un progetto. Visual Studio Usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo **ricevitore di eventi** dell'elemento di progetto al progetto, la stessa istanza dell'estensione viene utilizzata per personalizzare il secondo elemento di progetto.  
  
 Per accedere a un'istanza specifica del tipo di elemento di progetto si estende, gestire uno del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> gli eventi del *projectItemType* parametro nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo. Per determinare quando viene aggiunto un elemento di progetto del tipo si estende a un progetto, ad esempio, è consigliabile gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per ulteriori informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identificatori per gli elementi di progetto SharePoint  
 Ogni elemento di progetto SharePoint è un identificatore di stringa corrispondente. È necessario conoscere l'identificatore per un elemento di progetto se si desidera eseguire le attività seguenti:  
  
-   Creare un'estensione per l'elemento del progetto. In questo caso, è necessario passare l'identificatore per l'elemento del progetto che si vuole estendere al costruttore del <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per creare un'estensione per tutti i tipi di progetto elemento, passare il  **\***  valore stringa.  
  
-   Aggiungere l'elemento del progetto a un progetto a livello di codice. In questo caso, è necessario passare l'identificatore per l'elemento di progetto per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metodo.  
  
 Nella tabella seguente sono elencati gli identificatori per gli elementi di progetto SharePoint sono inclusi con Visual Studio.  
  
|Nome di elemento di progetto|Identificatore di stringa|  
|-----------------------|-----------------------|  
|Modello di catalogo dati business|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo di contenuto|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ricevitore di eventi|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vuoto|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definizione di elenco<br /><br /> Definizione di elenco da tipo di contenuto|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Istanza di elenco|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modulo|Microsoft.VisualStudio.SharePoint.Module|  
|Flusso di lavoro sequenziale<br /><br /> Flusso di lavoro della macchina a stati|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definizione di sito|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Web Part visiva|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Form di associazione del flusso di lavoro|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Procedura dettagliata: Estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  