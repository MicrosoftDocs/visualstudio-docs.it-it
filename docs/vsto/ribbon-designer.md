---
title: Sulla barra multifunzione progettazione | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cab4a223f8e2d33185f37bc6ad90397ace1d56e1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="ribbon-designer"></a>Finestra di progettazione della barra multifunzione
  La finestra di progettazione della barra multifunzione è un'area di progettazione visiva. Utilizzare la finestra di progettazione della barra multifunzione per aggiungere schede personalizzate, gruppi e controlli alla barra multifunzione di un'applicazione di Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Per aprire la finestra di progettazione della barra multifunzione, aggiungere un **della barra multifunzione (finestra di progettazione visiva)** elemento al progetto. È quindi possibile utilizzare gli strumenti di progettazione per le attività seguenti:  
  
-   [Progettare il layout della barra multifunzione](#DesigningRibbonLayout)  
  
-   [Gestire gli eventi e impostare le proprietà del controllo](#HandleEventsSetProperties)  
  
-   [Aggiungere controlli alla visualizzazione Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Esistono alcune attività che è possibile eseguire utilizzando la finestra di progettazione della barra multifunzione. Per ulteriori informazioni su queste attività e come è possibile eseguire, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come ricerca per categorie: utilizzare la finestra di progettazione della barra multifunzione per personalizzare la barra multifunzione in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="adding-a-ribbon-visual-designer-item-to-a-project"></a>Aggiunta di un elemento della barra multifunzione (finestra di progettazione visiva) a un progetto  
 Per utilizzare la finestra di progettazione della barra multifunzione, aggiungere un nuovo **della barra multifunzione (finestra di progettazione visiva)** elemento al progetto. Per altre informazioni, vedere [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Quando si aggiunge un nuovo **della barra multifunzione (finestra di progettazione visiva)** item, Visual Studio aggiunge automaticamente i seguenti file al progetto:  
  
-   Un file di codice della barra multifunzione. Questo file contiene il nome specificato per il **della barra multifunzione (finestra di progettazione visiva)** elemento il **Aggiungi nuovo elemento** la finestra di dialogo. Aggiungere il codice per gestire gli eventi della barra multifunzione per questo file.  
  
-   Un file di codice di progettazione della barra multifunzione. Questo file contiene codice generato dalla finestra di progettazione della barra multifunzione e non deve essere modificato direttamente.  
  
-   Un file di risorse. Questo file contiene i valori delle proprietà di ogni controllo sulla barra multifunzione.  
  
 Se si dispone già di un **della barra multifunzione (finestra di progettazione visiva)** elemento da un altro progetto, si può essere riutilizzata nel progetto corrente utilizzando il **Aggiungi elemento esistente** la finestra di dialogo.  
  
##  <a name="DesigningRibbonLayout"></a>Progettazione di una barra multifunzione  
 Esistono tre modi per aprire la finestra di progettazione della barra multifunzione:  
  
-   In **Esplora**, fare doppio clic sul file di codice della barra multifunzione.  
  
-   In **Esplora**, il file di codice della barra multifunzione e quindi fare clic su **Visualizza finestra di progettazione**.  
  
-   In **Esplora**, selezionare il file di codice della barra multifunzione e quindi fare clic su **progettazione** sul **vista** menu.  
  
 La finestra di progettazione della barra multifunzione contiene una scheda predefinita e un gruppo. È possibile rimuovere la scheda predefinita e il gruppo dalla finestra di progettazione della barra multifunzione. Per rimuovere il gruppo predefinito, fare doppio clic su **Group1**, quindi fare clic su **eliminare**. Per rimuovere la scheda predefinita, fare doppio clic su un'area vuota dell'area di progettazione e quindi fare clic su **Rimuovi scheda della barra multifunzione**.  
  
 È anche possibile aggiungere schede personalizzate, gruppi e controlli alla finestra di progettazione della barra multifunzione. È possibile trovare questi controlli il **della casella degli strumenti**nella **controlli della barra multifunzione di Office** gruppo. Esistono tre modi per aggiungere i controlli di **controlli della barra multifunzione di Office** gruppo alla finestra di progettazione della barra multifunzione:  
  
-   Trascinare un controllo in un'area appropriata nella finestra di progettazione della barra multifunzione.  
  
-   Fare clic su un controllo e quindi fare clic su un'area nella finestra di progettazione della barra multifunzione appropriata.  
  
-   Selezionare un'area appropriata nella finestra di progettazione e quindi fare doppio clic su un controllo nel **della casella degli strumenti**.  
  
### <a name="ribbon-design-workflow"></a>Flusso di lavoro progettazione della barra multifunzione  
 Seguire questi passaggi di base per progettare il layout della barra multifunzione:  
  
1.  [Aggiungere una scheda personalizzata alla barra multifunzione](#AddTabToRibbon).  
  
2.  [Aggiungere gruppi alla scheda](#AddGroupsToTab).  
  
3.  [Aggiungere controlli ai gruppi](#AddControlsToGroups).  
  
 I controlli possono essere rilasciati solo nei gruppi. è possibile trascinare un controllo direttamente a una scheda o alla barra multifunzione. I gruppi possono essere eliminati solo nelle schede. un gruppo non è possibile trascinare direttamente a una barra multifunzione.  
  
 Disporre i controlli trascinandoli nelle posizioni corrette. È possibile impostare le proprietà di un controllo utilizzando il **proprietà** finestra.  
  
 È possibile trascinare i controlli da una scheda a un altro sulla barra multifunzione. Se si desidera spostare un controllo a un'altra scheda, è necessario utilizzare il **Taglia** comando per rimuovere il controllo da una scheda e quindi incollare il controllo in un'altra scheda. Se si taglia il controllo e incollare il codice, il gestore dell'evento smette di funzionare. È possibile riconnettersi al gestore eventi di **proprietà** finestra. Per ulteriori informazioni, vedere [finestra proprietà](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a>Aggiungere schede personalizzate alla barra multifunzione  
 Esistono tre modi per aggiungere una scheda personalizzata alla barra multifunzione:  
  
-   Aggiungere una scheda dal **della casella degli strumenti**.  
  
-   Fare clic sulla finestra di progettazione della barra multifunzione e quindi fare clic su **Aggiungi scheda della barra multifunzione**.  
  
-   Aprire il **scheda Editor della raccolta**, quindi fare clic su **Aggiungi**.  
  
     Per aprire la **scheda Editor della raccolta**, nel **proprietà** finestra, seleziona il **schede** , proprietà e quindi fare clic sul pulsante con puntini di sospensione ![ASP.NET per dispositivi mobili Finestra di progettazione ellisse](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer").  
  
 Dopo aver aggiunto una scheda, è possibile aggiungere gruppi per contenere i controlli.  
  
#### <a name="removing-custom-tabs-from-the-ribbon"></a>Rimozione di schede personalizzate dalla barra multifunzione  
 Esistono tre modi per rimuovere una scheda personalizzata sulla barra multifunzione:  
  
-   Pulsante destro del mouse nella finestra di progettazione e quindi fare clic su **Rimuovi scheda della barra multifunzione**.  
  
-   Nel **comandi** riquadro del **proprietà** finestra, fare clic su **Rimuovi scheda della barra multifunzione**.  
  
-   Aprire il **scheda Editor della raccolta**, selezionare la scheda e quindi fare clic su **rimuovere**.  
  
#### <a name="changing-the-position-of-a-tab-on-the-ribbon"></a>La modifica della posizione di una scheda della barra multifunzione  
 È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione. È anche possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Per ulteriori informazioni, vedere [procedura: modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customizing-built-in-tabs-on-the-ribbon"></a>Personalizzare le schede predefinite della barra multifunzione  
 Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione di Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel.  
  
 È possibile aggiungere gruppi e controlli in una scheda incorporata, Per impostazione predefinita, un gruppo personalizzato viene visualizzato come l'ultimo gruppo in una scheda incorporata, anche se è possibile spostarlo prima o dopo un gruppo incorporato nella scheda.  
  
 È possibile rimuovere gruppi incorporati.  
  
 Per informazioni dettagliate su come personalizzare una scheda incorporata, vedere [procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a>Aggiunta di gruppi a una scheda  
 Gruppi di organizzano logicamente i controlli della barra multifunzione. Aggiungere gruppi a schede. Aggiungere il gruppo di tutti gli altri controlli.  
  
###  <a name="AddControlsToGroups"></a>Aggiunta di controlli ai gruppi  
 Aggiungere uno o più controlli a un gruppo. Nella tabella seguente viene descritto ogni controllo.  
  
|Control|Descrizione|  
|-------------|-----------------|  
|**Casella**|Un contenitore che organizza i controlli in un gruppo. È possibile aggiungere controlli a una casella ad eccezione di un separatore, un gruppo o una scheda. Una casella può essere orizzontale o verticale.|  
|**Pulsante**|Un pulsante che avvia un'azione. È possibile aggiungere un pulsante a un gruppo, un gruppo di pulsanti, un elenco a discesa, una raccolta, un menu o un pulsante di menu combinato.|  
|**Gruppo di pulsanti.**|Un gruppo che contiene uno o più pulsanti, interruttori, menu, pulsanti di menu combinato e raccolte. È possibile aggiungere un gruppo di pulsanti a un gruppo o un menu.|  
|**CheckBox**|Una casella che sia selezionata per attivare o disattivare un'opzione.|  
|**ComboBox**|Una casella di modifica è associata una casella di elenco. Gli utenti possono digitare o selezionare le proprie preferenze. Viene visualizzata la selezione corrente. Utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> proprietà da aggiungere e rimuovere elementi in fase di esecuzione prima o dopo che è stata caricata nell'applicazione di Office.|  
|**Elenco a discesa**|Un elenco di elementi che l'utente può selezionare. L'utente non è possibile digitare un nuovo elemento in un elenco a discesa.<br /><br /> Utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> proprietà per aggiungere elementi all'elenco. È possibile aggiungere e rimuovere elementi in fase di esecuzione.<br /><br /> Utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> proprietà per aggiungere pulsanti all'elenco. Tuttavia, è Impossibile aggiungere e rimuovere i pulsanti in fase di esecuzione dopo la barra multifunzione viene caricata nell'applicazione di Office.|  
|**Casella di modifica**|Casella in cui l'utente può digitare il testo.|  
|**Raccolta**|Un menu che visualizza una matrice o una griglia di opzioni visive selezionabili dagli utenti. È possibile controllare il layout delle selezioni nel menu. Utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> le proprietà per specificare il numero di righe e colonne che verranno visualizzati gli elementi e i pulsanti della raccolta.|  
|**Etichetta**|Testo che è possibile utilizzare per identificare i controlli della barra multifunzione.|  
|**Menu**|Elenco a discesa che può contenere uno dei seguenti controlli:<br /><br /> -Pulsante<br />-La casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante di menu combinato<br />-Pulsante Mostra/Nascondi<br />-Separatore<br /><br /> Per aggiungere un controllo a un menu nella finestra di progettazione della barra multifunzione, fare clic sulla freccia rivolta verso il basso nel menu per esporre l'area di progettazione di menu. È quindi possibile trascinare i controlli della barra multifunzione dal **della casella degli strumenti** nel menu. Per disporre i controlli, trascinarli nelle posizioni desiderate.<br /><br /> Per aggiungere controlli al <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo la barra multifunzione viene caricata nell'applicazione di Office, è necessario impostare il <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà **true** prima di caricata la barra multifunzione. Per informazioni su come eseguire questa operazione, vedere [Cenni preliminari sul modello di oggetto della barra multifunzione](../vsto/ribbon-object-model-overview.md).|  
|**Separatore**|Barra sottile utilizzata per separare gli elementi in un elenco. Quando aggiunta a un gruppo, la barra è verticale. Quando aggiunta a un menu, la barra è orizzontale.|  
|**SplitButton**|Un pulsante associato un menu. Un pulsante di menu combinato può contenere uno dei seguenti controlli:<br /><br /> -Pulsante<br />-La casella di controllo<br />-Raccolta<br />-Menu<br />-Pulsante di menu combinato<br />-Pulsante Mostra/Nascondi<br />-Separatore<br /><br /> Analogamente al menu, il pulsante di menu combinato dispone della propria area di progettazione. Tuttavia, a differenza di un menu, è possibile aggiornare solo gli elementi in un pulsante di menu combinato prima che la barra multifunzione viene caricata nell'applicazione di Office. Per informazioni su come aggiornare gli elementi in un pulsante di menu combinato, vedere [Cenni preliminari sul modello di oggetto della barra multifunzione](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Un pulsante visualizzato attivo o inattivo.|  
  
##  <a name="HandleEventsSetProperties"></a>Gestione degli eventi e impostazione delle proprietà  
 La finestra di progettazione della barra multifunzione consente di impostare le proprietà del controllo in fase di progettazione utilizzando il **proprietà** finestra. Inoltre, la barra multifunzione espone un modello a oggetti fortemente tipizzato che è possibile utilizzare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.  
  
 Fare doppio clic su qualsiasi controllo nella finestra di progettazione per aprire un gestore eventi per l'evento predefinito del controllo. È possibile creare gestori eventi per tutti gli altri eventi di controllo utilizzando il **proprietà** finestra.  
  
 Eventi della barra multifunzione e le proprietà si trovano nel <xref:Microsoft.Office.Tools.Ribbon> dello spazio dei nomi. Il **della barra multifunzione (finestra di progettazione visiva)** elemento aggiunge automaticamente un riferimento all'assembly nel progetto e inserisce appropriata **utilizzando** o **importazioni** istruzione all'inizio del file di codice della barra multifunzione.  
  
 Per informazioni sulla gestione degli eventi della barra multifunzione e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione, vedere [Cenni preliminari sul modello di oggetto della barra multifunzione](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a>Personalizzazione della visualizzazione Backstage  
 È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic il **File** scheda. Questo menu è detto visualizzazione Backstage.  
  
 È possibile posizionare i controlli prima o dopo i controlli incorporati utilizzando la finestra di progettazione della barra multifunzione. Un controllo incorporato è un controllo che è già presente nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli incorporati, è necessario utilizzare XML della barra multifunzione. Per ulteriori informazioni su **della barra multifunzione (XML)**, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md). Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [introduzione per la visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizzazione della visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Per informazioni su come aggiungere controlli alla visualizzazione Backstage, vedere [procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a>Accessibilità nella finestra di progettazione della barra multifunzione  
 È possibile utilizzare i tasti di scelta rapida per spostare i controlli nella finestra di progettazione della barra multifunzione. Alcuni tasti di scelta rapida si applicano a tutti i controlli e alcuni validi solo per i controlli che dispongono di menu.  
  
 Tasti di scelta rapida che si applicano a tutti i controlli vengono visualizzati nella tabella seguente.  
  
|Operazione|Tasto di scelta rapida|  
|------------|-----------------------|  
|Spostare un controllo prima che il controllo precedente nell'elenco.|CTRL + FRECCIA SU<br /><br /> CTRL + FRECCIA SINISTRA|  
|Spostare un controllo dopo il controllo successivo nell'elenco.|CTRL + FRECCIA GIÙ<br /><br /> CTRL + FRECCIA DESTRA|  
|Spostare la selezione da un controllo a un'altra nello stesso gruppo. Per un pannello di riepilogo a discesa, spostare tra il controllo padre e i controlli nel Pannello di riepilogo a discesa.|SU<br /><br /> GIÙ|  
|Eseguire l'iterazione in avanti con tutti i controlli.|TAB|  
|Eseguire l'iterazione di tutti i controlli in ordine ascendente.|MAIUSC+TAB|  
|Eliminare il controllo selezionato o un set di controlli.|DELETE|  
|Copiare i controlli selezionati.|CTRL+C|  
|Taglia i controlli selezionati.|CTRL+X|  
|Incollare i controlli dagli Appunti.|CTRL+V|  
|Selezionare il **della casella degli strumenti**.|CTRL+ALT+X|  
|Selezionare il componente padre.|ESC|  
  
 Tasti di scelta rapida che si applicano solo al Menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, e <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> vengono visualizzati nella tabella seguente.  
  
|Operazione|Tasto di scelta rapida|  
|------------|-----------------------|  
|Se il pannello di riepilogo a discesa è aperto ed è presente un controllo selezionato nel Pannello di riepilogo a discesa, selezionare il controllo padre.|LEFT|  
|Chiudere il pannello di riepilogo a discesa, se il pannello di riepilogo a discesa è aperto e viene selezionato il controllo padre.|LEFT|  
|Aprire il pannello di riepilogo a discesa.|RIGHT|  
|Se è aperto il pannello di riepilogo a discesa, selezionare il primo controllo nel Pannello di riepilogo a discesa.|RIGHT|  
|Chiudere il pannello di riepilogo a discesa.|ESC|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  