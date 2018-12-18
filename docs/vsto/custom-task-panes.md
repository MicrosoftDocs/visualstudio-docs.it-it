---
title: "Riquadri attività personalizzati | Documenti Microsoft"
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
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a99fd7cc89190a8360341684dee91a7cf93f0e0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="custom-task-panes"></a>Riquadri attività personalizzati
  I riquadri attività sono pannelli dell'interfaccia utente in genere ancorati a un lato di una finestra in un'applicazione di Microsoft Office. I riquadri attività personalizzati consentono di creare un riquadro attività basato sulle proprie esigenze specifiche e offrono agli utenti un'interfaccia utente nota per accedere alle funzionalità della soluzione. L'interfaccia può, ad esempio, contenere controlli che consentono di eseguire codice per la modifica dei documenti o per la visualizzazione dei dati di un'origine dati.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Un riquadro attività personalizzato è diverso da un riquadro azioni. Il riquadro azioni fa parte delle personalizzazioni a livello di documento per Microsoft Office Word e Microsoft Office Excel. Per altre informazioni, vedere [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Vantaggi dei riquadri attività personalizzati  
 I riquadri attività personalizzati consentono di integrare le funzionalità in un'interfaccia utente familiare. È possibile creare rapidamente un riquadro attività personalizzato usando gli strumenti di Visual Studio.  
  
### <a name="familiar-user-interface"></a>Interfaccia utente familiare  
 Gli utenti delle applicazioni di Microsoft Office hanno già familiari con l'uso dei riquadri attività, ad esempio il **stili e formattazione** riquadro attività in Word. I riquadri attività personalizzati presentano un funzionamento simile a quello di altri riquadri attività di Microsoft Office. Gli utenti possono ancorare i riquadri attività personalizzati a diversi lati della finestra dell'applicazione oppure possono trascinare i riquadri attività personalizzati in qualsiasi posizione all'interno della finestra. È possibile creare un componente aggiuntivo VSTO in grado di visualizzare più riquadri attività personalizzati allo stesso tempo, garantendo agli utenti la possibilità di controllare ogni riquadro attività singolarmente.  
  
### <a name="windows-forms-support"></a>Supporto di Windows Form  
 L'interfaccia utente di un riquadro attività personalizzato creato mediante gli strumenti di sviluppo di Office in Visual Studio si basa sui controlli Windows Form. È possibile usare il noto strumento Progettazione Windows Form per progettare l'interfaccia utente per un riquadro attività personalizzato. È inoltre possibile usare il supporto del data binding dei Windows Form per associare un'origine dati ai controlli del riquadro attività.  
  
## <a name="creating-a-custom-task-pane"></a>Creazione di un riquadro attività personalizzato  
 È possibile creare un riquadro attività personalizzato di base in due passaggi:  
  
1.  Creare un'interfaccia utente per il riquadro attività personalizzato aggiungendo controlli Windows Form a un oggetto <xref:System.Windows.Forms.UserControl>.  
  
