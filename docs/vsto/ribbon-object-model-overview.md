---
title: Panoramica del modello a oggetti di barra multifunzione | Documenti Microsoft
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bda61cd7ca0e169a4f62fbc0c33b24e3c4ec0048
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="ribbon-object-model-overview"></a>Cenni preliminari sul modello a oggetti della barra multifunzione
  Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] espone un modello a oggetti fortemente tipizzato che è possibile utilizzare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione. Ad esempio, è possibile in modo dinamico popolare i controlli menu, o mostrare e nascondere controlli in base al contesto. È anche possibile aggiungere schede, gruppi e controlli a una barra multifunzione, ma solo prima che la barra multifunzione viene caricata dall'applicazione di Office. Per informazioni, vedere [impostazione di proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Questo modello a oggetti della barra multifunzione è composto principalmente il [classe Ribbon](#RibbonClass), [eventi della barra multifunzione](#RibbonEvents), e [classi di controlli della barra multifunzione](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a>Classe Ribbon  
 Quando si aggiunge un nuovo **della barra multifunzione (finestra di progettazione visiva)** elemento a un progetto, Visual Studio aggiunge un **della barra multifunzione** classe al progetto. Il **della barra multifunzione** classe eredita la <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> classe.  
  
 Questa classe viene visualizzato come una classe parziale che viene suddiviso tra i file di codice della barra multifunzione e il file di codice di progettazione della barra multifunzione.  
  
##  <a name="RibbonEvents"></a>Eventi della barra multifunzione  
 Il **della barra multifunzione** classe contiene i seguenti tre eventi:  
  
|event|Descrizione|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Generato quando l'applicazione di Office carica la personalizzazione della barra multifunzione. Il <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> gestore eventi viene aggiunto automaticamente al file di codice della barra multifunzione. Utilizzare questo gestore eventi per eseguire codice personalizzato durante il caricamento della barra multifunzione.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Consente di memorizzare nella cache immagini la personalizzazione della barra multifunzione al caricamento della barra multifunzione. Se si scrive codice per memorizzare nella cache le immagini della barra multifunzione in questo gestore eventi, è possibile ottenere un leggero miglioramento delle prestazioni. Per altre informazioni, vedere <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Generato quando si chiude l'istanza della barra multifunzione.|  
  
##  <a name="RibbonControlClasses"></a>Controlli della barra multifunzione  
 Il <xref:Microsoft.Office.Tools.Ribbon> spazio dei nomi contiene un tipo per ogni controllo presente nel **controlli della barra multifunzione di Office** gruppo il **della casella degli strumenti**.  
  
 Nella tabella seguente mostra il tipo per ogni `Ribbon` controllo. Per una descrizione di ogni controllo, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
|Nome controllo|Nome di classe|  
|------------------|----------------|  
|**Casella**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Pulsante**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Gruppo di pulsanti.**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Elenco a discesa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Casella di modifica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Raccolta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Gruppo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etichetta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separatore**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Scheda**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Il <xref:Microsoft.Office.Tools.Ribbon> dello spazio dei nomi viene utilizzato il prefisso "Della barra multifunzione" per questi tipi per evitare conflitti con i nomi delle classi di controlli nel <xref:System.Windows.Forms> dello spazio dei nomi.  
  
 Quando si aggiunge un controllo alla finestra di progettazione della barra multifunzione, la finestra di progettazione della barra multifunzione dichiara la classe per il controllo come un campo nel file di codice di progettazione della barra multifunzione.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Attività comuni utilizzando le proprietà dei controlli della barra multifunzione  
 Ogni `Ribbon` controllo contiene proprietà che è possibile utilizzare per eseguire diverse attività, ad esempio l'assegnazione di un'etichetta a un controllo, o la disattivazione della visualizzazione dei controlli.  
  
 In alcuni casi, le proprietà diventano di sola lettura dopo il caricamento della barra multifunzione o dopo l'aggiunta di un controllo a un menu dinamico. Per ulteriori informazioni, vedere [impostazione delle proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 Nella tabella seguente vengono descritte alcune delle attività che è possibile eseguire utilizzando `Ribbon` le proprietà del controllo.  
  
