---
title: 'Procedura dettagliata: Creare un modello mediante controlli contenuto'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3feb17c2cfc51326f125fb6991b37ccde1f9b1bd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438567"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Procedura dettagliata: Creare un modello mediante controlli contenuto
  Questa procedura dettagliata mostra come creare una personalizzazione a livello di documento che usa i controlli contenuto per creare contenuti strutturati e riutilizzabili in un modello di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word consente di creare una raccolta di parti di documento riutilizzabili, denominate *blocchi predefiniti*. Questa procedura dettagliata mostra come creare due tabelle come blocchi predefiniti. Ogni tabella contiene diversi controlli contenuto che possono includere diversi tipi di contenuto, ad esempio testo normale o date. Una delle tabelle contiene informazioni su un dipendente, mentre un'altra contiene i suggerimenti del cliente.

 Dopo aver creato un documento dal modello, è possibile aggiungere una delle tabelle al documento usando diversi oggetti <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, che visualizzano i blocchi predefiniti disponibili nel modello.

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di una tabella contenente i controlli contenuto in un modello di Word in fase di progettazione.

- Popolamento a livello di codice di un controllo contenuto della casella combinata e di un controllo contenuto dell'elenco a discesa.

- Impedire agli utenti di modificare una tabella specificata.

- Aggiunta di tabelle alla raccolta di blocchi predefiniti di un modello.

- Creazione di un controllo contenuto che visualizza i blocchi predefiniti disponibili nel modello.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Creare un nuovo progetto di modello di Word
 Creare un modello di Word in modo che gli utenti possano creare facilmente le proprie copie.

### <a name="to-create-a-new-word-template-project"></a>Per creare un nuovo progetto di modello di Word

1. Creare un progetto di modello di Word con il nome **MyBuildingBlockTemplate**. Nella procedura guidata creare un nuovo documento nella soluzione. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Apre il nuovo modello di Word nella finestra di progettazione e aggiunge il **MyBuildingBlockTemplate** progetto al **Esplora soluzioni**.

## <a name="create-the-employee-table"></a>Creare la tabella employee
 Creare una tabella che contiene quattro tipi differenti di controlli contenuto in cui un utente può immettere le informazioni su un dipendente.

### <a name="to-create-the-employee-table"></a>Per creare la tabella dei dipendenti

1. Nel modello di Word ospitato nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, sulla barra multifunzione, fare clic sui **Inserisci** scheda.

2. Nel **tabelle** gruppo, fare clic su **tabella**e inserire una tabella con due colonne e quattro righe.

3. Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:

   ||
   |-|
   |**Nome del dipendente**|
   |**Data di assunzione**|
   |**Titolo**|
   |**Immagine**|

4. Fare clic nella prima cella nella seconda colonna (accanto a **Employee Name**).

5. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

   > [!NOTE]
   > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Nel **controlli** gruppo, fare clic sui **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.

7. Fare clic sulla seconda cella nella seconda colonna (accanto a **Data assunzione**).

8. Nel **controlli** gruppo, fare clic sui **Date Picker** pulsante ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.

9. Fare clic sulla terza cella della seconda colonna (accanto a **titolo**).

10. Nel **controlli** gruppo, fare clic sui **pole se Seznamem** pulsante ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>alla terza cella.

11. Fare clic su ultima cella della seconda colonna (accanto a **Picture**).

12. Nel **controlli** gruppo, fare clic sui **controllo contenuto immagine** pulsante ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PictureContentControl> all'ultima cella.

## <a name="create-the-customer-feedback-table"></a>Creare la tabella di commenti e suggerimenti dei clienti
 Creare una tabella che contiene tre tipi differenti di controlli contenuto in cui un utente può immettere le informazioni relative ai suggerimenti dei clienti.

### <a name="to-create-the-customer-feedback-table"></a>Per creare una tabella dei suggerimenti dei clienti

1. Nel modello di Word, fare clic nella riga dopo la tabella dei dipendenti aggiunta in precedenza e premere **invio** per aggiungere un nuovo paragrafo.

