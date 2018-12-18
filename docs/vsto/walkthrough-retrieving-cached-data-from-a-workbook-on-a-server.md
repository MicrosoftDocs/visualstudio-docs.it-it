---
title: 'Procedura dettagliata: Recupero di dati memorizzati nella cache da una cartella di lavoro in un Server | Documenti Microsoft'
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
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 080cbf3d8985f9bcbf1affebfc988a7be61f7818
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-retrieving-cached-data-from-a-workbook-on-a-server"></a>Procedura dettagliata: recupero dei dati memorizzati nella cache di una cartella di lavoro contenuta in un server
  Questa procedura dettagliata illustra come recuperare dati da un set di dati memorizzato nella cache di una cartella di lavoro di Microsoft Office Excel senza avviare Excel utilizzando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Definizione di un set di dati che contiene i dati dal database AdventureWorksLT.  
  
-   Creazione di istanze del set di dati in un progetto cartella di lavoro di Excel e un progetto applicazione console.  
  
-   Creazione di un <xref:Microsoft.Office.Tools.Excel.ListObject> che è associato al set di dati nella cartella di lavoro e il popolamento di <xref:Microsoft.Office.Tools.Excel.ListObject> con i dati quando viene aperta la cartella di lavoro.  
  
-   Aggiunta di set di dati nella cartella di lavoro per la cache dei dati.  
  
