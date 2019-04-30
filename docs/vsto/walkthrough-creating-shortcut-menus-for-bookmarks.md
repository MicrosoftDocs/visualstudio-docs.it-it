---
title: 'Procedura dettagliata: Creare i menu di scelta rapida per segnalibri'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b4b412d2e9456142c1be1af388e2803634d15c0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438534"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Procedura dettagliata: Creare i menu di scelta rapida per segnalibri
  Questa procedura dettagliata viene illustrato come creare i menu di scelta rapida per <xref:Microsoft.Office.Tools.Word.Bookmark> controlli in una personalizzazione a livello di documento per Word. Quando un utente fa clic il testo in un segnalibro, un menu di scelta rapida viene visualizzata e fornisce le opzioni utente per la formattazione del testo.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- [Creare il progetto](#BKMK_CreateProject).

- [Aggiungere testo e i segnalibri nel documento](#BKMK_addtextandbookmarks).

- [Aggiungere comandi al menu di scelta rapida](#BKMK_AddCmndsShortMenu).

- [Formattare il testo nel segnalibro](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="BKMK_CreateProject"></a> Creare il progetto
 Il primo passaggio consiste nel creare un progetto documento di Word in Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

- Creare un progetto documento di Word con il nome **risorse del Menu di scelta rapida di segnalibro**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **risorse del Menu di scelta rapida di segnalibro** progetto al **Esplora soluzioni**.

## <a name="BKMK_addtextandbookmarks"></a> Aggiungere testo e i segnalibri nel documento
 Aggiungere testo al documento e quindi aggiungere due segnalibri sovrapposti.

### <a name="to-add-text-to-your-document"></a>Per aggiungere testo al documento

- Nel documento che viene visualizzato nella finestra di progettazione del progetto, digitare il testo seguente.

     **Questo è un esempio di creazione di un menu di scelta rapida facendo clic sul testo nel segnalibro.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Per aggiungere un controllo Bookmark a un documento

1. Nel **casella degli strumenti**, dalle **controlli Word** scheda, trascinare un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo al documento.

    Il **Aggiungi controllo Bookmark** verrà visualizzata la finestra di dialogo.

2. Selezionare le parole "Creazione di un menu di scelta rapida si fa clic con il pulsante destro del testo", quindi fare clic su **OK**.

    `bookmark1` viene aggiunto al documento.

3. Aggiungere un altro <xref:Microsoft.Office.Tools.Word.Bookmark> controllare con le parole "fare clic sul testo all'interno di un segnalibro".

    `bookmark2` viene aggiunto al documento.

   > [!NOTE]
   > Le parole "pulsante destro del mouse il testo" sono entrambi `bookmark1` e `bookmark2`.

   Quando si aggiunge un segnalibro a un documento in fase di progettazione, un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo viene creato. È possibile programmare usando diversi eventi del segnalibro. È possibile scrivere codice <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> evento del segnalibro, in modo che quando l'utente fa clic il testo nel segnalibro, viene visualizzato un menu di scelta rapida.

## <a name="BKMK_AddCmndsShortMenu"></a> Aggiungere comandi al menu di scelta rapida
 Aggiungere pulsanti al menu di scelta rapida visualizzato facendo clic sul documento.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Per aggiungere comandi al menu di scelta rapida

1. Aggiungere un **XML della barra multifunzione** elemento al progetto. Per altre informazioni, vedere [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Nelle **Esplora soluzioni**, selezionare **ThisDocument.cs** oppure **ThisDocument. vb**.

3. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il **ThisDocument** classe file viene aperto nell'Editor del codice.

4. Aggiungere il codice seguente per il **ThisDocument** classe. Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe XML della barra multifunzione all'applicazione di Office.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. In **Esplora soluzioni**selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è denominato Ribbon1.xml.

6. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il file XML della barra multifunzione viene aperto nell'editor di codice.

7. Nell'Editor di codice, sostituire il contenuto del file XML della barra multifunzione con il codice seguente.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Questo codice aggiunge due pulsanti al menu di scelta rapida visualizzato facendo clic sul documento.

8. Nelle **Esplora soluzioni**, fare doppio clic su `ThisDocument`, quindi fare clic su **Visualizza codice**.

9. Dichiarare le variabili seguenti e una variabile segnalibri a livello di classe.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. Nelle **Esplora soluzioni**, selezionare il file di codice della barra multifunzione. Per impostazione predefinita, il file di codice della barra multifunzione è denominato **Ribbon1.cs** oppure **Ribbon1.vb**.

11. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il file di codice della barra multifunzione viene aperto nell'editor di codice.

12. Nel file di codice della barra multifunzione, aggiungere il metodo seguente. Si tratta di un metodo di callback per i due pulsanti che sono stati aggiunti al menu di scelta rapida del documento. Questo metodo determina se questi pulsanti vengono visualizzati nel menu di scelta rapida. I pulsanti in grassetto e corsivo vengono visualizzati solo se facendo clic all'interno del segnalibro.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="BKMK_formattextbkmk"></a> Formattare il testo nel segnalibro

### <a name="to-format-the-text-in-the-bookmark"></a>Per formattare il testo nel segnalibro

1. Nel file di codice della barra multifunzione, aggiungere un `ButtonClick` gestore dell'evento per applicare la formattazione al segnalibro.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **Esplora soluzioni**, selezionare **ThisDocument.cs** oppure **ThisDocument. vb**.

3. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il **ThisDocument** classe file viene aperto nell'Editor del codice.

4. Aggiungere il codice seguente per il **ThisDocument** classe.

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > È necessario scrivere codice per gestire il caso in cui si sovrappongono segnalibri. In caso contrario, per impostazione predefinita, il codice verrà chiamato per tutti i segnalibri nella selezione.

5. In c#, è necessario aggiungere i gestori eventi per i controlli segnalibro di <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Per informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>Testare l'applicazione
 Testare il documento per verificare che le voci di menu in grassetto e corsivo vengono visualizzati nel menu di scelta rapida facendo clic su testo in un segnalibro e che il testo è formattato correttamente.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Fare doppio clic nel primo segnalibro e quindi fare clic su **grassetto**.

3. Verificare che tutto il testo in `bookmark1` viene formattato come grassetto.

4. Pulsante destro del mouse il testo in cui si sovrappongono i segnalibri, quindi fare clic su **corsivo**.

5. Verificare che tutto il testo nelle `bookmark2` corsivo e solo la parte del testo nel `bookmark1` sovrapposta `bookmark2` è in corsivo.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Scrivere codice per rispondere agli eventi dei controlli host di Excel. Per altre informazioni, vedere [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Usare una casella di controllo per modificare la formattazione in un segnalibro. Per altre informazioni, vedere [Procedura dettagliata: Modifica la formattazione dei documenti mediante controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedere anche
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Bookmark (controllo)](../vsto/bookmark-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
