---
title: "Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d2231f3e6dc6185c97a5a09e4d81db3883e8431
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041889"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato
  Questa procedura dettagliata mostra come creare un riquadro attività personalizzato che consente di automatizzare PowerPoint. Il riquadro attività personalizzato inserisce le date in una diapositiva quando l'utente fa clic su un controllo <xref:System.Windows.Forms.MonthCalendar> che si trova nel riquadro attività personalizzato.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Benché questa procedura dettagliata usi PowerPoint in modo specifico, i concetti illustrati sono applicabili a tutte le applicazioni elencate in precedenza.

 Questa procedura dettagliata illustra le attività seguenti:

- Progettazione dell'interfaccia utente del riquadro attività personalizzato.

- Automazione di PowerPoint dal riquadro attività personalizzato.

- Visualizzazione del riquadro attività personalizzato in PowerPoint.

> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 o [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Creare il progetto di componente aggiuntivo
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per PowerPoint.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di componente aggiuntivo VSTO per PowerPoint denominato **MyAddIn**, usando il modello per il progetto di componente aggiuntivo di PowerPoint. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e aggiunge il progetto **MyAddIn** a **Esplora soluzioni**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Progettare l'interfaccia utente del riquadro attività personalizzato
 Non sono presenti finestre di visualizzazione visiva per i riquadri attività personalizzati, ma è possibile progettare un controllo utente con il layout desiderato. Più avanti in questa procedura dettagliata il controllo utente verrà aggiunto al riquadro attività personalizzato.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Per progettare l'interfaccia utente del riquadro attività personalizzato

1. Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del controllo utente su **MyUserControl**e fare clic su **Aggiungi**.

     Il controllo utente viene visualizzato nella finestra di progettazione.

3. Nella scheda **Controlli comuni** della **casella degli strumenti**trascinare un controllo **MonthCalendar** nel controllo utente.

     Se il controllo **MonthCalendar** è più ampio dell'area di progettazione del controllo utente, ridimensionare il controllo utente per adattare il controllo **MonthCalendar** .

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatizzare PowerPoint dal riquadro attività personalizzato
 Lo scopo del componente aggiuntivo VSTO è inserire una data selezionata nella prima diapositiva della presentazione attiva. Usare l'evento <xref:System.Windows.Forms.MonthCalendar.DateChanged> del controllo per aggiungere la data selezionata ogni volta che viene modificata.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Per automatizzare PowerPoint dal riquadro attività personalizzato

1. Nella finestra di progettazione fare doppio clic sul controllo <xref:System.Windows.Forms.MonthCalendar> .

     Il file **MyUserControl.cs** o **MyUserControl.vb** si apre e viene creato un gestore eventi per l'evento <xref:System.Windows.Forms.MonthCalendar.DateChanged> .

2. Aggiungere il codice seguente all'inizio del file. Questo codice crea gli alias per gli spazi dei nomi <xref:Microsoft.Office.Core> e <xref:Microsoft.Office.Interop.PowerPoint> .

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Aggiungere il codice seguente alla classe `MyUserControl` . Questo codice dichiara un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Shape> come membro di `MyUserControl`. Nel passaggio seguente viene usato <xref:Microsoft.Office.Interop.PowerPoint.Shape> per aggiungere una casella di testo a una diapositiva nella presentazione attiva.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. Sostituire il gestore eventi `monthCalendar1_DateChanged` con il codice seguente. Questo codice aggiunge una casella di testo alla prima diapositiva nella presentazione attiva, quindi aggiunge la data attualmente selezionata alla casella di testo. Questo codice usa l'oggetto `Globals.ThisAddIn` per accedere al modello di oggetto di PowerPoint.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **MyAddIn** , quindi scegliere **Compila**. Verificare che il progetto venga compilato senza errori.

## <a name="display-the-custom-task-pane"></a>Visualizzare il riquadro attività personalizzato
 Per visualizzare il riquadro attività personalizzato quando viene avviato il componente aggiuntivo VSTO, aggiungere il controllo utente al riquadro attività nel gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> del componente aggiuntivo VSTO.

### <a name="to-display-the-custom-task-pane"></a>Per visualizzare il riquadro attività personalizzato

1. In **Esplora soluzioni**espandere **PowerPoint**.

2. Fare clic con il pulsante destro del mouse su **ThisAddIn.cs** o **ThisAddIn.vb** , quindi scegliere **Visualizza codice**.

3. Aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn` .

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. Sostituire il gestore eventi `ThisAddIn_Startup` con il codice seguente. Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes` . Il codice visualizza anche il riquadro attività.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Testare il componente aggiuntivo
 Quando si esegue il progetto, PowerPoint si apre e il componente aggiuntivo VSTO visualizza il riquadro attività personalizzato. Fare clic sul controllo <xref:System.Windows.Forms.MonthCalendar> per testare il codice.

### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro attività personalizzato sia visibile.

3. Fare clic su una data nel controllo <xref:System.Windows.Forms.MonthCalendar> nel riquadro attività.

     La data viene inserita nella prima diapositiva della presentazione attiva.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare i riquadri attività personalizzati, vedere gli argomenti seguenti:

- Creare un riquadro attività personalizzato in un componente aggiuntivo VSTO per un'altra applicazione. Per altre informazioni sulle applicazioni che supportano i riquadri attività personalizzati, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

- Creare un pulsante della barra multifunzione da usare per visualizzare o nascondere un riquadro attività personalizzato. Per altre informazioni, vedere [Procedura dettagliata: Sincronizzare un riquadro attività personalizzato con un pulsante della barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Creare un riquadro attività personalizzato per ogni messaggio di posta elettronica aperto in Outlook. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare i riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Vedere anche
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Procedura dettagliata: Sincronizzare un riquadro attività personalizzato con un pulsante della barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Procedura dettagliata: Visualizzare i riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
