---
title: 'Procedura dettagliata: Creazione di un modello mediante controlli contenuto | Documenti Microsoft'
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
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d221b9374bf71df3d66400289c50310263c2e9e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto
  Questa procedura dettagliata mostra come creare una personalizzazione a livello di documento che usa i controlli contenuto per creare contenuti strutturati e riutilizzabili in un modello di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word consente di creare una raccolta di parti di documento riutilizzabili, denominate *blocchi*. Questa procedura dettagliata mostra come creare due tabelle come blocchi predefiniti. Ogni tabella contiene diversi controlli contenuto che possono includere diversi tipi di contenuto, ad esempio testo normale o date. Una delle tabelle contiene informazioni su un dipendente, mentre un'altra contiene i suggerimenti del cliente.  
  
 Dopo aver creato un documento dal modello, è possibile aggiungere una delle tabelle al documento usando diversi oggetti <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, che visualizzano i blocchi predefiniti disponibili nel modello.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di una tabella contenente i controlli contenuto in un modello di Word in fase di progettazione.  
  
-   Popolamento a livello di codice di un controllo contenuto della casella combinata e di un controllo contenuto dell'elenco a discesa.  
  
-   Impedire agli utenti di modificare una tabella specificata.  
  
-   Aggiunta di tabelle alla raccolta di blocchi predefiniti di un modello.  
  
-   Creazione di un controllo contenuto che visualizza i blocchi predefiniti disponibili nel modello.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-a-new-word-template-project"></a>Creazione di un nuovo progetto di modello di Word  
 Creare un modello di Word in modo che gli utenti possano creare facilmente le proprie copie.  
  
#### <a name="to-create-a-new-word-template-project"></a>Per creare un nuovo progetto di modello di Word  
  
1.  Creare un progetto di modello di Word con il nome **MyBuildingBlockTemplate**. Nella procedura guidata creare un nuovo documento nella soluzione. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Apre il nuovo modello di Word nella finestra di progettazione e aggiunge il **MyBuildingBlockTemplate** progetto **Esplora**.  
  
## <a name="creating-the-employee-table"></a>Creazione della tabella dei dipendenti  
 Creare una tabella che contiene quattro tipi differenti di controlli contenuto in cui un utente può immettere le informazioni su un dipendente.  
  
#### <a name="to-create-the-employee-table"></a>Per creare la tabella dei dipendenti  
  
1.  Nel modello di Word ospitato nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, sulla barra multifunzione, fare clic su di **inserire** scheda.  
  
2.  Nel **tabelle** gruppo, fare clic su **tabella**e inserire una tabella con 2 colonne e 4 righe.  
  
3.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |**Nome del dipendente**|  
    |**Data di assunzione**|  
    |**Titolo**|  
    |**Immagine**|  
  
4.  Fare clic sulla prima cella nella seconda colonna (accanto a **nome dipendente**).  
  
5.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Nel **controlli** gruppo, fare clic su di **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.  
  
7.  Fare clic sulla seconda cella nella seconda colonna (accanto a **Data assunzione**).  
  
8.  Nel **controlli** gruppo, fare clic su di **selezione data** pulsante ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.  
  
9. Fare clic sulla terza cella della seconda colonna (accanto a **titolo**).  
  
10. Nel **controlli** gruppo, fare clic su di **casella combinata** pulsante ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>alla terza cella.  
  
11. Fare clic su ultima cella nella seconda colonna (accanto a **immagine**).  
  
12. Nel **controlli** gruppo, fare clic su di **controllo contenuto immagine** pulsante ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PictureContentControl> all'ultima cella.  
  
## <a name="creating-the-customer-feedback-table"></a>Creazione della tabella dei suggerimenti dei clienti  
 Creare una tabella che contiene tre tipi differenti di controlli contenuto in cui un utente può immettere le informazioni relative ai suggerimenti dei clienti.  
  
#### <a name="to-create-the-customer-feedback-table"></a>Per creare una tabella dei suggerimenti dei clienti  
  