2. Sulla barra multifunzione, fare clic sui **Inserisci** scheda.

3. Nel **tabelle** gruppo, fare clic su **tabella**e inserire una tabella con due colonne e tre righe.

4. Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:

   ||
   |-|
   |**Nome del cliente**|
   |**Valutazione soddisfazione**|
   |**Commenti**|

5. Fare clic nella prima cella della seconda colonna (accanto a **Customer Name**).

6. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

7. Nel **controlli** gruppo, fare clic sui **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.

8. Fare clic nella seconda cella della seconda colonna (accanto a **valutazione soddisfazione**).

9. Nel **controlli** gruppo, fare clic sul **elenco a discesa** pulsante ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> alla seconda cella.

10. Fare clic nell'ultima cella della seconda colonna (accanto a **commenti**).

11. Nel **controlli** gruppo, fare clic sui **Rich Text** pulsante ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.RichTextContentControl>all'ultima cella.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Popolare la casella combinata e un elenco a discesa scegliere a livello di codice
 È possibile inizializzare i controlli contenuto in fase di progettazione utilizzando il **delle proprietà** finestra in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. È anche possibile inizializzarli in fase di esecuzione, che consente di impostare gli stati iniziali in modo dinamico. Per questa procedura dettagliata, usare codice per popolare le voci nel <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in fase di esecuzione in modo che è possibile visualizzare questi oggetti funzionano.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Per modificare l'interfaccia utente dei controlli contenuto a livello di codice

1. Nelle **Esplora soluzioni**, fare doppio clic su **ThisDocument.cs** oppure **ThisDocument. vb**, quindi fare clic su **Visualizza codice**.

2. Aggiungere il codice seguente alla classe `ThisDocument` . Questo codice dichiara diversi oggetti che verranno usati più avanti nella procedura dettagliata.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice aggiunge voci a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nelle tabelle e imposta il testo del segnaposto visualizzato in ciascun controllo prima che l'utente apporti modifiche.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>Impedire agli utenti di modificare la tabella dei dipendenti
 Usare l'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza per proteggere la tabella dei dipendenti. Dopo aver protetto la tabella, gli utenti possono comunque modificarne i controlli contenuto. Tuttavia, non possono modificare il testo nella prima colonna o modificare la tabella in altri modi, ad esempio aggiungendo o rimuovendo righe e colonne. Per altre informazioni su come usare un <xref:Microsoft.Office.Tools.Word.GroupContentControl> per proteggere una parte di un documento, vedere [dei controlli contenuto](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Per impedire agli utenti di modificare la tabella dei dipendenti

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice impedisce agli utenti di modificare la tabella dei dipendenti inserendo la tabella all'interno dell'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>Aggiungere le tabelle alla raccolta di blocchi predefiniti
 Aggiungere le tabelle a una raccolta di blocchi predefiniti del documento nel modello in modo che gli utenti possano inserire le tabelle create all'interno di quel documento. Per altre informazioni sui blocchi predefiniti di documento, vedere [dei controlli contenuto](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Per aggiungere le tabelle ai blocchi predefiniti nel modello

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice aggiunge nuovi blocchi predefiniti che contengono le tabelle alla raccolta Microsoft.Office.Interop.Word.BuildingBlockEntries, che contiene tutti i blocchi predefiniti riutilizzabili nel modello. I nuovi blocchi predefiniti sono definiti in una nuova categoria denominata **informazioni su dipendenti e clienti** e viene assegnato il tipo di blocco predefinito `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice elimina le tabelle dal modello. Le tabelle non sono più necessarie perché sono state aggiunte alla raccolta di blocchi predefiniti riutilizzabili nel modello. Il codice passa innanzitutto il documento in modalità progettazione in modo che la tabella dei dipendenti protetta possa essere eliminata.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Creare un controllo contenuto che visualizza i blocchi predefiniti
 Creare un controllo contenuto che fornisca l'accesso ai blocchi predefiniti (ossia, alle tabelle) create in precedenza. Gli utenti possono selezionare questo controllo per aggiungere le tabelle al documento.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Per creare un controllo contenuto che visualizza i blocchi predefiniti

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Il codice inizializza l'oggetto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> dichiarato in precedenza. Il <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> consente di visualizzare tutti i blocchi predefiniti definiti nella categoria **informazioni su dipendenti e clienti** e che hanno il tipo di blocco predefinito `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>Il progetto di test
 Gli utenti possono fare clic sui controlli della raccolta di blocchi predefiniti nel documento per inserire la tabella dei dipendenti o la tabella dei suggerimenti dei clienti. Gli utenti possono digitare o selezionare le risposte nei controlli contenuto in entrambe le tabelle. Gli utenti possono modificare altre parti della tabella dei suggerimenti dei clienti, ma non devono poter modificare altre parti della tabella dei dipendenti.

