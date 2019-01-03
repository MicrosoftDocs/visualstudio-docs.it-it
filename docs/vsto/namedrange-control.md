---
title: NamedRange (controllo)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: f23da0d6e91e63eaab9cd1153f07727b6399b375
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871885"
---
# <a name="namedrange-control"></a>NamedRange (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è un intervallo con un nome univoco che espone gli eventi e può essere associato ai dati. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Creare il controllo  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione o in fase di esecuzione nei progetti a livello di documento.  
  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO. Per altre informazioni, vedere [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Per impostazione predefinita, gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 I controlli<xref:Microsoft.Office.Tools.Excel.NamedRange> possono essere costituiti solo da intervalli in fogli specifici. I controlli<xref:Microsoft.Office.Tools.Excel.NamedRange> non possono avere nomi relativi che si applicano a tutti i fogli e non possono essere costituiti da intervalli estesi a due o più fogli di lavoro di una cartella di lavoro (intervalli 3D).  
  
## <a name="bind-data-to-the-control"></a>Associare dati al controllo  
 Un intervallo denominato può sembrare il candidato ideale per il data binding complesso, dal momento che può includere diverse celle. Un intervallo è però semplicemente una raccolta di celle di cui non è possibile eseguire facilmente il mapping a una determinata colonna particolare di un set di dati. Di conseguenza, i controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> supportano solo il data binding semplici. Per il data binding complesso è possibile usare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> . Per altre informazioni, vedere [ListObject control](../vsto/listobject-control.md).  
  
 È possibile associare il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un'origine dati usando le proprietà <xref:System.Windows.Forms.Control.DataBindings%2A> . La proprietà di data binding predefinita del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> è <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> rispecchia le modifiche.  
  
## <a name="formatting"></a>Formattazione  
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Excel.Range> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> . Questo include i bordi, i tipi di carattere, formati di numero e gli stili.  
  
## <a name="rename-the-control"></a>Rinominare il controllo  
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
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