1.  Nel modello di Word fare clic sulla riga dopo la tabella dei dipendenti aggiunta in precedenza, quindi premere INVIO per aggiungere un nuovo paragrafo.  
  
2.  Sulla barra multifunzione, fare clic su di **inserire** scheda.  
  
3.  Nel **tabelle** gruppo, fare clic su **tabella**e inserire una tabella con 2 colonne e 3 righe.  
  
4.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |**Nome del cliente**|  
    |**Valutazione soddisfazione**|  
    |**Commenti**|  
  
5.  Fare clic sulla prima cella della seconda colonna (accanto a **nome cliente**).  
  
6.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
7.  Nel **controlli** gruppo, fare clic su di **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.  
  
8.  Fare clic su nella seconda cella della seconda colonna (accanto a **soddisfazione**).  
  
9. Nel **controlli** gruppo, fare clic su di **riepilogo** pulsante ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> alla seconda cella.  
  
10. Fare clic nell'ultima cella della seconda colonna (accanto a **commenti**).  
  
11. Nel **controlli** gruppo, fare clic su di **Rich Text** pulsante ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.RichTextContentControl>all'ultima cella.  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>Popolamento a livello di codice della casella combinata e dell'elenco a discesa  
 È possibile inizializzare i controlli contenuto in fase di progettazione utilizzando il **proprietà** finestra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. È anche possibile inizializzarli in fase di esecuzione. In questo caso gli stati iniziali possono essere impostati dinamicamente. Per questa procedura dettagliata, è necessario utilizzare codice per popolare le voci di <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in fase di esecuzione in modo da poter visualizzare il funzionano di questi oggetti.  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Per modificare l'interfaccia utente dei controlli contenuto a livello di codice  
  
1.  In **Esplora**, fare doppio clic su **ThisDocument. cs** o **ThisDocument. vb**, quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere il codice seguente alla classe `ThisDocument`. Questo codice dichiara diversi oggetti che verranno usati più avanti nella procedura dettagliata.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice aggiunge voci a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nelle tabelle e imposta il testo del segnaposto visualizzato in ciascun controllo prima che l'utente apporti modifiche.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>Impedire agli utenti di modificare la tabella dei dipendenti  
 Usare l'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza per proteggere la tabella dei dipendenti. Dopo aver protetto la tabella, gli utenti possono comunque modificarne i controlli contenuto. Tuttavia, non possono modificare il testo nella prima colonna o modificare la tabella in altri modi, ad esempio aggiungendo o rimuovendo righe e colonne. Per ulteriori informazioni su come usare un <xref:Microsoft.Office.Tools.Word.GroupContentControl> per proteggere una parte di un documento, vedere [controlli contenuto](../vsto/content-controls.md).  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>Per impedire agli utenti di modificare la tabella dei dipendenti  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice impedisce agli utenti di modificare la tabella dei dipendenti inserendo la tabella all'interno dell'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>Aggiunta di tabella alla raccolta di blocchi predefiniti  
 Aggiungere le tabelle a una raccolta di blocchi predefiniti del documento nel modello in modo che gli utenti possano inserire le tabelle create all'interno di quel documento. Per ulteriori informazioni sui blocchi predefiniti del documento, vedere [controlli contenuto](../vsto/content-controls.md).  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Per aggiungere le tabelle ai blocchi predefiniti nel modello  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice aggiunge nuovi blocchi predefiniti che contengono le tabelle alla raccolta Microsoft.Office.Interop.Word.BuildingBlockEntries, che contiene tutti i blocchi predefiniti riutilizzabili nel modello. I nuovi blocchi predefiniti definiti in una nuova categoria denominata **informazioni su dipendenti e clienti** e viene assegnato il tipo di blocco predefinito wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice elimina le tabelle dal modello. Le tabelle non sono più necessarie perché sono state aggiunte alla raccolta di blocchi predefiniti riutilizzabili nel modello. Il codice passa innanzitutto il documento in modalità progettazione in modo che la tabella dei dipendenti protetta possa essere eliminata.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>Creazione di un controllo contenuto che visualizza i blocchi predefiniti  
 Creare un controllo contenuto che fornisca l'accesso ai blocchi predefiniti (ossia, alle tabelle) create in precedenza. Gli utenti possono selezionare questo controllo per aggiungere le tabelle al documento.  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Per creare un controllo contenuto che visualizza i blocchi predefiniti  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Il codice inizializza l'oggetto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> dichiarato in precedenza. Il <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Visualizza tutti i blocchi predefiniti definiti nella categoria **informazioni su dipendenti e clienti** e che hanno il tipo di blocco predefinito wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>Test del progetto  
 Gli utenti possono fare clic sui controlli della raccolta di blocchi predefiniti nel documento per inserire la tabella dei dipendenti o la tabella dei suggerimenti dei clienti. Gli utenti possono digitare o selezionare le risposte nei controlli contenuto in entrambe le tabelle. Gli utenti possono modificare altre parti della tabella dei suggerimenti dei clienti, ma non devono poter modificare altre parti della tabella dei dipendenti.  
  
