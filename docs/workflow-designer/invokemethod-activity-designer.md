---
title: ActivityDesigner InvokeMethod | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1fe242e3e4fd2a885373d776f79f50071fa83c1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="invokemethod-activity-designer"></a>ActivityDesigner InvokeMethod
**InvokeMethod** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeMethod> attività.  
  
## <a name="the-invokemethod-activity"></a>Attività InvokeMethod  
 L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.  
  
### <a name="using-the-invokemethod-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeMethod  
 Il **InvokeMethod** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)  
  
 Il **InvokeMethod** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area in cui le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeMethod> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeMethod. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeMethod** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.  
  
### <a name="the-invokemethod-properties"></a>Proprietà di InvokeMethod  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeMethod> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>. Il valore predefinito è InvokeMethod.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nome del metodo da richiamare quando viene eseguita l'attività. Il metodo chiamato deve essere dichiarato come **pubblica**. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Raccolta di parametri del metodo chiamato. I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo. Nella griglia delle proprietà, fare clic sul pulsante con puntini di sospensione di **parametri** campo, viene visualizzato il **parametri** finestra di dialogo che consente di impostare questa proprietà. Fare clic su di **Crea argomento** pulsante per aggiungere i parametri.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valore restituito dalla chiamata del metodo.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Specifica se il metodo viene chiamato in modo asincrono. Il valore predefinito è **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Oggetto contenente il metodo da chiamare. È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo di <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. È possibile modificare questa proprietà nell'area della finestra di progettazione. È necessario impostare questa proprietà solo se il metodo chiamato è statico.|  
  
 Per passare i parametri come c# **out** parametro (ad esempio, `Method1(out myParam)),` si consiglia di utilizzare **OutArgument** anziché **InOutArgument**  
  
 I metodi con argomenti chiamati **TargetObject** o **risultato** non può essere richiamato usando il <xref:System.Activities.Statements.InvokeMethod> attività. Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:  
  
1.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.  
  
 L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> e presenta il messaggio seguente: 'InvokeMethod': Esiste già una variabile, RuntimeArgument o DelegateArgument con il nome 'TargetObject'. I nomi devono essere univoci in un ambito di ambiente.  
  
 Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> perché non sono argomenti del flusso di lavoro e pertanto non sono registrati nella raccolta <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> dell'attività <xref:System.Activities.Statements.InvokeMethod> nel metodo <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assegnare](../workflow-designer/assign-activity-designer.md)   
 [Ritardo](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)