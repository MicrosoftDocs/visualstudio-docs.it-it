---
title: 'Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato | Documenti Microsoft'
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
ms.openlocfilehash: 2da3ebd75ef8b195b0e4c6117b28a6bc294ac050
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una proprietà per l'elemento del progetto. La proprietà viene visualizzata nel **proprietà** finestra quando è selezionato l'elemento del progetto in **Esplora**.  
  
 I passaggi seguenti presuppongono che sia già stata definita proprio tipo di elemento di progetto SharePoint. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Per aggiungere una proprietà a una definizione di un tipo di elemento di progetto  
  
1.  Definire una classe con una proprietà pubblica che rappresenta la proprietà che si sta aggiungendo il tipo di elemento di progetto personalizzati. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto personalizzati, è possibile definire tutte le proprietà della stessa classe o in classi diverse.  
  
2.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del *projectItemTypeDefinition* parametro.  
  
3.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà personalizzate per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come aggiungere una proprietà denominata **esempio proprietà** su un oggetto personalizzato dell'elemento di progetto tipo.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>Informazioni sul codice  
 Per garantire che la stessa istanza del `CustomProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento si verifica, l'esempio di codice salva l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di questo evento si verifica il tempo di elemento al primo progetto. Ogni volta che questo evento si verifica nuovamente, il codice recupera l'oggetto. Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per salvare i dati con elementi di progetto, vedere [associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Per rendere permanenti le modifiche al valore della proprietà, il **impostare** funzione di accesso per `ExampleProperty` Salva il nuovo valore per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto a cui è associata la proprietà. Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per rendere persistenti i dati con elementi di progetto, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Specifica il comportamento delle proprietà personalizzate  
 È possibile definire come una proprietà personalizzata viene visualizzato e si comporta come il **proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che è presente il **proprietà** finestra.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che verrà visualizzata nella parte inferiore della **proprietà** finestra quando la proprietà è selezionata.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nella **proprietà** finestra e un valore di proprietà non stringa.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questi esempi di codice richiedono un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>L'elemento del progetto di distribuzione  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento del progetto, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) del pacchetto per l'assembly, il modello e qualsiasi altro file che si desiderano distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definizione di tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  