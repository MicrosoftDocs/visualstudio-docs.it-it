---
title: 'Procedura: gestire il Layout dei controlli nei riquadri azioni | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0831740c612e4e9d4eddd47a0648302e9460f060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procedura: gestire il layout di controllo dei riquadri delle azioni
  Un riquadro azioni è ancorato a destra di un documento o foglio di lavoro per impostazione predefinita. Tuttavia, può essere ancorato a sinistra, superiore o inferiore. Se si usano più controlli utente, è possibile scrivere codice per sovrapporre correttamente i controlli nel riquadro azioni. Per altre informazioni, vedere [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'ordine dei controlli dipende se il riquadro azioni è ancorato orizzontalmente o verticalmente.  
  
> [!NOTE]  
>  Se l'utente ridimensiona il riquadro delle azioni in fase di esecuzione, è possibile impostare i controlli per ridimensionare il riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. Per ulteriori informazioni, vedere [procedura: ancorare i controlli in Windows Form](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Per impostare l'ordine dello stack dei controlli riquadro azioni  
  
1.  Aprire un progetto a livello di documento per Microsoft Office Word che include un riquadro azioni con più controlli utente o i controlli del riquadro azioni annidati. Per ulteriori informazioni, vedere [procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Fare doppio clic su **ThisDocument. cs** o **ThisDocument. vb** in **Esplora** e quindi fare clic su **Visualizza codice**.  
  
3.  Nel <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> gestore eventi del riquadro azioni, verificare se l'orientamento del riquadro azioni è orizzontale.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Se l'orientamento orizzontale, stack i controlli riquadro azioni da sinistra. in caso contrario, li stack dall'alto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  In c#, è necessario aggiungere un gestore eventi per il `ActionsPane` per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Eseguire il progetto e verificare che i controlli riquadro azioni siano impilati da sinistra a destra quando il riquadro azioni è ancorato nella parte superiore del documento e i controlli sono impilati dall'alto verso il basso per il riquadro azioni è ancorato a destra del documento.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Controlli di un progetto a livello di documento di Word con un riquadro delle azioni che contiene più controlli utente o un riquadro azioni annidati.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura dettagliata: Inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro Azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  