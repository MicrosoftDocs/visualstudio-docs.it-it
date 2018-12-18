---
title: "Procedura: aggiungere una proprietà ai progetti SharePoint | Documenti Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4318550e74d5324195de173659d96abaf952979
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Procedura: aggiungere una proprietà ai progetti SharePoint
  È possibile utilizzare un'estensione di progetto per aggiungere una proprietà a qualsiasi progetto SharePoint. La proprietà viene visualizzata nel **proprietà** finestra quando è selezionato il progetto in **Esplora**.  
  
 I passaggi seguenti presuppongono che un'estensione di progetto è già stato creato. Per ulteriori informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Per aggiungere una proprietà a un progetto SharePoint  
  
1.  Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere ai progetti SharePoint. Se si desidera aggiungere più proprietà, è possibile definire tutte le proprietà della stessa classe o in classi diverse.  
  
2.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento del *projectService* parametro.  
  
3.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come aggiungere due proprietà ai progetti SharePoint. Una proprietà mantiene i relativi dati nel file di progetto utente opzione (i. file csproj o. vbproj). L'altra proprietà mantiene i dati nel file di progetto (file con estensione csproj o vbproj).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Informazioni sul codice  
 Per garantire che la stessa istanza del `CustomProjectProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento si verifica, l'esempio di codice aggiunge l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di questo evento si verifica il progetto la prima volta. Ogni volta che questo evento si verifica nuovamente, il codice recupera l'oggetto. Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare i dati con i progetti, vedere [associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Per rendere permanenti le modifiche ai valori della proprietà, il **impostare** funzioni di accesso per le proprietà utilizzare le API seguenti:  
  
-   `CustomUserFileProperty`Usa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà per salvare il valore del file di progetto utente opzione.  
  
-   `CustomProjectFileProperty`Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> per salvare il relativo valore per il file di progetto.  
  
 Per ulteriori informazioni sulla persistenza dei dati in questi file, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Specifica il comportamento delle proprietà personalizzate  
 È possibile definire come una proprietà personalizzata viene visualizzato e si comporta come il **proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che è presente il **proprietà** finestra.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che verrà visualizzata nella parte inferiore del **proprietà** finestra quando la proprietà è selezionata.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nel **proprietà** finestra e un valore di proprietà non stringa.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   VisualStudio  
  
-   8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  