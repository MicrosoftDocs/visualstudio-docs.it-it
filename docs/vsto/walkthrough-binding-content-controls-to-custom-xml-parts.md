---
title: 'Procedura dettagliata: Associazione di controlli contenuto a parti XML personalizzate | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ca9c3e049d29874419327ec4ac7d71e0537466c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-content-controls-to-custom-xml-parts"></a>Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate
  Questa procedura dettagliata illustra come associare i controlli contenuto in una personalizzazione a livello di documento per Word a dati XML archiviati nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word consente di archiviare dati XML, denominati *parti XML personalizzate*, in un documento. È possibile controllare la visualizzazione di questi dati associando i controlli contenuto a elementi in una parte XML personalizzata. Il documento di esempio in questa procedura dettagliata visualizza informazioni sui dipendenti che vengono archiviate in una parte XML personalizzata. Quando si apre il documento, i controlli contenuto visualizzano i valori degli elementi XML. Nella parte XML personalizzata vengono salvate le eventuali modifiche apportate al testo nei controlli contenuto.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di controlli contenuto al documento di Word presente in un progetto a livello di documento in fase di progettazione.  
  
-   Creazione di un file di dati XML e di uno schema XML che definisce gli elementi da associare ai controlli contenuto.  
  
-   Associazione dello schema XML al documento in fase di progettazione.  
  
-   Aggiunta dei contenuti del file XML a una parte XML personalizzata nel documento in fase di progettazione.  
  
-   Binding dei controlli contenuto a elementi nella parte XML personalizzata.  
  
-   Binding di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori definiti nello schema XML.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-a-new-word-document-project"></a>Creazione di un nuovo progetto di documento di Word  
 Creare un documento di Word che verrà usato nella procedura dettagliata.  
  
#### <a name="to-create-a-new-word-document-project"></a>Per creare un progetto di documento di Word  
  
1.  Creare un progetto documento di Word con il nome **EmployeeControls**. Creare un nuovo documento per la soluzione. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Apre il nuovo documento di Word nella finestra di progettazione e aggiunge i **EmployeeControls** progetto **Esplora**.  
  
## <a name="adding-content-controls-to-the-document"></a>Aggiunta di controlli contenuto al documento  
 Creare una tabella che contiene tre tipi diversi di controlli contenuto in cui un utente può visualizzare o modificare informazioni su un dipendente.  
  
#### <a name="to-add-content-controls-to-the-document"></a>Per aggiungere controlli contenuto al documento  
  
1.  Nel documento di Word ospitato nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progettazione della barra multifunzione scegliere la **inserire** scheda.  
  
2.  Nel **tabelle** gruppo **tabella**e inserire una tabella con 2 colonne e 3 righe.  
  
3.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |**Nome del dipendente**|  
    |**Data di assunzione**|  
    |**Titolo**|  
  
4.  Nella seconda colonna della tabella, scegliere la prima riga (accanto a **nome dipendente**).  
  
5.  Sulla barra multifunzione, scegliere il **Developer** scheda.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Nel **controlli** gruppo, scegliere il **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.  
  
7.  Nella seconda colonna della tabella, scegliere la seconda riga (accanto a **Data assunzione**).  
  
8.  Nel **controlli** gruppo, scegliere il **selezione data** pulsante ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.  
  
9. Nella seconda colonna della tabella, selezionare la terza riga (accanto a **titolo**).  
  
10. Nel **controlli** gruppo, scegliere il **riepilogo** pulsante ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") da aggiungere un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> all'ultima cella.  
  
 È l'intera interfaccia utente per questo progetto. Se si esegue il progetto a questo punto, è possibile digitare un testo nella prima riga e selezionare una data nella seconda riga. Il passaggio successivo consiste nell'allegare i dati che si vogliano visualizzare al documento in un file XML.  
  
## <a name="creating-the-xml-data-file"></a>Creazione di file di dati XML  
 In genere, si ottengono dati XML da archiviare in una parte XML personalizzata da un'origine esterna, ad esempio un file o un database. In questa procedura dettagliata è possibile creare un file XML che contiene i dati del dipendente, contrassegnati da elementi che verranno associati ai controlli contenuto del documento. Per rendere disponibili i dati in fase di esecuzione, incorporare il file XML come risorsa nell'assembly di personalizzazione.  
  
#### <a name="to-create-the-data-file"></a>Per creare il file di dati  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel **modelli** riquadro, selezionare **File XML**.  
  
3.  Nome del file **employees.xml**, quindi scegliere il **Aggiungi** pulsante.  
  
     Il **employees.xml** file verrà aperto nell'Editor di codice.  
  
