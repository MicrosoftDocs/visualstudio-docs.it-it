---
title: 'Procedura: Ridimensionare i controlli ListObject'
description: Informazioni su come usare le Visual Studio ridimensionare a livello di codice i controlli ListObject in una cartella di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a2fd0b8ce46ba15066ab4cf070807e2457c21e70
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828956"
---
# <a name="how-to-resize-listobject-controls"></a>Procedura: Ridimensionare i controlli ListObject
  Impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> quando lo si aggiunge a una cartella di lavoro di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito. Ad esempio, potrebbe essere necessario cambiare un elenco a due colonne in uno a tre colonne.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile ridimensionare controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di progettazione oppure in fase di esecuzione in progetti a livello di documento. È possibile <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionare i controlli in fase di esecuzione in un progetto di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Ridimensionare i controlli ListObject in fase di progettazione](#designtime)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per altre informazioni sui <xref:Microsoft.Office.Tools.Excel.ListObject> controlli, vedere [Controllo ListObject.](../vsto/listobject-control.md)

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Ridimensionare un controllo ListObject in fase di progettazione
 Per ridimensionare un elenco, è possibile selezionare e trascinare uno dei punti di controllo oppure è possibile ridefinirne la dimensione nella finestra di dialogo **Ridimensiona elenco** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Per ridimensionare un elenco usando la finestra di dialogo Ridimensiona elenco

1. Fare clic in un punto qualsiasi della  <xref:Microsoft.Office.Tools.Excel.ListObject> tabella. Verrà **visualizzata la scheda** Progettazione di  >  **Strumenti** tabella nella barra multifunzione.

2. Nella sezione Proprietà fare clic su **Ridimensiona tabella**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Selezionare il nuovo intervallo di dati per la tabella.

4. Fare clic su **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ridimensionare un controllo ListObject in fase di esecuzione in un progetto a livello di documento
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione usando il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Non è possibile usare questo metodo per spostare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in una nuova posizione nel foglio di lavoro. Le intestazioni devono rimanere nella stessa riga e il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve sovrapporsi all'oggetto elenco originale. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve contenere una riga di intestazione e almeno una riga di dati.

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet6":::

2. Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ridimensionare un ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un controllo a un foglio di lavoro usando un componente aggiuntivo VSTO, vedere Procedura: Aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> [ListObject ai fogli di lavoro.](../vsto/how-to-add-listobject-controls-to-worksheets.md)

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet12":::

2. Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word e cartelle di lavoro di Excel nei componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Excel tramite oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Controllo ListObject](../vsto/listobject-control.md)
- [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Ridimensionare i controlli Segnalibro](../vsto/how-to-resize-bookmark-controls.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
