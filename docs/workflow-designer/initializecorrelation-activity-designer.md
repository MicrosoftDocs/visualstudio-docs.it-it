---
title: ActivityDesigner InitializeCorrelation | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72778ac3757cc259019df5fb5616115f41ce0c34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation
Il **InitializeCorrelation** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività che viene usato per stabilire una correlazione tra i messaggi prima dell'invio e ricezione.

## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation
 Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation
 Il **InitializeCorrelation** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **InitializeCorrelation** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area. Crea un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività con valore predefinito è <xref:System.Activities.Activity.DisplayName%2A> di InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InitializeCorrelation** ActivityDesigner o nel  **DisplayName** casella della finestra di **proprietà** finestra.

 Il <xref:System.ServiceModel.Activities.CorrelationHandle> può essere specifica nel **correlazione** campo **proprietà** finestra il **InitializeCorrelation** superficie dell'ActivityDesigner.

 Fare clic sul pulsante ellisse oltre il **CorrelationData** campo **proprietà** finestra o il testo di suggerimento "Vista …" nel **InitializeCorrelation** ActivityDesigner superficie di attacco consente di visualizzare il **Inizializza correlazione** la finestra di dialogo in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore utilizzate per l'inizializzazione. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere il [finestra di dialogo Editor dell'insieme di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.

### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella **proprietà** finestra oppure [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare il **Inizializza correlazione** la finestra di dialogo per configurare il <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo, vedere il [finestra di dialogo Editor dell'insieme di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.|

## <a name="see-also"></a>Vedere anche

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Ricezione](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Invia](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)