#### <a name="to-test-the-employee-table"></a>Per testare la tabella dei dipendenti  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic su **scegliere il primo blocco predefinito** per visualizzare il primo controllo contenuto della raccolta di blocchi predefiniti.  
  
3.  Fare clic sulla freccia giù accanto al **raccolta personalizzata 1** titolo nel controllo e selezionare **tabella Employee**.  
  
4.  Fare clic nella cella a destra del **nome dipendente** cella e digitare un nome.  
  
     Verificare di poter aggiungere solo testo alla cella. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> consente agli utenti di aggiungere solo testo, non altri tipi di contenuto, ad esempio grafici o tabelle.  
  
5.  Fare clic nella cella a destra del **Data assunzione** e selezionare una data nella selezione data.  
  
6.  Fare clic nella cella a destra del **titolo** di cella e selezionare uno dei titoli professionali nella casella combinata.  
  
     Facoltativamente, digitare il nome di un titolo professionale non presente nell'elenco. <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>, infatti, consente agli utenti di effettuare una selezione da un elenco di voci oppure di digitare le voci personalizzate.  
  
7.  Fare clic sull'icona nella cella a destra del **immagine** di cella e selezionare un'immagine per visualizzarla.  
  
8.  Provare ad aggiungere e quindi a eliminare le righe o le colonne dalla tabella. Verificare che non sia possibile modificare la tabella. <xref:Microsoft.Office.Tools.Word.GroupContentControl> impedisce di apportare modifiche.  
  
#### <a name="to-test-the-customer-feedback-table"></a>Per testare la tabella dei suggerimenti dei clienti  
  
1.  Fare clic su **scegliere il secondo blocco predefinito** per visualizzare il secondo controllo contenuto della raccolta di blocchi predefiniti.  
  
2.  Fare clic sulla freccia giù accanto al **raccolta personalizzata 1** titolo nel controllo e selezionare **tabella Customer**.  
  
3.  Fare clic nella cella a destra del **nome cliente** cella e digitare un nome.  
  
4.  Fare clic nella cella a destra del **soddisfazione** di cella e selezionare una delle opzioni disponibili.  
  
     Verificare che non sia possibile digitare una voce personalizzata. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> consente di selezionare solo da un elenco di voci.  
  
5.  Fare clic nella cella a destra del **commenti** cella e digitare i commenti.  
  
     Facoltativamente, aggiungere alcuni contenuti diversi dal testo, ad esempio un grafico o una tabella incorporata. <xref:Microsoft.Office.Tools.Word.RichTextContentControl> consente, infatti, agli utenti di aggiungere contenuti diversi dal testo.  
  
6.  Verificare di poter aggiungere e quindi eliminare le righe o le colonne dalla tabella. Ciò è possibile perché la tabella non è stata protetta inserendola in <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Chiudere il modello.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere l'argomento seguente:  
  
-   Associare controlli contenuto a parti del codice XML, chiamate anche parti XML personalizzate, incorporate in un documento. Per ulteriori informazioni, vedere [procedura dettagliata: associazione di controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: proteggere parti di documenti mediante controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  