4.  Sostituire il contenuto del **employees.xml** file con il testo seguente.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  In **Esplora**, scegliere il **employees.xml** file.  
  
6.  Nel **proprietà** finestra, seleziona il **azione di compilazione** , proprietà e quindi modificare il valore di **risorsa incorporata**.  
  
     Questo passaggio incorpora il file XML come risorsa nell'assembly quando si compila il progetto. e consente di accedere al contenuto del file XML in fase di esecuzione.  
  
## <a name="creating-an-xml-schema"></a>Creazione di uno schema XML  
 Se si intende associare un controllo contenuto a un singolo elemento in una parte XML personalizzata, non è necessario usare uno schema XML. Tuttavia, per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori, è necessario creare uno schema XML che convalida il file di dati XML creato in precedenza. Lo schema XML definisce i valori possibili per l'elemento `title`. L'associazione di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a questo elemento viene eseguita più avanti in questa procedura dettagliata.  
  
#### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel **modelli** riquadro, selezionare **XML Schema**.  
  
3.  Nome dello schema **employees.xsd** e scegliere il **Aggiungi** pulsante.  
  
     Viene aperta la progettazione schema.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per **employees.xsd**, quindi scegliere **Visualizza codice**.  
  
5.  Sostituire il contenuto del **employees.xsd** file con lo schema seguente.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Nel **File** menu, fare clic su **Salva tutto** per salvare le modifiche apportate al **employees.xml** e **employees.xsd** file.  
  
## <a name="attaching-the-xml-schema-to-the-document"></a>Associazione dello schema XML al documento  
 È necessario allegare lo schema XML al documento per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ai valori validi dell'elemento `title`.  
  
#### <a name="to-attach-the-xml-schema-to-the-document-includeword15shortvstoincludesword-15-short-mdmd"></a>Per allegare lo schema XML al documento ([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Attivare **EmployeeControls.docx** nella finestra di progettazione.  
  
2.  Sulla barra multifunzione, scegliere il **Developer** scheda e quindi scegliere il **Add-Ins** pulsante.  
  
3.  Nel **modelli e componenti aggiuntivi** finestra di dialogo scegliere la **XML Schema** scheda e quindi scegliere il **Aggiungi Schema** pulsante.  
  
4.  Individuare il **employees.xsd** schema creato in precedenza, che si trova nella directory del progetto e quindi scegliere il **aprire** pulsante.  
  
5.  Scegliere il **OK** pulsante il **impostazioni Schema** la finestra di dialogo.  
  
6.  Scegliere il **OK** per chiudere la **modelli e componenti aggiuntivi** la finestra di dialogo.  
  
#### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Per allegare lo schema XML al documento (Word 2010)  
  
1.  Attivare **EmployeeControls.docx** nella finestra di progettazione.  
  
2.  Sulla barra multifunzione, scegliere il **Developer** scheda.  
  
3.  Nel **XML** gruppo, scegliere il **Schema** pulsante.  
  
4.  Nel **modelli e componenti aggiuntivi** finestra di dialogo scegliere la **XML Schema** scheda e quindi scegliere il **Aggiungi Schema** pulsante.  
  
5.  Individuare il **employees.xsd** schema creato in precedenza, che si trova nella directory del progetto e scelga il **aprire** pulsante.  
  
6.  Scegliere il **OK** pulsante il **impostazioni Schema** la finestra di dialogo.  
  
7.  Scegliere il **OK** per chiudere la **modelli e componenti aggiuntivi** la finestra di dialogo.  
  
     Il **struttura XML** Visualizza il riquadro attività.  
  
8.  Chiudi il **struttura XML** riquadro attività.  
  
## <a name="adding-a-custom-xml-part-to-the-document"></a>Aggiunta di una parte XML personalizzata al documento  
 Prima di poter associare i controlli contenuto a elementi nel file XML, è necessario aggiungere il contenuto del file XML a una nuova parte XML personalizzata nel documento.  
  
#### <a name="to-add-a-custom-xml-part-to-the-document"></a>Per aggiungere una parte XML personalizzata al documento  
  