### <a name="to-test-the-employee-table"></a>Per testare la tabella dei dipendenti

1. Premere **F5** per eseguire il progetto.

2. Fare clic su **scegliere il primo blocco predefinito** per visualizzare il primo controllo contenuto della raccolta di blocco predefinito.

3. Fare clic sulla freccia giù accanto al **raccolta personalizzata 1** intestazione nel controllo e selezionare **Employee Table**.

4. Fare clic nella cella a destra del **Employee Name** cella e digitare un nome.

     Verificare di poter aggiungere solo testo alla cella. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> consente agli utenti di aggiungere solo testo, non altri tipi di contenuto, ad esempio grafici o tabelle.

5. Fare clic nella cella a destra del **Data assunzione** cella e selezionare una data nella selezione data.

6. Fare clic nella cella a destra del **titolo** di cella e selezionare uno dei titoli professionali nella casella combinata.

     Facoltativamente, digitare il nome di un titolo professionale non presente nell'elenco. <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>, infatti, consente agli utenti di effettuare una selezione da un elenco di voci oppure di digitare le voci personalizzate.

7. Fare clic sull'icona nella cella a destra del **Picture** di cella e selezionare un'immagine per visualizzarla.

8. Provare ad aggiungere e quindi a eliminare le righe o le colonne dalla tabella. Verificare che non sia possibile modificare la tabella. <xref:Microsoft.Office.Tools.Word.GroupContentControl> impedisce di apportare modifiche.

### <a name="to-test-the-customer-feedback-table"></a>Per testare la tabella dei suggerimenti dei clienti

1. Fare clic su **scegliere il secondo blocco predefinito** per visualizzare il secondo controllo contenuto della raccolta di blocco predefinito.

2. Fare clic sulla freccia giù accanto al **raccolta personalizzata 1** intestazione nel controllo e selezionare **tabella Customer**.

3. Fare clic nella cella a destra del **Customer Name** cella e digitare un nome.

4. Fare clic nella cella a destra del **valutazione soddisfazione** di cella e selezionare una delle opzioni disponibili.

     Verificare che non sia possibile digitare una voce personalizzata. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> consente di selezionare solo da un elenco di voci.

5. Fare clic nella cella a destra del **commenti** cella e digitare i commenti.

     Facoltativamente, aggiungere alcuni contenuti diversi dal testo, ad esempio un grafico o una tabella incorporata. <xref:Microsoft.Office.Tools.Word.RichTextContentControl> consente, infatti, agli utenti di aggiungere contenuti diversi dal testo.

6. Verificare di poter aggiungere e quindi eliminare le righe o le colonne dalla tabella. Ciò è possibile perché la tabella non è stata protetta inserendola in <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

7. Chiudere il modello.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere l'argomento seguente:

- Associare controlli contenuto a parti del codice XML, chiamate anche parti XML personalizzate, incorporate in un documento. Per altre informazioni, vedere [Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>Vedere anche
- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controlli del contenuto](../vsto/content-controls.md)
- [Procedura: Aggiungere controlli contenuto a documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Proteggere parti di documenti mediante controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
