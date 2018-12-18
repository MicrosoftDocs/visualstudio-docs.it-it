---
title: "Procedura dettagliata: Creare un'attività flusso di lavoro sito personalizzato | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b723635b1baecfec4bddb2339414d57803c76d5d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procedura dettagliata: creare un'attività personalizzata per un flusso di lavoro del sito
  Questa procedura dettagliata viene illustrato come creare un'attività personalizzata per un flusso di lavoro a livello di sito utilizzando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Flussi di lavoro a livello di sito si applicano all'intero sito, non solo un elenco nel sito). L'attività personalizzata consente di creare un elenco di annunci di backup e quindi copia il contenuto dell'elenco di annunci al suo interno.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un flusso di lavoro a livello di sito.  
  
-   Creazione di un'attività flusso di lavoro personalizzato.  
  
-   Creazione ed eliminazione di un elenco di SharePoint.  
  
-   Copia gli elementi da un elenco a altro.  
  
-   Visualizzazione di un elenco sulla barra Avvio veloce.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Le edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>Creazione di un progetto di attività personalizzata flusso di lavoro del sito  
 Creare innanzitutto un progetto per gestire e testare l'attività flusso di lavoro personalizzato.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Per creare un progetto di attività personalizzata flusso di lavoro del sito  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **progetto** per visualizzare il **nuovo progetto** la finestra di dialogo.  
  
2.  Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.  
  
4.  Nel **nome** immettere **AnnouncementBackup**, quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
5.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di livello e predefinito attendibile.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro.  
  
6.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
7.  In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
8.  Nel **modelli** riquadro, scegliere il **flusso di lavoro sequenziale (solo soluzione Farm)** , modello e quindi scegliere il **Aggiungi** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
9. Nel **specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (AnnouncementBackup - Workflow1). Modificare il tipo di modello del flusso di lavoro in **flusso di lavoro sito**, quindi scegliere il **Avanti** pulsante.  
  
10. Scegliere il **fine** pulsante per accettare le impostazioni predefinite rimanenti.  
  
## <a name="adding-a-custom-workflow-activity-class"></a>Aggiunta di una classe di attività del flusso di lavoro personalizzato  
 Successivamente, aggiungere una classe al progetto contenente il codice per l'attività flusso di lavoro personalizzato.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Per aggiungere una classe di attività del flusso di lavoro personalizzato  
  
1.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento** per visualizzare il **Aggiungi nuovo elemento** la finestra di dialogo.  
  
2.  Nel **modelli installati** visualizzazione ad albero, scegliere il **codice** nodo, quindi scegliere il **classe** modello nell'elenco dei modelli di elemento di progetto. Utilizzare il nome predefinito Class1. Scegliere il pulsante **Aggiungi**.  
  
3.  Sostituire tutto il codice in Class1 con quanto segue:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Salvare il progetto e quindi nella barra dei menu scegliere **compilare**, **Compila soluzione**.  
  
     Class1 viene visualizzato come un'azione personalizzata nel **della casella degli strumenti** sul **componenti AnnouncementBackup** scheda.  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>Aggiunta dell'attività personalizzata al flusso di lavoro del sito  
 Successivamente, aggiungere un'attività al flusso di lavoro contenente il codice personalizzato.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Per aggiungere un'attività personalizzata per il sito del flusso di lavoro  
  
1.  Aprire Workflow1 nella finestra di progettazione del flusso di lavoro nella visualizzazione progettazione.  
  
2.  Trascinare Class1 dal **della casella degli strumenti** in modo che venga visualizzata sotto il `onWorkflowActivated1` attività oppure aprire il menu di scelta rapida per Class1, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il `onWorkflowActivated1` attività, quindi scegliere **Incolla**.  
  
3.  Salvare il progetto.  
  
## <a name="testing-the-site-workflow-custom-activity"></a>L'attività personalizzata del flusso di lavoro del sito di test  
 Successivamente, eseguire il progetto e avviare il flusso di lavoro del sito. L'attività personalizzata crea un elenco di annunci di backup e copia il contenuto dell'elenco di annunci corrente al suo interno. Il codice verifica inoltre se esiste già un elenco di backup prima di crearne uno nuovo. Se esiste già un elenco di backup, questo viene eliminato. Viene inoltre aggiunto un collegamento per il nuovo elenco sulla barra Avvio veloce del sito di SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Per testare l'attività personalizzata del flusso di lavoro del sito  
  
1.  Premere il tasto F5 per eseguire il progetto e distribuirlo in SharePoint.  
  
2.  Nella barra Avvio veloce scegliere il **Elenca** link per visualizzare tutti gli elenchi che sono disponibili nel sito di SharePoint. Si noti non è presente un solo elenco per gli annunci denominato **annunci**.  
  
3.  Nella parte superiore della pagina Web di SharePoint, scegliere il **flussi di lavoro sito** collegamento.  
  
4.  In Inizio sezione un nuovo flusso di lavoro, scegliere il **AnnouncementBackup - Workflow1** collegamento. Questo viene avviato il flusso di lavoro del sito e si esegue il codice dell'azione personalizzata.  
  
5.  Nella barra Avvio veloce scegliere il **Backup annunci** collegamento. Si noti che tutti gli annunci presenti nel **annunci** elenco sono stati copiati in questo nuovo elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  