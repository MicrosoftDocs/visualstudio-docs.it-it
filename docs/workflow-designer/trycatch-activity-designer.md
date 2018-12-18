---
title: ActivityDesigner TryCatch | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae4cd4340bc30249ea649a2806afe3e027fc439
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="trycatch-activity-designer"></a>ActivityDesigner TryCatch
Il **TryCatch** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TryCatch> attività.

## <a name="the-trycatch-activity"></a>Attività TryCatch
 Il <xref:System.Activities.Statements.TryCatch> attività contiene un <xref:System.Activities.Statements.TryCatch.Try%2A> attività, una raccolta di **Catch\<TException >** e <xref:System.Activities.Statements.TryCatch.Finally%2A> attività. Oggetto <xref:System.Activities.Statements.Catch%601> di tipo **TException** contiene un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e <xref:System.Activities.Statements.Catch%601.Action%2A>. che vengono usate insieme per implementare un meccanismo tipico di gestione degli errori basato sulle eccezioni. Un'attività <xref:System.Activities.Statements.TryCatch> tenta di eseguire la relativa attività <xref:System.Activities.Statements.TryCatch.Try%2A>. Se il <xref:System.Activities.Statements.TryCatch.Try%2A> attività genera un'eccezione, il <xref:System.Activities.Statements.TryCatch> attività utilizza la **Catch < TException\>**  insieme in modo che corrisponda all'eccezione. Se esiste una corrispondenza, la <xref:System.Activities.Statements.Catch%601.Action%2A> dei corrispondenti **Catch\<TException >** viene eseguita, che funge da logica per l'eccezione di gestione degli errori. Se le attività nella sezione di <xref:System.Activities.Statements.TryCatch.Try%2A> o le attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> terminano in modo corretto, l'attività di <xref:System.Activities.Statements.TryCatch> esegue la relativa attività di <xref:System.Activities.Statements.TryCatch.Finally%2A>. Per ulteriori informazioni, vedere [le eccezioni del flusso di lavoro di Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Utilizzo dell'ActivityDesigner TryCatch
 Il **TryCatch** ActivityDesigner è reperibile nel **Error Handling** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **TryCatch** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TryCatch> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito TryCatch. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **TryCatch** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. Le altre proprietà deve essere modificata nell'area del **TryCatch** ActivityDesigner.

 Fare clic sul pulsante di espansione nell'angolo superiore destro della **TryCatch** progettazione per visualizzare il **provare**, **intercetta**, e **infine** caselle il visualizzazione espansa. Per aggiungere un blocco catch, fare clic su di **Aggiungi nuovo catch** pulsante **TryCatch** finestra di progettazione. Il pulsante diventa una casella combinata del tipo. Selezionare un tipo di eccezione e premere INVIO per aggiungere il catch. Dopo aver aggiunto un **Catch**, l'area dei catch si espande e può essere rilasciare un'attività nel catch in modo da definire la logica di esecuzione. Si noti la presenza di una casella di testo a destra dell'area dei catch espansa. Questa casella consente di assegnare un nome alla variabile dell'eccezione. La variabile dell'eccezione utilizzabile solo per le attività all'interno dello stesso **Catch**.

 Il **TryCatch** finestra di progettazione non supporta la modifica **Catch**. Se si desidera modificare il tipo di eccezione, è necessario eliminare il **Catch** e aggiungerne uno nuovo. A **Catch** può essere eliminato selezionandolo e l'eliminazione o utilizzando il **eliminare** menu nel menu di scelta rapida facendo clic destro del mouse.

### <a name="the-trycatch-properties"></a>Proprietà di TryCatch
 La tabella seguente mostra la <xref:System.Activities.Statements.TryCatch>proprietà e viene descritto come vengono utilizzati nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TryCatch>. Il percorso predefinito è TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|L'attività è stata eseguita per prima quando viene eseguito <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|La raccolta di **Catch** elementi da verificare quando il <xref:System.Activities.Statements.TryCatch.Try%2A> attività genera un'eccezione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|L'attività da eseguire quando <xref:System.Activities.Statements.TryCatch.Try%2A> e qualsiasi attività necessaria nella raccolta <xref:System.Activities.Statements.TryCatch.Catches%2A> completano l'esecuzione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)