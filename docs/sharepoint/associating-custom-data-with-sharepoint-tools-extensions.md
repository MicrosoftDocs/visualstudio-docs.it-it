---
title: Estensioni degli strumenti di associazione di dati personalizzati con SharePoint | Documenti Microsoft
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
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8868300375d34664ba267b473f24d2c6a91ddd55
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>Associazione di dati personalizzati alle estensioni degli strumenti di SharePoint
  È possibile aggiungere dati personalizzati a determinati oggetti nelle estensioni degli strumenti di SharePoint. Ciò è utile quando si dispone di dati in una parte dell'estensione che si desidera accedere in un secondo momento da altro codice nell'estensione. Anziché implementare un modo personalizzato per archiviare e accedere ai dati, è possibile associare i dati a un oggetto nell'estensione e quindi recuperare i dati dallo stesso oggetto in un secondo momento.  
  
 Aggiunta di dati personalizzati agli oggetti è utile anche quando si desidera conservare i dati rilevanti per un elemento specifico in Visual Studio. Estensioni degli strumenti di SharePoint vengono caricate solo una volta in Visual Studio, pertanto l'estensione potrebbe funzionare con diverse voci (ad esempio progetti, gli elementi, del progetto o **Esplora Server** nodi) in qualsiasi momento. Se si dispone di dati personalizzati a cui sono rilevanti solo per un elemento specifico, è possibile aggiungere i dati per l'oggetto che rappresenta l'elemento.  
  
 Quando si aggiungono dati personalizzati agli oggetti nelle estensioni degli strumenti di SharePoint, i dati non vengono mantenute. I dati sono disponibili solo per la durata dell'oggetto. Dopo l'oggetto venga recuperato da garbage collection, i dati vengono persi.  
  
 Nelle estensioni del sistema del progetto SharePoint, è anche possibile salvare i dati di tipo stringa che persiste dopo aver scaricata l'estensione. Per ulteriori informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Oggetti che possono contenere dati personalizzati  
 È possibile aggiungere dati personalizzati in qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Questa interfaccia definisce solo una delle proprietà, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, che è una raccolta di oggetti dati personalizzati. Implementano i seguenti tipi di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="adding-and-retrieving-custom-data"></a>Aggiunta e recupero di dati personalizzati  
 Per aggiungere dati personalizzati a un oggetto in un'estensione degli strumenti di SharePoint, ottenere il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto a cui si desidera aggiungere i dati e quindi utilizzare il <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodo per aggiungere i dati all'oggetto.  
  
 Per recuperare i dati personalizzati da un oggetto in un'estensione degli strumenti di SharePoint, ottenere il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto e quindi utilizzare uno dei metodi seguenti:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Questo metodo restituisce **true** se esiste l'oggetto dati, o **false** se non esiste. È possibile utilizzare questo metodo per recuperare le istanze di tipi di valore o tipi di riferimento.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Questo metodo restituisce i dati oggetto se viene chiusa, o **null** se non esiste. È possibile utilizzare questo metodo solo per recuperare le istanze dei tipi di riferimento.  
  
 Esempio di codice seguente determina se un determinato oggetto dati è già associata a un elemento di progetto. Se l'oggetto dati non è già associato all'elemento di progetto, quindi il codice aggiunge l'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'elemento del progetto. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Estensione di Esplora Server per visualizzare Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato] (.. /SharePoint/How-to-Add-a-Property-to-a-Custom-SharePoint-Project-Item-Type.MD   
  