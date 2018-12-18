---
title: XmlMappedRange (controllo) | Documenti Microsoft
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f4b78da11efafff45f34b3dc4ab9e7f1349a2e8a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="xmlmappedrange-control"></a>Controllo XmlMappedRange
  Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo è un intervallo che viene creato solo quando un elemento dello schema non ripetuto viene eseguito il mapping a una cella in Microsoft Office Excel. Ad esempio, quando il `maxOccurs` attributo di un elemento dello schema è uguale a 1. Dopo Visual Studio crea l'intervallo XML mappato, è possibile programmare utilizzandolo direttamente senza dover passare attraverso il modello a oggetti Excel. È possibile eliminare solo un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo all'interno di Excel quando viene rimosso il mapping dell'elemento.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come si ricerca per categorie: utilizzare XML di Mapping in Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Data binding al controllo  
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo supporta l'associazione a un singolo campo dati (data binding semplice). Il <xref:Microsoft.Office.Tools.Excel.ListObject> può controllo supporta il data binding complesso e viene creata automaticamente quando un elemento ripetuto dello schema viene mappato a una cella. Per altre informazioni, vedere [ListObject Control](../vsto/listobject-control.md).  
  
 Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> associato a un'origine dati usando il <xref:System.Windows.Forms.Control.DataBindings%2A> proprietà. Quando un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene aggiunto a una cella di foglio di lavoro, Visual Studio automaticamente genera un set di dati dai dati di celle mappate e associa il controllo di set di dati. La proprietà di associazione di dati predefinita del <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo riflette le modifiche.  
  
## <a name="formatting"></a>Formattazione  
 È possibile applicare la stessa formattazione a un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo che è possibile applicare a un <xref:Microsoft.Office.Interop.Excel.Range>. Questo include i bordi, i tipi di carattere, il formato numero e gli stili.  
  
## <a name="events"></a>Eventi  
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo sono:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: mappare schemi a fogli di lavoro all'interno di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  