-   Lettura dei dati dal set di dati memorizzati nella cache nel set di dati nell'applicazione console, senza avviare Excel.  
  
 Sebbene questa procedura dettagliata si presuppone che si esegue il codice nel computer di sviluppo, è possibile utilizzare il codice illustrato in questa procedura dettagliata in un server che non dispongono di Excel installato.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un'istanza in esecuzione di Microsoft SQL Server o Microsoft SQL Server Express con database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:  
  
    -   Per collegare un database con SQL Server Management Studio o SQL Server Management Studio Express, vedere [Procedura: Collegamento di un database (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Per collegare un database usando la riga di comando, vedere [Procedura: Collegamento di un file di database a SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Crea un progetto libreria di classi che definisce un set di dati  
 Per utilizzare lo stesso set di dati in un progetto cartella di lavoro di Excel e un'applicazione console, è necessario definire il set di dati in un assembly separato a cui fa riferimento a entrambi questi progetti. Questa procedura dettagliata, definire il set di dati in un progetto libreria di classi.  
  
#### <a name="to-create-the-class-library-project"></a>Per creare il progetto libreria di classi  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro modelli espandere **Visual c#** o **Visual Basic**, quindi fare clic su **Windows**.  
  
4.  Nell'elenco dei modelli di progetto, selezionare **libreria di classi**.  
  
5.  Nel **nome** digitare **AdventureWorksDataSet**.  
  
6.  Fare clic su **Sfoglia**, passare alla cartella %UserProfile%\Documents (per Windows Vista) o %UserProfile%\My documenti (per Windows XP e versioni precedenti) e quindi fare clic su **selezionare la cartella**.  
  
7.  Nel **nuovo progetto** finestra di dialogo, verificare che il **Crea directory per soluzione** casella di controllo è deselezionata.  
  
8.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **AdventureWorksDataSet** progetto **Esplora** e apre il **Class1. cs** o **Class1. vb** file di codice.  
  
9. In **Esplora**, fare doppio clic su **Class1.cs** o **Class1. vb**e quindi fare clic su **eliminare**. Questo file non è necessario per questa procedura dettagliata.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>La definizione di un set di dati nel progetto libreria di classi  
 Definire un dataset tipizzato che contiene i dati dal database AdventureWorksLT per SQL Server 2005. Più avanti in questa procedura dettagliata, si farà riferimento questo set di dati da un progetto di cartella di lavoro di Excel e un progetto applicazione console.  
  
 Il set di dati è un *dataset tipizzato* che rappresenta i dati nella tabella Product del database AdventureWorksLT. Per ulteriori informazioni sui dataset tipizzati, vedere [strumenti Dataset in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Per definire un set di dati tipizzato nel progetto libreria di classi  
  
1.  In **Esplora**, fare clic su di **AdventureWorksDataSet** progetto.  
  
2.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre**e **Origini dati**dalla barra dei menu.  
  
3.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
4.  Selezionare **Database**e quindi scegliere **Avanti**.  
  
5.  Se si dispone di una connessione esistente al database AdventureWorksLT, selezionarla e fare clic su **Avanti**.  
  
     In caso contrario, scegliere **Nuova connessione**e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.  
  
7.  Nel **Seleziona oggetti di Database** espandere **tabelle** e selezionare **Product (SalesLT)**.  
  
8.  Scegliere **Fine**.  
  
     Il file AdventureWorksLTDataSet.xsd viene aggiunto per il **AdventureWorksDataSet** progetto. Questo file definisce gli elementi seguenti:  
  
    -   Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta il contenuto della tabella Product nel database AdventureWorksLT.  
  
    -   Un oggetto TableAdapter denominato `ProductTableAdapter`. Questo oggetto TableAdapter può essere utilizzato per leggere e scrivere dati `AdventureWorksLTDataSet`. Per altre informazioni, vedere [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.  
  
9. In **Esplora**, fare doppio clic su **AdventureWorksDataSet** e fare clic su **compilare**.  
  
     Verificare che il progetto venga compilato senza errori.  
  
## <a name="creating-an-excel-workbook-project"></a>Creazione di un progetto Cartella di lavoro di Excel  
 Creare un progetto di cartella di lavoro di Excel per l'interfaccia per i dati. Più avanti in questa procedura dettagliata, si creerà un <xref:Microsoft.Office.Tools.Excel.ListObject> che visualizza i dati e si aggiungerà un'istanza del set di dati nella cache di dati nella cartella di lavoro.  
  
#### <a name="to-create-the-excel-workbook-project"></a>Per creare il progetto di cartella di lavoro di Excel  
  
1.  In **Esplora**, fare doppio clic su di **AdventureWorksDataSet** soluzione, scegliere **Aggiungi**e quindi fare clic su **nuovo progetto**.  
  
2.  Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.  
  
3.  Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .  
  
4.  Nell'elenco di modelli di progetto selezionare il progetto **Cartella di lavoro di Excel 2010** o **Cartella di lavoro di Excel 2013** .  
  
5.  Nel **nome** digitare **AdventureWorksReport**. Non modificare il percorso.  
  
6.  Fare clic su **OK**.  
  
     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .  
  
7.  Verificare che **creare un nuovo documento** sia selezionata e fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Apre il **AdventureWorksReport** cartella di lavoro nella finestra di progettazione e aggiunge il **AdventureWorksReport** progetto **Esplora**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Aggiunta di set di dati a origini dati nel progetto di cartella di lavoro di Excel  
 Prima di poter visualizzare il set di dati della cartella di lavoro di Excel, è innanzitutto necessario aggiungere il set di dati alle origini dati nel progetto di cartella di lavoro di Excel.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Per aggiungere il set di dati alle origini dati nel progetto di cartella di lavoro di Excel  
  
1.  In **Esplora**, fare doppio clic su **Sheet1. cs** o **Sheet1. vb** sotto il **AdventureWorksReport** progetto.  
  
     Consente di aprire la cartella di lavoro nella finestra di progettazione.  
  
2.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Il **configurazione guidata origine dati** apre.  
  
3.  Fare clic su **oggetto**, quindi fare clic su **Avanti**.  
  
4.  Nel **selezionare l'oggetto da associare** alla pagina, fare clic su **Aggiungi riferimento**.  
  
5.  Nel **progetti** scheda, fare clic su **AdventureWorksDataSet** e quindi fare clic su **OK**.  
  
6.  Sotto il **AdventureWorksDataSet** dello spazio dei nomi del **AdventureWorksDataSet** assembly, fare clic su **AdventureWorksLTDataSet** e quindi fare clic su **fine** .  
  
     Il **origini dati** verrà visualizzata la finestra, e **AdventureWorksLTDataSet** viene aggiunto all'elenco di origini dati.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creazione di un controllo ListObject associato a un'istanza del set di dati  
 Per visualizzare il set di dati nella cartella di lavoro, creare un <xref:Microsoft.Office.Tools.Excel.ListObject> associato a un'istanza del set di dati. Per altre informazioni sull'associazione dei controlli ai dati, vedere [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Per creare un controllo ListObject associato a un'istanza del set di dati  
  
1.  Nel **origini dati** finestra, espandere il **AdventureWorksLTDataSet** nodo **AdventureWorksDataSet**.  
  
2.  Selezionare il **prodotto** nodo, fare clic sulla freccia giù visualizzata e selezionarla **ListObject** nell'elenco a discesa.  
  
     Se non viene visualizzata la freccia a discesa, verificare che la cartella di lavoro è aperta nella finestra di progettazione.  
  
3.  Trascinare il **prodotto** alla cella A1.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `productListObject` viene creato nel foglio di lavoro, a partire dalla cella A1. Allo stesso tempo, un oggetto dataset denominato `adventureWorksLTDataSet` e <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource` vengono aggiunti al progetto. <xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Aggiunta di set di dati nella Cache di dati  
 Per consentire al codice all'esterno del progetto di cartella di lavoro di Excel per accedere ai set di dati nella cartella di lavoro, è necessario aggiungere il set di dati per la cache dei dati. Per ulteriori informazioni sulla cache di dati, vedere [dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md) e [la memorizzazione nella cache dati](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>Per aggiungere il set di dati nella cache di dati  
  
1.  Nella finestra di progettazione, fare clic su **adventureWorksLTDataSet**.  
  
2.  Nel **proprietà** finestra, impostare il **modificatori** proprietà **pubblica**.  
  
3.  Impostare il **CacheInDocument** proprietà **True**.  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>L'inizializzazione del set di dati nella cartella di lavoro  
 Prima di poter recuperare i dati dal set di dati memorizzati nella cache tramite l'applicazione console, è necessario innanzitutto popolare il set di dati memorizzati nella cache con i dati.  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>Per inizializzare il set di dati nella cartella di lavoro  
  
1.  In **Esplora**, fare doppio clic su di **Sheet1. cs** o **Sheet1. vb** file e fare clic su **Visualizza codice**.  
  
2.  Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Questo codice viene utilizzata un'istanza di `ProductTableAdapter` classe definita nel **AdventureWorksDataSet** progetto per riempire il set di dati memorizzati nella cache con dati, se è attualmente vuota.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Compilare ed eseguire il progetto di cartella di lavoro di Excel per garantire che questa venga compilata e viene eseguito senza errori. Questa operazione, inoltre, viene compilato il set di dati memorizzati nella cache e Salva i dati nella cartella di lavoro.  
  
#### <a name="to-build-and-run-the-project"></a>Per compilare ed eseguire il progetto  
  
1.  In **Esplora**, fare doppio clic su di **AdventureWorksReport** del progetto, scegliere **Debug**e quindi fare clic su **Avvia nuova istanza**.  
  
     Il progetto viene compilato e la cartella di lavoro viene aperto in Excel. Verificare quanto segue:  
  
    -   Il <xref:Microsoft.Office.Tools.Excel.ListObject> inserisce i dati.  
  
    -   Il valore di **ListPrice** colonna per la prima riga del <xref:Microsoft.Office.Tools.Excel.ListObject> è 1431.5. Più avanti in questa procedura dettagliata, si utilizzerà un'applicazione console per modificare i valori di **ListPrice** colonna.  
  
2.  Salvare la cartella di lavoro. Non modificare il nome del file o il percorso della cartella di lavoro.  
  
3.  Chiudere Excel.  
  
## <a name="creating-a-console-application-project"></a>Creazione di un progetto di applicazione Console  
 Creare un progetto di applicazione console da utilizzare per modificare i dati nel set di dati memorizzati nella cache nella cartella di lavoro.  
  
#### <a name="to-create-the-console-application-project"></a>Per creare il progetto di applicazione console  
  
1.  In **Esplora**, fare doppio clic su di **AdventureWorksDataSet** soluzione, scegliere **Aggiungi**e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **tipi di progetto** riquadro espandere **Visual c#** o **Visual Basic**, quindi fare clic su **Windows**.  
  
3.  Nel **modelli** riquadro, selezionare **applicazione Console**.  
  
4.  Nel **nome** digitare **DataReader**. Non modificare il percorso.  
  
5.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **DataReader** progetto **Esplora** e apre il **Program.cs** o **Module1. vb** file di codice.  
  
## <a name="retrieving-data-from-the-cached-dataset-by-using-the-console-application"></a>Il recupero dei dati dal set di dati memorizzati nella cache tramite l'applicazione Console  
 Utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'applicazione console per leggere i dati in una classe locale `AdventureWorksLTDataSet` oggetto. Per verificare che il set di dati locale è stato inizializzato con i dati dal set di dati memorizzati nella cache, l'applicazione visualizza il numero di righe nel set di dati locale.  
  
#### <a name="to-retrieve-data-from-the-cached-dataset"></a>Per recuperare i dati dal set di dati memorizzati nella cache  
  
1.  In **Esplora**, fare doppio clic su di **DataReader** sul progetto e scegliere **Aggiungi riferimento**.  
  
2.  Nel **.NET** selezionare ServerDocument.  
  
3.  Fare clic su **OK**.  
  
4.  In **Esplora**, fare doppio clic su di **DataReader** sul progetto e scegliere **Aggiungi riferimento**.  
  
5.  Nel **progetti** , selezionare **AdventureWorksDataSet**, fare clic su **OK**.  
  
6.  Aprire il file Program.cs o Module1. vb nell'Editor di codice.  
  
7.  Aggiungere il seguente **utilizzando** (per c#) o **importazioni** (per Visual Basic) all'inizio del file di codice.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Aggiungere al metodo `Main` il seguente codice. Questo codice dichiara gli oggetti seguenti:  
  
    -   Un'istanza di `AdventureWorksLTDataSet` tipo definito nel **AdventureWorksDataSet** progetto.  
  
    -   Il percorso alla cartella di lavoro AdventureWorksReport nella cartella di compilazione di **AdventureWorksReport** progetto.  
  
    -   Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> oggetto da usare per accedere alla cache di dati nella cartella di lavoro.  
  
        > [!NOTE]  
        >  Il codice seguente si presuppone che la cartella di lavoro viene salvato con estensione xlsx. Se la cartella di lavoro nel progetto è un'estensione diversa, modificare il percorso in base alle esigenze.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Aggiungere il codice seguente per il `Main` (metodo), dopo il codice aggiunto nel passaggio precedente. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Usa il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per accedere al dataset memorizzato nella cartella di lavoro.  
  
    -   Legge i dati dal set di dati memorizzati nella cache nel set di dati locale.  
  
    -   Visualizza il numero di righe nel set di dati locale, per verificare che disponga di dati.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. Nel **compilare** menu, fare clic su **Compila DataReader**.  
  
## <a name="testing-the-project"></a>Test del progetto  
 Quando si esegue l'applicazione console, Visualizza il numero di righe nel set di dati locale.  
  
#### <a name="to-test-the-workbook"></a>Per testare la cartella di lavoro  
  
1.  In **Esplora**, fare doppio clic su di **DataReader** , scegliere **Debug**e quindi fare clic su **Avvia nuova istanza**.  
  
     Verificare che l'applicazione indica che il set di dati locale ha 295 righe.  
  
2.  Premere INVIO per chiudere l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per ulteriori informazioni sull'utilizzo di dati memorizzati nella cache gli argomenti seguenti informazioni:  
  
-   Modifica dei dati in un dataset memorizzato nella cache senza avviare Excel. Per ulteriori informazioni, vedere [procedura dettagliata: modifica di dati memorizzati nella cache in una cartella di lavoro in un Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Inserimento di dati in una cartella di lavoro in un Server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Procedura dettagliata: Modifica dei dati memorizzati in una cartella di lavoro in un Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Connessione ai dati nelle applicazioni Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  