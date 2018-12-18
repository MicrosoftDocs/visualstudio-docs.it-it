---
title: Eseguire il binding a un'attività&#39;finestra di dialogo proprietà s (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a799b57169116343f5d83e54ce5bd87dedfd801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Eseguire il binding a un'attività&#39;finestra di dialogo proprietà s (Legacy)
Questo argomento viene descritto come utilizzare il **associare alla proprietà di un'attività** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Un tipo di istanza di proprietà di dipendenza può essere associato alla proprietà pubblica di un'altra attività o evento. Per ulteriori informazioni sull'associazione di attività, vedere [utilizzando le proprietà di dipendenza](http://go.microsoft.com/fwlink?LinkID=65007).

 Si seleziona una proprietà da associare usando la **associare alla proprietà di un'attività** la finestra di dialogo. Si apre questa finestra di dialogo facendo clic sui puntini di sospensione **[…]**  alla fine della casella di testo della proprietà selezionata nel **proprietà** finestra, oppure facendo clic sull'icona di punto esclamativo blu visualizzata accanto al nome di proprietà nel Visualizzatore proprietà.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **associare alla proprietà di un'attività** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Associare a un membro esistente**|Selezionare un membro che si desidera associare nel riquadro di visualizzazione albero. Il riquadro al di sotto della visualizzazione albero visualizza un messaggio che indica se il membro è un tipo valido per l'associazione o no. Fare clic su **OK** da associare al membro valido selezionato.|
|**Associa a un nuovo membro**|Creare un campo o una proprietà per il membro nuovo da associare. Immettere un **nuovo nome di membro**. Scegliere se si desidera creare una proprietà di dipendenza o un campo pubblico selezionando **Crea campo** o **crea proprietà**. Fare clic su **OK** per creare il nuovo membro.|

## <a name="see-also"></a>Vedere anche

- [Utilizzando le proprietà dell'attività](http://go.microsoft.com/fwlink?LinkID=65013)
- [Utilizzando proprietà di dipendenza](http://go.microsoft.com/fwlink?LinkID=65007)
- [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)