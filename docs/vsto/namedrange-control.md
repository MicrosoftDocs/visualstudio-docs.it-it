---
title: NamedRange (controllo) | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22adc003c10e95de0e701eb3f382d9e530b28acf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="namedrange-control"></a>NamedRange (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è un intervallo con un nome univoco che espone gli eventi e può essere associato ai dati. Per altre informazioni, vedere [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Creazione del controllo  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione o in fase di esecuzione nei progetti a livello di documento.  
  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO. Per altre informazioni, vedere [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Per impostazione predefinita, gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 I controlli<xref:Microsoft.Office.Tools.Excel.NamedRange> possono essere costituiti solo da intervalli in fogli specifici. I controlli<xref:Microsoft.Office.Tools.Excel.NamedRange> non possono avere nomi relativi che si applicano a tutti i fogli e non possono essere costituiti da intervalli estesi a due o più fogli di lavoro di una cartella di lavoro (intervalli 3D).  
  
## <a name="binding-data-to-the-control"></a>Data binding al controllo  
 Un intervallo denominato può sembrare il candidato ideale per il data binding complesso, dal momento che può includere diverse celle. Un intervallo è però semplicemente una raccolta di celle di cui non è possibile eseguire facilmente il mapping a una determinata colonna particolare di un set di dati. Di conseguenza, i controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> supportano solo il data binding semplici. Per il data binding complesso è possibile usare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> . Per altre informazioni, vedere [ListObject Control](../vsto/listobject-control.md).  
  
 È possibile associare il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un'origine dati usando le proprietà <xref:System.Windows.Forms.Control.DataBindings%2A> . La proprietà di data binding predefinita del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> rispecchia le modifiche.  
  
## <a name="formatting"></a>Formattazione  
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Excel.Range> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> . Questo include i bordi, i tipi di carattere, il formato numero e gli stili.  
  
## <a name="renaming-the-control"></a>Ridenominazione del controllo  
 Quando si aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> al foglio di lavoro dalla **Casella degli strumenti**, Visual Studio genera automaticamente un nome per il controllo che può essere modificato nella finestra **Proprietà** .  
  
## <a name="events"></a>Eventi  
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> :  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procedure dettagliate ed esempi di sviluppo di office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  