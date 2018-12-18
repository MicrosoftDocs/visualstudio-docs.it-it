---
title: 'Procedura: nascondere i controlli nei fogli di lavoro durante la stampa | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d02d823e707054fd17a5f3f892db41258b08081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Procedura: nascondere i controlli contenuti nei fogli di lavoro durante la stampa
  Quando si stampa un documento di Microsoft Office Excel che contiene controlli Windows Form, i controlli sono visibili nel foglio di lavoro. È possibile nascondere i controlli durante la stampa di un foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Se si nascondono i controlli che visualizzano i dati, ad esempio un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, i dati nel controllo non sarà visibili nel foglio di lavoro.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Per nascondere i controlli di quando un foglio di lavoro viene stampato  
  
1.  Creare o aprire un progetto di Excel in Visual Studio e verificare che **Sheet1** è visibile nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dal **controlli comuni** scheda della finestra il **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.Button> il controllo a una cella in `Sheet1`.  
  
3.  Nel **proprietà** finestra, impostare il <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> proprietà **False**.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  