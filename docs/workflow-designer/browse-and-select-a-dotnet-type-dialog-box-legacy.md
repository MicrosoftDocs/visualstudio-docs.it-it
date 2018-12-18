---
title: Individuare e selezionare una casella di dialogo tipo .NET (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a283caa664bb208613a695cb4afb8873caba3645
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Finestra di dialogo Cerca e seleziona un tipo .NET (legacy)
Questo argomento viene descritto come utilizzare il **Cerca e seleziona un tipo .NET** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Nel **proprietà** finestra, quando si selezionano le proprietà che accettano un tipo .NET Framework in un assembly di riferimento, i puntini di sospensione **[…]**  visualizzata alla fine della casella di testo della proprietà. Fare clic su di **[…]**  apre il **Cerca e seleziona un tipo .NET** la finestra di dialogo. In questa finestra di dialogo, è possibile scegliere un tipo dalla visualizzazione albero degli assembly a cui si fa riferimento. Ad esempio, quando si utilizza la finestra di progettazione di attività, nel **proprietà** finestra, fare clic sul **di una classe Base** i puntini di sospensione **[…]**  per selezionare un'altra classe di base per un'attività dall'albero assembly a cui fa riferimento.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Cerca e seleziona un tipo .NET** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Nome tipo:**|Nome del tipo correntemente selezionato.|
|**Type**|Nel riquadro sinistro è presente una visualizzazione albero degli Assembly a cui si fa riferimento. Nel riquadro di destra vengono visualizzati i tipi disponibili per la selezione dall’Assembly cui si fa riferimento selezionato nel riquadro sinistro.|

## <a name="see-also"></a>Vedere anche

- [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)