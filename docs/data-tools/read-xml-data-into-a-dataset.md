---
title: Leggere i dati XML in un set di dati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c6c2ea2b46fcd05360e079dc84da9bfe807ff489
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="read-xml-data-into-a-dataset"></a>Leggere i dati XML in un set di dati
ADO.NET fornisce semplici metodi per lavorare con i dati XML. In questa procedura dettagliata, si crea un'applicazione Windows che carica i dati XML in un set di dati. Il set di dati viene visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo. Infine, uno schema XML in base al contenuto del file XML viene visualizzato in una casella di testo.

 Questa procedura dettagliata è costituita da cinque passaggi principali:

1.  Crea un nuovo progetto

2.  Creazione di un file XML da leggere nel set di dati

3.  Creazione dell'interfaccia utente

4.  Creazione del set di dati, la lettura del file XML e visualizzarli in un <xref:System.Windows.Forms.DataGridView> controllo

5.  Aggiunta di codice per visualizzare lo schema XML basato su un file XML in un <xref:System.Windows.Forms.TextBox> controllo

> [!NOTE]
>  Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere il **strumenti** dal menu **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio si crea un progetto di Visual Basic o Visual c# che contiene questa procedura dettagliata.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

4. Denominare il progetto **ReadingXML**, quindi scegliere **OK**.

     Il **ReadingXML** progetto viene creato e aggiunto a **Esplora**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generare il file XML da leggere nel set di dati
 Poiché questa procedura dettagliata si concentra sulla lettura di dati XML in un set di dati, viene fornito il contenuto di un file XML.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Per creare il file XML che verrà letto nel set di dati

1.  Nel **progetto** dal menu **Aggiungi nuovo elemento**.

2.  Selezionare **File XML**, denominare il file `authors.xml`, quindi selezionare **Aggiungi**.

     Il file XML viene caricato nella finestra di progettazione e pronto per la modifica.

3.  Incollare il codice seguente nell'editor, sotto la dichiarazione XML:

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4.  Nel **File** dal menu **salvare authors**.

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente
 L'interfaccia utente per questa applicazione è costituita dai seguenti elementi:

-   Oggetto <xref:System.Windows.Forms.DataGridView> controllo che visualizza il contenuto del file XML come dati.

-   Oggetto <xref:System.Windows.Forms.TextBox> controllo che visualizza lo schema XML per il file XML.

-   Due <xref:System.Windows.Forms.Button> controlli.

    -   Legge il file XML nel set di dati di un pulsante che viene visualizzato nel <xref:System.Windows.Forms.DataGridView> controllo.

    -   Un secondo pulsante estrae lo schema del set di dati e tramite un <xref:System.IO.StringWriter> viene visualizzato nel <xref:System.Windows.Forms.TextBox> controllo.

#### <a name="to-add-controls-to-the-form"></a>Per aggiungere controlli al form

1.  Aprire `Form1` nella visualizzazione progettazione.

2.  Dal **della casella degli strumenti**, trascinare i controlli seguenti nel form:

    -   Uno <xref:System.Windows.Forms.DataGridView> controllo

    -   Uno <xref:System.Windows.Forms.TextBox> controllo

    -   Due <xref:System.Windows.Forms.Button> controlli

3.  Impostare le proprietà seguenti:

    |Control|Proprietà|Impostazione|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Barre di scorrimento**|**Verticale**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**per**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**per**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Creare il set di dati che riceve i dati XML
 In questo passaggio si crea un nuovo set di dati denominato `authors`. Per ulteriori informazioni sui set di dati, vedere [strumenti Dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Per creare un nuovo set di dati che riceve i dati XML

1.  In **Esplora**, selezionare il file di origine per **Form1**e quindi selezionare il **Visualizza finestra di progettazione** pulsante il **Esplora** barra degli strumenti.

2.  Dal [casella degli strumenti, scheda dati](../ide/reference/toolbox-data-tab.md), trascinare un **DataSet** su **Form1**.

3.  Nel **Aggiungi set di dati** nella finestra di dialogo **dataset non tipizzato**, quindi selezionare **OK**.

     **DataSet1** viene aggiunto alla barra dei componenti.

4.  Nel **proprietà** finestra, impostare il **nome** e <xref:System.Data.DataSet.DataSetName%2A> le proprietà per`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Creare il gestore eventi per leggere il file XML nel set di dati
 Il **Read XML** pulsante legge il file XML nel set di dati. Proprietà viene quindi impostato sul <xref:System.Windows.Forms.DataGridView> controllo associarlo al set di dati.

#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Per aggiungere codice al gestore dell'evento ReadXmlButton_Click

1.  In **Esplora**, selezionare **Form1**e quindi selezionare il **Visualizza finestra di progettazione** pulsante il **Esplora** barra degli strumenti.

2.  Selezionare il **Read XML** pulsante.

     Il **Editor di codice** verrà visualizzato il `ReadXmlButton_Click` gestore dell'evento.

3.  Digitare il seguente codice nel `ReadXmlButton_Click` gestore eventi:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  Nel `ReadXMLButton_Click` codice del gestore eventi, modifica il `filepath =` voce per il percorso corretto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Creare il gestore eventi per visualizzare lo schema nella casella di testo
 Il **Show Schema** consente di creare un <xref:System.IO.StringWriter> oggetto che viene riempito con lo schema e viene visualizzato nel <xref:System.Windows.Forms.TextBox>controllo.

#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Per aggiungere codice al gestore dell'evento ShowSchemaButton_Click

1.  In **Esplora**selezionare **Form1**e quindi selezionare il **Visualizza finestra di progettazione** pulsante.

2.  Selezionare il **Show Schema** pulsante.

     Il **Editor di codice** verrà visualizzato il `ShowSchemaButton_Click` gestore dell'evento.

3.  Digitare il seguente codice nel `ShowSchemaButton_Click` gestore dell'evento.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Verificare il modulo
 È ora possibile testare il form per assicurarsi che tutto funzioni come previsto.

#### <a name="to-test-the-form"></a>Per verificare il modulo

1.  Selezionare **F5** per eseguire l'applicazione.

2.  Selezionare il **Read XML** pulsante.

     Il controllo DataGridView viene visualizzato il contenuto del file XML.

3.  Selezionare il **Show Schema** pulsante.

     Nella casella di testo viene visualizzato lo schema XML per il file XML.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base di lettura di un file XML in un set di dati, nonché la creazione di uno schema in base al contenuto del file XML. Ecco alcune attività che è possibile eseguire successivamente:

-   Modificare i dati nel set di dati e riscriverli come XML. Per altre informazioni, vedere <xref:System.Data.DataSet.WriteXml%2A>.

-   Modificare i dati nel set di dati e scriverlo in un database. Per ulteriori informazioni, vedere [salvataggio dati](../data-tools/saving-data.md).

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)