2.  Creare un'istanza del riquadro attività personalizzato passando il controllo utente all'oggetto <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> nel componente aggiuntivo VSTO. Questa raccolta restituisce un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> che può essere usato per modificare l'aspetto del riquadro attività e per rispondere agli eventi utente.  
  
 Per ulteriori informazioni, vedere [procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="creating-the-user-interface"></a>Creazione dell'interfaccia utente  
 Tutti i riquadri attività personalizzati creati tramite gli strumenti di sviluppo di Office in Visual Studio contengono un oggetto <xref:System.Windows.Forms.UserControl>. Tale controllo utente fornisce l'interfaccia utente del riquadro attività personalizzato e può essere creato in fase di progettazione o di esecuzione. Se viene creato in fase di progettazione, è possibile usare Progettazione Windows Form per costruire l'interfaccia utente del riquadro attività.  
  
### <a name="instantiating-the-custom-task-pane"></a>Creazione di un'istanza del riquadro attività personalizzato  
 Dopo aver creato un controllo utente contenente l'interfaccia utente del riquadro attività personalizzato, è necessario creare un'istanza di un oggetto <xref:Microsoft.Office.Tools.CustomTaskPane>. A questo scopo, passare il controllo utente all'oggetto <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> nel componente aggiuntivo VSTO chiamando uno dei metodi <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>. Tale raccolta viene esposta come campo `CustomTaskPanes` della classe `ThisAddIn`. Per usare l'esempio di codice seguente è necessario eseguirlo dalla classe `ThisAddIn`.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 I metodi <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> restituiscono un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane>, che può essere usato per modificare l'aspetto del riquadro attività e per rispondere agli eventi utente.  
  
### <a name="controlling-the-task-pane-in-multiple-windows"></a>Controllo del riquadro attività in più finestre  
 I riquadri attività personalizzati sono associati a una finestra cornice di documento che presenta all'utente una visualizzazione di un documento o di un elemento. Il riquadro attività è visibile solo quando la finestra associata è visibile.  
  
 Per determinare quale finestra visualizza il riquadro attività personalizzato, usare l'overload del metodo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> appropriato quando si crea il riquadro attività:  
  
-   Per associare il riquadro attività alla finestra attiva, usare il metodo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
-   Per associare il riquadro attività a un documento ospitato da una finestra specifica, usare il metodo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
 Alcune applicazioni di Office richiedono istruzioni esplicite su quando creare o visualizzare il riquadro attività nei casi in cui siano aperte più finestre. In questi casi è importante prendere in considerazione il punto del codice in cui creare un'istanza del riquadro attività personalizzato per garantire che il riquadro attività visualizzato contenga i documenti o gli elementi appropriati dell'applicazione. Per ulteriori informazioni, vedere [la gestione dei riquadri attività personalizzati nelle finestre dell'applicazione](#Managing).  
  
## <a name="accessing-the-application-from-the-task-pane"></a>Accesso all'applicazione dal riquadro attività  
 Per automatizzare l'applicazione dal controllo utente, è possibile accedere direttamente al modello a oggetti usando la classe `Globals.ThisAddIn.Application` nel codice. La classe statica `Globals` consente di accedere all'oggetto `ThisAddIn`. Il campo `Application` di questo oggetto rappresenta il punto di ingresso nel modello a oggetti dell'applicazione.  
  
 Per ulteriori informazioni sul `Application` campo il `ThisAddIn` , vedere [programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md). Per una procedura dettagliata che illustri come automatizzare un'applicazione da un riquadro attività personalizzato, vedere [procedura dettagliata: automazione di un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Per ulteriori informazioni sul `Globals` classe, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="managing-the-user-interface-of-the-task-pane"></a>Gestione dell'interfaccia utente del riquadro attività  
 Dopo aver creato il riquadro attività è possibile usare le proprietà e gli eventi dell'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> per controllare l'interfaccia utente del riquadro attività e per definire il comportamento in risposta alle modifiche apportate dall'utente al riquadro attività.  
  
### <a name="making-the-custom-task-pane-visible"></a>Rendere visibile il riquadro attività personalizzato  
 Per impostazione predefinita, il riquadro attività non è visibile. Per rendere visibile il riquadro attività, è necessario impostare il <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> proprietà **true**.  
  
 Gli utenti possono chiudere un riquadro attività in qualsiasi momento facendo clic di **chiudere** pulsante (X) nell'angolo del riquadro attività. Non esiste, tuttavia, una modalità predefinita per riaprire il riquadro attività personalizzato. Se un utente chiude un riquadro attività personalizzato, potrà visualizzarlo di nuovo solo se viene fornito uno strumento che consente di eseguire tale operazione.  
  
 Se si crea un riquadro attività personalizzato nel componente aggiuntivo VSTO, è consigliabile creare anche un elemento dell'interfaccia utente, ad esempio un pulsante, selezionabile dagli utenti per visualizzare o nascondere il riquadro stesso. Se il riquadro attività personalizzato viene creato in un'applicazione di Microsoft Office che supporta la personalizzazione della barra multifunzione, è possibile aggiungere un gruppo di controlli alla barra multifunzione contenente un pulsante che consente di visualizzare o nascondere il riquadro attività personalizzato. Per una procedura dettagliata che illustra come eseguire questa operazione, vedere [procedura dettagliata: sincronizzazione di un riquadro attività personalizzato con un pulsante della barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Se si crea un riquadro attività personalizzato in un'applicazione di Microsoft Office che non supporta la personalizzazione della barra multifunzione, è possibile aggiungere un oggetto <xref:Microsoft.Office.Core.CommandBarButton> che consente di visualizzare o nascondere tale riquadro.  
  
### <a name="modifying-the-appearance-of-the-task-pane"></a>Modifica dell'aspetto del riquadro attività  
 È possibile controllare le dimensioni e la posizione di un riquadro attività personalizzato usando le proprietà dell'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane>, nonché apportare molte altre modifiche all'aspetto del riquadro attività usando le proprietà dell'oggetto <xref:System.Windows.Forms.UserControl> contenuto nel riquadro stesso. È possibile, ad esempio, specificare un'immagine di sfondo per un riquadro attività personalizzato usando la proprietà <xref:System.Windows.Forms.Control.BackgroundImage%2A> del controllo utente.  
  
 Nella tabella seguente sono elencate le modifiche che è possibile apportare a un riquadro attività personalizzato mediante le proprietà <xref:Microsoft.Office.Tools.CustomTaskPane>.  
  
|Attività|Proprietà|  
|----------|--------------|  
|Per modificare le dimensioni del riquadro attività|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Per modificare la posizione del riquadro attività|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Per nascondere il riquadro attività o renderlo visibile|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Per impedire che l'utente modifichi la posizione del riquadro attività|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="programming-custom-task-pane-events"></a>Programmazione degli eventi del riquadro attività personalizzato  
 È possibile che si desideri impostare il componente aggiuntivo VSTO in modo che risponda alle modifiche apportate dall'utente al riquadro attività personalizzato. Se, ad esempio, l'utente modifica l'orientamento del riquadro da verticale a orizzontale, potrebbe essere necessario riposizionare i controlli.  
  
 Nella tabella seguente sono elencati gli eventi che è possibile gestire per rispondere alle modifiche apportate dall'utente al riquadro attività personalizzato.  
  
|Attività|event|  
|----------|-----------|  
|Per definire il comportamento quando l'utente modifica la posizione del riquadro attività.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Per definire il comportamento quando l'utente nasconde o rende visibile il riquadro attività.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="cleaning-up-resources-used-by-the-task-pane"></a>Pulizia delle risorse usate dal riquadro attività  
 Dopo aver creato un riquadro attività personalizzato, l'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> rimane in memoria finché il componente aggiuntivo VSTO è in esecuzione.  L'oggetto rimane in memoria anche dopo che l'utente fa clic il **Chiudi** pulsante (X) nell'angolo del riquadro attività.  
  
 Per pulire le risorse usate dal riquadro attività mentre il componente aggiuntivo VSTO è ancora in esecuzione, usare i metodi <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A>. Tali metodi rimuovono l'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> specificato dalla raccolta `CustomTaskPanes` ed effettuano quindi la chiamata al metodo <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> dell'oggetto.  
  
 In [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene effettuata la pulizia automatica delle risorse usate dal riquadro attività personalizzato quando il componente aggiuntivo VSTO viene scaricato. Non chiamare il <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metodi di `ThisAddIn_Shutdown` gestore dell'evento nel progetto. Tali metodi generano un'eccezione <xref:System.ObjectDisposedException>, perché in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene effettuata la pulizia delle risorse usate dall'oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> prima della chiamata a `ThisAddIn_Shutdown`. Per ulteriori informazioni su `ThisAddIn_Shutdown`, vedere [eventi nei progetti di Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a>Gestione dei riquadri attività personalizzati in più finestre dell'applicazione  
 Quando si crea un riquadro attività personalizzato in un'applicazione che usa più finestre per visualizzare documenti e altri elementi, è necessario effettuare altre azioni per assicurarsi che il riquadro attività sia visibile quando l'utente si aspetta che lo sia.  
  
 I riquadri attività personalizzati in tutte le applicazioni sono associati a una finestra cornice del documento che presenta una visualizzazione di un documento o di un elemento all'utente. Il riquadro attività è visibile solo quando la finestra associata è visibile. Non tutte le applicazioni usano tuttavia le finestre cornice del documento nello stesso modo.  
  
 I gruppi di applicazioni seguenti hanno requisiti di sviluppo diversi:  
  
-   [Outlook](#Outlook)  
  
-   [Word, InfoPath e PowerPoint](#WordAndInfoPath)  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come ricerca per categorie: gestire i riquadri attività nei componenti aggiuntivi VSTO di Word?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a>Outlook  
 Quando si crea un riquadro attività personalizzato per Outlook, tale riquadro viene associato a una finestra di esplorazione o a una finestra di controllo specifica. Le finestre di esplorazione sono finestre che visualizzano il contenuto di una cartella, mentre le finestre di controllo visualizzano un elemento quale un messaggio di posta elettronica o un'attività.  
  
 Per visualizzare un riquadro attività personalizzato con più finestre di esplorazione o di controllo, è necessario creare una nuova istanza del riquadro attività personalizzato quando viene aperta una nuova finestra di esplorazione o di controllo. A questo scopo, gestire un evento generato quando viene creata una finestra di esplorazione o di controllo, quindi creare il riquadro attività nel gestore eventi. È anche possibile gestire gli eventi relativi alle finestre di esplorazione e di controllo per nascondere o visualizzare i riquadri attività a seconda di quale finestra è visibile.  
  
 Per associare il riquadro attività a un'esplorazione o di controllo specifici, usare il <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodo per creare il riquadro attività e passare il <xref:Microsoft.Office.Interop.Outlook.Explorer> o <xref:Microsoft.Office.Interop.Outlook.Inspector> dell'oggetto per il *finestra* parametro. Per ulteriori informazioni sulla creazione di riquadri attività personalizzati, vedere [panoramica dei riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
 Per una procedura dettagliata viene illustrato come creare un riquadro attività per ogni messaggio di posta elettronica aperto, vedere [procedura dettagliata: visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
### <a name="outlook-events"></a>Eventi di Outlook  
 Per monitorare lo stato delle finestre di esplorazione, è possibile gestire gli eventi seguenti correlati all'esplorazione:  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 Per controllare lo stato delle finestre di controllo, è possibile gestire gli eventi seguenti correlati al controllo:  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="preventing-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Come impedire l'apertura di più istanze di un riquadro attività personalizzato in Outlook  
 Per impedire la visualizzazione nelle finestre di Outlook di più istanze di un riquadro attività personalizzato, rimuovere esplicitamente il riquadro dalla raccolta `CustomTaskPanes` della classe `ThisAddIn` al momento della chiusura di ogni finestra. Chiamare il metodo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> in un evento generato quando viene chiusa una finestra, ad esempio <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> o <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Se non si rimuove esplicitamente il riquadro attività personalizzato, nelle finestre di Outlook potrebbero essere visualizzate più istanze di tale riquadro. In Outlook le finestre vengono talvolta riciclate e pertanto possono conservare riferimenti ai riquadri attività personalizzati a esse associati.  
  
##  <a name="WordAndInfoPath"></a>Word, InfoPath e PowerPoint  
 Word, InfoPath e PowerPoint visualizzano ogni documento in una finestra cornice documento diversa. Quando si crea un riquadro attività personalizzato per queste applicazioni, tale riquadro viene associato solo a un documento specifico. Se l'utente apre un documento diverso, il riquadro attività personalizzato viene nascosto fino a che il documento precedente non è nuovamente visibile.  
  
 Per visualizzare un riquadro attività personalizzato con più documenti, creare una nuova istanza del riquadro attività personalizzato quando l'utente crea un nuovo documento o ne apre uno esistente.  A questo scopo, gestire gli eventi generati quando viene creato o aperto un documento, quindi creare il riquadro attività nei gestori di eventi. È inoltre possibile gestire gli eventi del documento per nascondere o visualizzare i riquadri attività a seconda del documento visibile.  
  
 Per associare il riquadro attività a una finestra del documento specifica, usare il <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodo per creare il riquadro attività e passare un <xref:Microsoft.Office.Interop.Word.Window> (per Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (per InfoPath) o <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (per PowerPoint) per il *finestra*parametro.  
  
### <a name="word-events"></a>Eventi di Word  
 Per monitorare lo stato delle finestre di documento in Word, è possibile gestire gli eventi seguenti:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Eventi di InfoPath  
 Per monitorare lo stato delle finestre di documento in InfoPath, è possibile gestire gli eventi seguenti:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Eventi di PowerPoint  
 Per monitorare lo stato delle finestre di documento in PowerPoint, è possibile gestire gli eventi seguenti:  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procedura dettagliata: Automazione di un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Procedura dettagliata: Sincronizzazione di un riquadro attività personalizzato con un pulsante della barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Procedura dettagliata: visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
