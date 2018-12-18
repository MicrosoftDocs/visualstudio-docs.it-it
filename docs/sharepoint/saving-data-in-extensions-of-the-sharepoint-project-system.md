---
title: Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56cdfb95de6f0e5f8644ea3c73daacbf90e33a97
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Salvataggio dei dati nelle estensioni del sistema di progetto SharePoint
  Quando si estende il sistema di progetto SharePoint, è possibile salvare i dati di tipo stringa che persiste dopo la chiusura di un progetto SharePoint. I dati sono in genere associato a un elemento di progetto specifico o con il progetto stesso.  
  
 Se si dispone di dati che non si desidera mantenere, è possibile aggiungere i dati in qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Per ulteriori informazioni, vedere [associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Salvataggio di dati è associato a un elemento di progetto  
 Quando si dispone di dati associato a un particolare elemento di progetto SharePoint, ad esempio il valore di una proprietà che aggiunge un elemento di progetto, è possibile salvare i dati per il file con estensione spdata per l'elemento del progetto. A tale scopo, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto. I dati aggiunti a questa proprietà viene salvati nel **ExtensionData** elemento nel file con estensione spdata per l'elemento del progetto. Per ulteriori informazioni, vedere [ExtensionData (elemento)](../sharepoint/extensiondata-element.md).  
  
 Esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per salvare il valore di una proprietà stringa che è definito in un tipo di elemento di progetto SharePoint personalizzato. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Salvataggio di dati è associato a un progetto  
 Quando si dispone di dati a livello di progetto, ad esempio il valore di una proprietà che aggiunta ai progetti SharePoint, è possibile salvare i dati per il file di progetto (file con estensione csproj o vbproj) o il file di progetto utente opzione (i. file csproj o. vbproj). Il file che si sceglie di salvare i dati in dipende da come si desidera dati da utilizzare:  
  
-   Se i dati siano disponibili per tutti gli sviluppatori che aprono il progetto di SharePoint, è possibile salvare i dati del file di progetto. Questo file è sempre archiviato nel database di controllo di origine, pertanto i dati in questo file sono disponibili per gli sviluppatori che estraggono il progetto.  
  
-   Se si desiderano dati sia disponibile solo per lo sviluppatore corrente che ha il progetto SharePoint aperto in Visual Studio, è possibile salvare i dati del file di progetto utente opzione. Questo file non è in genere archiviato nel database di controllo di origine, pertanto i dati in questo file non sono disponibili per gli sviluppatori che estraggono il progetto.  
  
### <a name="saving-data-to-the-project-file"></a>Salvataggio di dati al File di progetto  
 Per salvare i dati del file di progetto, è possibile convertire un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> l'oggetto in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> oggetto, quindi utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo. Esempio di codice riportato di seguito viene illustrato come utilizzare questo metodo per salvare il valore di una proprietà di progetto per il file di progetto. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Per ulteriori informazioni sulla conversione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> degli oggetti in altri tipi nel modello oggetto di automazione di Visual Studio o modello di integrazione, vedere [la conversione tra sistema di tipi di progetto SharePoint e altri tipi di progetto da Visual Studio ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Salvataggio di dati del File di progetto utente opzione  
 Per salvare i dati del file di progetto utente opzione, usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto. Esempio di codice riportato di seguito viene illustrato come utilizzare questa proprietà per salvare il valore di una proprietà di progetto per il file di progetto utente opzione. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associazione di dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  