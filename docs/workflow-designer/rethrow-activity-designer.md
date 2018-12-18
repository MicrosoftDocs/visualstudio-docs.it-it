---
title: ActivityDesigner rethrow | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28982b16f9eebcaf34eba900303b92eaef870e31
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow
Il **Rethrow** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Rethrow> attività.

## <a name="the-rethrow-activity"></a>Attività Rethrow
 L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilizzo dell'ActivityDesigner ReThrow
 Il **Rethrow** ActivityDesigner è reperibile nel **Error Handling** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **Rethrow** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Rethrow> attività con valore predefinito è **DisplayName** throw. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **Rethrow** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Rethrow> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)