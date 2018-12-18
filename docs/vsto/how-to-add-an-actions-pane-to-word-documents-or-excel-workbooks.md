---
title: 'Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel | Documenti Microsoft'
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d259442104cfbd6b072d0068ab5f2b4f182f027f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel
  Per aggiungere un riquadro azioni a un documento di Microsoft Office Word o una cartella di lavoro di Microsoft Excel, creare innanzitutto un controllo utente Windows Form. Quindi, aggiungere il controllo utente per il <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel) nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Creazione del controllo utente  
 La procedura seguente viene illustrato come creare un controllo utente o un progetto di Excel. Aggiunge anche un pulsante nel controllo utente che scrive il testo nel documento o una cartella di lavoro quando viene selezionato.  
  
#### <a name="to-create-the-user-control"></a>Per creare il controllo utente  
  
1.  Aprire il progetto a livello di documento di Word o Excel in Visual Studio.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **controllo riquadro azioni**, denominarla **HelloControl**, fare clic su **Aggiungi**.  
  
    > [!NOTE]  
    >  In alternativa, è possibile aggiungere un **controllo utente** elemento al progetto. Le classi generate dal **controllo riquadro azioni** e **controllo utente** gli elementi sono funzionalmente equivalenti.  
  
4.  Dal **Windows Form** scheda della finestra di **della casella degli strumenti,** trascinare un **pulsante** controllo sul controllo.  
  
    > [!NOTE]  
    >  Se il controllo non è visibile nella finestra di progettazione, fare doppio clic **HelloControl** in **Esplora**.  
  
5.  Aggiungere il codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del pulsante. Nell'esempio seguente viene illustrato il codice per un documento di Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  In c#, è necessario aggiungere un gestore eventi per il clic del pulsante. È possibile inserire il codice nel `HelloControl` costruttore dopo la chiamata a `IntializeComponent`.  
  
     Per informazioni su come creare gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="adding-the-user-control-to-the-actions-pane"></a>Aggiunta del controllo utente al riquadro azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo utente per il <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel).  
  
#### <a name="to-add-the-user-control-to-the-actions-pane"></a>Per aggiungere il controllo utente al riquadro azioni  
  
1.  Aggiungere il codice seguente per il `ThisDocument` o `ThisWorkbook` classe come una dichiarazione a livello di classe (non aggiungere questo codice a un metodo).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Aggiungere il codice seguente per il `ThisDocument_Startup` gestore dell'evento del `ThisDocument` classe o `ThisWorkbook_Startup` gestore dell'evento del `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura dettagliata: Inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro Azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  