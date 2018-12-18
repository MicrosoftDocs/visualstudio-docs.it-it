---
title: ExistsInCollection&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6175fdc9c0af417acb8bcfe9d4297172b31a2e3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; ActivityDesigner
Il **ExistsInCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.ExistsInCollection%601> attività.

## <a name="the-existsincollectiont-activity"></a>Il ExistsInCollection < T\> attività
 L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.

### <a name="using-the-existsincollectiont-activity-designer"></a>Utilizzo di ExistsInCollection\<T > ActivityDesigner
 Il **ExistsInCollection\<T >** ActivityDesigner è reperibile nel **raccolta** categoria del **della casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **ExistsInCollection\<T >** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.ExistsInCollection%601> attività con valore predefinito è <xref:System.Activities.Activity.DisplayName%2A> existsincollection < Int32\>. (Per impostazione predefinita, il *TypeArgument* è **Int32**. Tale valore può essere modificato nella griglia delle proprietà.  Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **ExistsInCollection < T\>**  ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-existsincollectiont-properties"></a>Il ExistsInCollection < T\> proprietà
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ExistsInCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. Il valore predefinito è ExistsInCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Elemento da aggiungere alla raccolta\<T >. Questo elemento è di tipo *T* è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection < TypeArgument\>.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *TypeArgument* tipo è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)