1.  In **Esplora**, aprire il menu di scelta rapida per **ThisDocument. cs** o **ThisDocument. vb**, quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere le seguenti dichiarazioni alla classe `ThisDocument`. Questo codice dichiara diversi oggetti che verranno usati per aggiungere una parte XML personalizzata al documento.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `ThisDocument` . Questo metodo ottiene il contenuto del file di dati XML incorporato come risorsa nell'assembly e restituisce il contenuto come stringa XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Aggiungere il metodo seguente alla classe `ThisDocument` . Il metodo crea `AddCustomXmlPart` una nuova parte XML personalizzata che contiene una stringa XML che viene passata al metodo.  
  
     Per garantire che la parte XML personalizzata venga creata solo una volta, il metodo crea la parte XML personalizzata solo se non esiste già nel documento una parte XML personalizzata con GUID corrispondente. La prima volta che viene chiamato questo metodo, viene salvato il valore della proprietà <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> per la stringa `employeeXMLPartID`. Il valore della stringa `employeeXMLPartID` viene mantenuto nel documento perché è stato dichiarato mediante l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="binding-the-content-controls-to-elements-in-the-custom-xml-part"></a>Associazione dei controlli contenuto a elementi nella parte XML personalizzata  
 Associare ogni controllo contenuto a un elemento nella parte XML personalizzata usando il **XMLMapping** proprietà di ogni controllo contenuto.  
  
#### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Per associare i controlli contenuto a elementi nella parte XML personalizzata  
  
1.  Aggiungere il metodo seguente alla classe `ThisDocument` . Questo metodo associa ogni controllo del contenuto a un elemento nella parte XML personalizzata e imposta il formato di visualizzazione della data di <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="running-your-code-when-the-document-is-opened"></a>Esecuzione di codice quando il documento è aperto  
 Creare la parte XML personalizzata e associare i controlli personalizzati ai dati quando il documento viene aperto.  
  
#### <a name="to-run-your-code-when-the-document-is-opened"></a>Per eseguire il codice quando il documento è aperto  
  
1.  Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice ottiene la stringa XML dal **employees.xml** file, aggiunge la stringa XML a una nuova parte XML personalizzata nel documento e associa i controlli contenuto agli elementi nella parte XML personalizzata.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="testing-the-project"></a>Test del progetto  
 Quando si apre il documento, i controlli contenuto consentono di visualizzare dati dagli elementi nella parte XML personalizzata. È possibile fare clic il <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> per selezionare uno dei tre valori validi per il `title` elemento, che sono definiti nel **employees.xsd** file. Se si modificano i dati in uno dei controlli contenuto, i nuovi valori vengono salvati nella parte XML personalizzata del documento.  
  
#### <a name="to-test-the-content-controls"></a>Per testare i controlli contenuto  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che la tabella nel documento sia simile alla tabella seguente. Tutte le stringhe della seconda colonna sono ottenute da un elemento nella parte XML personalizzata del documento.  
  
    |||  
    |-|-|  
    |**Nome del dipendente**|**Karina Leal**|  
    |**Data di assunzione**|**1 aprile 1999**|  
    |**Titolo**|**Manager**|  
  
3.  Scegliere la cella a destra del **nome dipendente** di cella e digitare un nome diverso.  
  
4.  Scegliere la cella a destra del **Data assunzione** e selezionare una data diversa nella selezione data.  
  
5.  Scegliere la cella a destra del **titolo** di cella e selezionare un nuovo elemento nell'elenco a discesa.  
  
6.  Salvare e chiudere il documento.  
  
7.  In Esplora file aprire la cartella \bin\Debug nel percorso del progetto.  
  
8.  Aprire il menu di scelta rapida per **EmployeeControls.docx** e quindi scegliere **rinominare**.  
  
9. Nome del file **EmployeeControls.docx.zip**.  
  
     Il **EmployeeControls.docx** documento viene salvato in formato Open XML. Il documento è stato rinominato con l'estensione del nome file zip e quindi è possibile esaminarne il contenuto. Per ulteriori informazioni sul formato Open XML, vedere l'articolo tecnico [Introduzione ai formati Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Aprire il **EmployeeControls.docx.zip** file.  
  
11. Aprire il **customXml** cartella.  
  
12. Aprire il menu di scelta rapida per **item2.xml** e quindi scegliere **aprire**.  
  
     Il file contiene la parte XML personalizzata che è stata aggiunta al documento.  
  
13. Verificare che gli elementi `name`, `hireDate` e `title` contengano i nuovi valori immessi nei controlli contenuto nel documento.  
  
14. Chiudi il **item2.xml** file.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere gli argomenti seguenti:  
  
-   Usare tutti i controlli contenuto disponibili per creare un modello. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un modello per i controlli del contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modificare i dati nella parte XML personalizzata mentre il documento è chiuso. Alla successiva apertura del documento, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.  
  
-   Usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: proteggere parti di documenti mediante controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  