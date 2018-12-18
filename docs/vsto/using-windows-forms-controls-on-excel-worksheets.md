---
title: Utilizzo di Windows Form controlli nei fogli di lavoro di Excel | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4c754c0fff7f7a0f5c3bf31293696e3ec57961f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Utilizzo di controlli Windows Form nei fogli di lavoro di Excel
  È possibile aggiungere controlli Windows Form per le cartelle di lavoro di Microsoft Office Excel nello stesso modo aggiungere controlli a un Windows Form. Per informazioni generali sull'utilizzo dei controlli nei documenti, vedere [controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Considerazioni sui controlli per Excel  
 Esistono alcune considerazioni specifiche di Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Corrispondenza delle dimensioni del controllo e la dimensione della cella  
 È possibile impostare il ridimensionamento automatico del controllo quando vengono modificate le dimensioni della cella padre. Per ulteriori informazioni, vedere [procedura: ridimensionare i controlli all'interno di celle di foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Aggiunta di componenti condivisi da tutti i fogli di lavoro  
 I componenti da condividere in tutti i fogli di lavoro, ad esempio un oggetto <xref:System.Data.DataSet>, possono essere aggiunti alla finestra di progettazione delle cartelle di lavoro anziché ai fogli di lavoro. Il componente verrà visualizzato nella barra dei componenti.  
  
### <a name="formula-for-embedding-controls"></a>Formula per l'incorporamento di controlli  
 Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Procedura: nascondere controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procedura dettagliata: Modifica della formattazione di foglio di lavoro mediante i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procedura dettagliata: Visualizzazione di testo in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  