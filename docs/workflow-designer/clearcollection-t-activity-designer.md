---
title: ClearCollection&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 54cac37194a3b96d464b886c14bfbbbde4a1f861
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; ActivityDesigner
Il **ClearCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.ClearCollection%601> attività.  
  
## <a name="the-clearcollectiont-activity"></a>Il ClearCollection < T\> attività  
 L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>Utilizzo di ClearCollection\<T > ActivityDesigner  
 Il **ClearCollection\<T >** ActivityDesigner è reperibile nel **raccolta** categoria del **della casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda della finestra il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)  
  
 Il **ClearCollection\<T >** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.ClearCollection%601> attività con valore predefinito è <xref:System.Activities.Activity.DisplayName%2A> clearcollection < Int32\>. (Per impostazione predefinita, il *TypeArgument* è **Int32**. Tale valore può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **ClearCollection < T\>**  ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### <a name="the-clearcollectiont-properties"></a>Il ClearCollection < T\> proprietà  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>. Il valore predefinito è ClearCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Specifica la raccolta di cui cancellare tutti gli elementi. Questa raccolta è di tipo **ICollection\<TypeArgument >.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *TypeArgument* tipo è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)