|Per questa attività:|Eseguire questa operazione:|  
|--------------------|--------------|  
|Nascondere o mostrare un controllo.|Utilizzare la proprietà Visible.|  
|Abilitare o disabilitare un controllo.|Utilizzare la proprietà Enabled.|  
|Impostare le dimensioni di un controllo.|Utilizzare la proprietà ControlSize.|  
|Ottenere l'immagine visualizzata su un controllo.|Utilizzare la proprietà immagine.|  
|Modificare l'etichetta di un controllo.|Utilizzare la proprietà Label.|  
|Aggiungere un controllo di dati definiti dall'utente.|Utilizzare la proprietà Tag.|  
|Ottenere gli elementi in un <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>controllo.|Utilizzare la proprietà di elementi.|  
|Aggiungere elementi a un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> controllo.|Utilizzare la proprietà di elementi.|  
|Aggiungere controlli a un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilizzare la proprietà di elementi.<br /><br /> Per aggiungere controlli al <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo la barra multifunzione viene caricata nell'applicazione di Office, è necessario impostare il <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> proprietà **true** prima che la barra multifunzione viene caricata nell'applicazione di Office. Per informazioni, vedere [impostazione di proprietà che diventano di sola lettura](#SettingReadOnlyProperties).|  
|Ottenere l'elemento selezionato di un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilizzare la proprietà SelectedItem. Per un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> proprietà.|  
|Ottenere i gruppi in un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Usare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Specificare il numero di righe e colonne che vengono visualizzati in un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilizzare il <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> proprietà.|  
  
##  <a name="SettingReadOnlyProperties"></a>Impostazione delle proprietà che diventano di sola lettura  
 Alcune proprietà possono essere impostate solo prima di caricamento della barra multifunzione. Esistono tre posizioni per impostare queste proprietà:  
  
-   In Visual Studio **proprietà** finestra.  
  
-   Nel costruttore del **della barra multifunzione** classe.  
  
-   Nel metodo CreateRibbonExtensibilityObject il `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto.  
  
 Menu dinamici presentano alcune eccezioni. È possibile creare nuovi controlli, impostarne le proprietà e quindi aggiungerli a un menu dinamico in fase di esecuzione, anche dopo il caricamento della barra multifunzione che contiene il menu di.  
  
 In qualsiasi momento, è possono impostare le proprietà dei controlli aggiunti a un menu dinamico.  
  
 Per ulteriori informazioni, vedere [proprietà che diventano di sola lettura](#ReadOnlyProperties).  
  
### <a name="setting-properties-in-the-constructor-of-the-ribbon"></a>Impostazione delle proprietà nel costruttore della barra multifunzione  
 È possibile impostare le proprietà di un `Ribbon` nel costruttore del controllo di **della barra multifunzione** classe. Questo codice deve essere visualizzata dopo la chiamata al `InitializeComponent` metodo. Nell'esempio seguente viene aggiunto un nuovo pulsante a un gruppo, se l'ora corrente è 17:00 del Pacifico (UTC-8) o versione successiva.  
  
 Aggiungere il codice seguente.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 Nei progetti Visual c# che è stato eseguito l'aggiornamento da Visual Studio 2008, il costruttore viene visualizzato nel file di codice della barra multifunzione.  
  
 Nei progetti Visual Basic o nei progetti Visual c# creati in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], il costruttore viene visualizzato nel file di codice di progettazione della barra multifunzione. Questo file è denominato *YourRibbonItem*. Designer.cs o *YourRibbonItem*. Designer. Per visualizzare questo file nei progetti Visual Basic, è innanzitutto necessario scegliere il **Mostra tutti i file** pulsante in Esplora soluzioni.  
  
### <a name="setting-properties-in-the-createribbonextensibilityobject-method"></a>Impostazione delle proprietà nel metodo CreateRibbonExtensibilityObject  
 È possibile impostare le proprietà di un `Ribbon` controllare quando si esegue l'override del metodo CreateRibbonExtensibilityObject nella `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto. Per ulteriori informazioni sul metodo CreateRibbonExtensibilityObject, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
 Nell'esempio seguente imposta la proprietà della barra multifunzione nel metodo CreateRibbonExtensibilityObject la `ThisWorkbook` classe di un progetto cartella di lavoro di Excel.  
  
 Aggiungere il codice seguente.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a>Proprietà che diventano di sola lettura  
 Nella tabella seguente mostra le proprietà che possono essere impostate solo prima di caricamento della barra multifunzione.  
  
> [!NOTE]  
>  È possibile impostare le proprietà dei controlli nel menu dinamici in qualsiasi momento. Questa tabella non viene applicato in questo caso.  
  
|Proprietà|Classe del controllo della barra multifunzione|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dinamica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Gruppi**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Posizione**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Conteggio delle righe**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Schede**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titolo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="setting-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Impostazione delle proprietà per barre multifunzione visualizzate nei controlli di Outlook  
 Ogni volta che un utente apre un controllo in cui viene visualizzata la barra multifunzione viene creata una nuova istanza della barra multifunzione. Tuttavia, è possibile impostare le proprietà elencate nella tabella precedente solo prima che venga creata la prima istanza della barra multifunzione. Dopo la prima istanza viene creata, queste proprietà diventano di sola lettura perché la prima istanza definisce il file XML che è usato da Outlook per caricare la barra multifunzione.  
  
 Se si dispone di logica condizionale che imposta una di queste proprietà su un valore diverso quando vengono create altre istanze della barra multifunzione, questo codice avrà alcun effetto.  
  
> [!NOTE]  
>  Verificare che il **nome** proprietà è impostata per ogni controllo che aggiunge a una barra multifunzione di Outlook. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di esecuzione, è necessario impostare questa proprietà nel codice. Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di progettazione, la proprietà Name viene impostata automaticamente.  
  
## <a name="ribbon-control-events"></a>Eventi di controllo della barra multifunzione  
 Ogni classe del controllo contiene uno o più eventi. Nella tabella seguente vengono descritti questi eventi.  
  
|event|Descrizione|  
|-----------|-----------------|  
|Clic|Si verifica quando si seleziona un controllo.|  
|TextChanged|Si verifica quando viene modificato il testo di una casella di modifica o una casella combinata.|  
|ItemsLoading|Si verifica quando la raccolta di elementi del controllo viene richiesto dalle applicazioni di Office. Office memorizza nella cache la raccolta di elementi fino a quando il codice modifica le proprietà del controllo o si chiama il <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metodo.|  
|ButtonClick|Si verifica quando un pulsante in un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> si fa clic.|  
|SelectionChanged|Si verifica quando la selezione in un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> le modifiche.|  
|DialogLauncherClick|Si verifica quando si seleziona l'icona di visualizzazione della finestra di dialogo nell'angolo inferiore destro di un gruppo.|  
  
 I gestori eventi per questi eventi sono i due parametri seguenti.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*mittente*|Un <xref:System.Object> che rappresenta il controllo che ha generato l'evento.|  
|*e*|Oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> che contiene un <xref:Microsoft.Office.Core.IRibbonControl>. Utilizzare questo controllo di accesso a qualsiasi proprietà che non è disponibile nel modello a oggetti della barra multifunzione fornito dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Aggiornamento dei controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  