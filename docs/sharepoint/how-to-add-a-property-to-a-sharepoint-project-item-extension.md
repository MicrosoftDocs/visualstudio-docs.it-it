---
title: "Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint | Documenti Microsoft"
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
ms.openlocfilehash: 1b096a1d524a1702d7fae01d35fb08e2fa697c70
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint
  È possibile utilizzare un'estensione di elemento di progetto per aggiungere una proprietà a qualsiasi elemento di progetto SharePoint che è già installato in Visual Studio. La proprietà viene visualizzata nel **proprietà** finestra quando è selezionato l'elemento del progetto in **Esplora**.  
  
 I passaggi seguenti presuppongono che un'estensione di elemento di progetto è già stato creato. Per ulteriori informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Per aggiungere una proprietà a un'estensione di elemento di progetto  
  
1.  Definire una classe con una proprietà pubblica che rappresenta la proprietà che si sta aggiungendo a un tipo di elemento di progetto. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto, è possibile definire tutte le proprietà della stessa classe o in classi diverse.  
  
2.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del *projectItemType* parametro.  
  
3.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come aggiungere una proprietà denominata **proprietà esempio** all'elemento del progetto ricevitore di eventi.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>Informazioni sul codice  
 Per garantire che la stessa istanza del `CustomProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento si verifica, l'esempio di codice aggiunge l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di questo evento si verifica il tempo di elemento al primo progetto. Ogni volta che questo evento si verifica nuovamente, il codice recupera l'oggetto. Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare dati a elementi di progetto, vedere [associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Per rendere permanenti le modifiche al valore della proprietà, il **impostare** funzione di accesso per `ExampleProperty` Salva il nuovo valore per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto a cui è associata la proprietà. Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per rendere persistenti i dati con elementi di progetto, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Specifica il comportamento delle proprietà personalizzate  
 È possibile definire come una proprietà personalizzata viene visualizzato e si comporta come il **proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che è presente il **proprietà** finestra.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che verrà visualizzata nella parte inferiore del **proprietà** finestra quando la proprietà è selezionata.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nel **proprietà** finestra e un valore di proprietà non stringa.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questi esempi richiedono un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  