---
title: Elementi host e Cenni preliminari sui controlli Host | Documenti Microsoft
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
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1512b4774efea9639f01135932ad076f6630ea12
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="host-items-and-host-controls-overview"></a>Panoramica degli elementi e dei controlli host
  Gli elementi e i controlli host sono tipi che consentono di fornire il modello di programmazione per le soluzioni Office create tramite gli strumenti di sviluppo di Office in Visual Studio. Rendono l'interazione con i modelli a oggetti di Microsoft Office Word e Microsoft Office Excel, basati su COM, analoga all'interazione con gli oggetti gestiti, ad esempio i controlli Windows Form.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Elementi host  
 Gli elementi host sono tipi che si trovano al livello più elevato delle gerarchie del modello a oggetti nei progetti di Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] definisce gli elementi host seguenti per le soluzioni Word ed Excel:  
  
-   <xref:Microsoft.Office.Tools.Word.Document>  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Ognuno di questi tipi estende un oggetto presente a livello nativo nel modello a oggetti di Word o Excel, denominato *oggetto nativo di Office*. Ad esempio, l'elemento host <xref:Microsoft.Office.Tools.Word.Document> estende l'oggetto <xref:Microsoft.Office.Interop.Word.Document> , definito nell'assembly di interoperabilità primario per Word.  
  
 Gli elementi host hanno generalmente la stessa funzionalità di base degli oggetti Office corrispondenti, ma sono potenziati con le funzionalità seguenti:  
  
-   Possibilità di ospitare i controlli gestiti, inclusi i controlli host e quelli Windows Form.  
  
-   Modelli di eventi più ricchi. Alcuni eventi relativi a documenti, cartelle di lavoro e fogli di lavoro nei modelli a oggetti nativi di Word ed Excel vengono generati soltanto a livello di applicazione. Gli elementi host forniscono questi eventi a livello di documento, in modo che sia più semplice gestire gli eventi per un documento specifico.  
  
### <a name="understanding-host-items-in-document-level-projects"></a>Informazioni sugli elementi host nei progetti a livello di documento  
 Nei progetti a livello di documento, gli elementi host forniscono un punto di ingresso per il codice e contengono finestre di progettazione che consentono di sviluppare la soluzione.  
  
 Gli elementi host <xref:Microsoft.Office.Tools.Word.Document> e <xref:Microsoft.Office.Tools.Excel.Worksheet> contengono finestre di progettazione associate che rappresentano visivamente il documento o il foglio di lavoro, in maniera analoga a quanto avviene per una finestra di progettazione di Windows Form. Questa finestra di progettazione può essere usata per modificare il contenuto del documento o del foglio di lavoro direttamente in Word o Excel e per trascinare i controlli nell'area di progettazione. Per altre informazioni, vedere [Document Host Item](../vsto/document-host-item.md) e [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
 L'elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> non funge da contenitore per i controlli che hanno un'interfaccia utente. La finestra di progettazione per questo elemento host funge invece da barra dei componenti che consente il trascinamento di un componente, ad esempio <xref:System.Data.DataSet>, nell'area di progettazione. Per altre informazioni, vedere [Workbook Host Item](../vsto/workbook-host-item.md).  
  
 Non è possibile creare elementi host a livello di codice nei progetti a livello di documento. Al contrario, si possono usare le classi `ThisDocument`, `ThisWorkbook`o `Sheet`*n* , generate automaticamente da Visual Studio nel progetto in fase di progettazione. Queste classi generate derivano dagli elementi host e forniscono un punto di ingresso per il codice. Per altre informazioni, vedere [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understanding-host-items-in-vsto-add-in-projects"></a>Informazioni sugli elementi host nei progetti di componente aggiuntivo VSTO  
 Quando si crea un componente aggiuntivo VSTO, per impostazione predefinita non si ha l'accesso ad alcun elemento host. Tuttavia, è possibile generare gli elementi host <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>e <xref:Microsoft.Office.Tools.Excel.Worksheet> nei componenti aggiuntivi VSTO di Word e di Excel in fase di esecuzione.  
  
 Dopo aver generato un elemento host, è possibile eseguire attività quali l'aggiunta di controlli ai documenti. Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Controlli host  
 I controlli host estendono i vari oggetti dell'interfaccia utente nei modelli a oggetti di Word ed Excel, ad esempio Microsoft.Office.Interop.Word.ContentControl e <xref:Microsoft.Office.Interop.Excel.Range> oggetti.  
  
 Per i progetti Excel sono disponibili i controlli host seguenti:  
  
-   [Chart Control](../vsto/chart-control.md)  
  
-   [Controllo ListObject](../vsto/listobject-control.md)  
  
-   [Controllo NamedRange](../vsto/namedrange-control.md)  
  
-   [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)  
  
 Per i progetti Word sono disponibili i controlli host seguenti:  
  
-   [Controllo Bookmark](../vsto/bookmark-control.md)  
  
-   [Controlli del contenuto](../vsto/content-controls.md)  
  
-   [Controllo XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controllo XMLNodes](../vsto/xmlnodes-control.md)  
  
 I controlli host aggiunti ai documenti di Office si comportano come gli oggetti nativi di Office, ma dispongono di funzionalità aggiuntive che includono eventi e funzionalità di data binding. Ad esempio, per acquisire gli eventi di un oggetto <xref:Microsoft.Office.Interop.Excel.Range> nativo in Excel, è necessario per prima cosa gestire l'evento di modifica del foglio di lavoro. Quindi, è necessario determinare se la modifica è avvenuta all'interno di <xref:Microsoft.Office.Interop.Excel.Range>. Il controllo host <xref:Microsoft.Office.Tools.Excel.NamedRange> contiene invece un evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> che è possibile gestire direttamente.  
  
 La relazione tra un elemento host e i controlli host è molto simile a quella esistente tra un oggetto Windows Form e i controlli Windows Form. Posizionare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> esattamente come si posiziona un controllo casella di testo in un oggetto Windows Form. L'illustrazione seguente mostra la relazione tra elementi host e controlli host.  
  
 ![Relazione tra elementi host e controlli host](../vsto/media/hostitemscontrols.png "relazione tra elementi host e controlli host")  
  
 È anche possibile usare i controlli Windows Form nelle soluzioni Office aggiungendoli direttamente nell'area del documento di Word ed Excel. Per altre informazioni, vedere [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  L'aggiunta di controlli host o di controlli Windows Form a un documento secondario di Word non è supportata.  
  
### <a name="adding-host-controls-to-your-documents"></a>Aggiunta di controlli host ai documenti  
 Nei progetti a livello di documento è possibile aggiungere controlli host ai documenti di Word o ai fogli di lavoro di Excel in fase di progettazione nei modi seguenti:  
  
-   Aggiungere i controlli host a un documento in fase di progettazione nello stesso modo in cui si aggiunge un oggetto nativo.  
  
-   Trascinare i controlli host dalla **Casella degli strumenti** nei documenti e nei fogli di lavoro. I controlli host di Excel sono disponibili nella scheda **Controlli Excel** dei progetti Excel, mentre i controlli host di Word sono disponibili nella scheda **Controlli Word** dei progetti Word.  
  
-   Trascinare i controlli host dalla finestra **Origini dati** nei documenti e nei fogli di lavoro. In questo modo è possibile aggiungere controlli già associati ai dati. Per ulteriori informazioni, vedere [associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Nei progetti a livello di documento e in quelli di componenti aggiuntivi VSTO è anche possibile aggiungere alcuni controlli host ai documenti in fase di esecuzione. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Per altre informazioni su come aggiungere i controlli host ai documenti, vedere gli argomenti seguenti:  
  
-   [Procedura: Aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
-   [Procedura: Aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
-   [Procedura: Aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Procedura: Aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
-   [Procedura: Aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="naming-host-controls"></a>Denominazione dei controlli host  
 Quando si trascina un controllo host dalla **Casella degli strumenti** nel documento, il controllo viene automaticamente denominato usando il tipo del controllo con un numero incrementale alla fine. I segnalibri saranno, ad esempio, denominati **bookmark1**, **bookmark2**e così via. Se si usa la funzionalità nativa di Word o Excel per aggiungere il controllo, è possibile assegnare un nome specifico al momento della creazione. È anche possibile rinominare i controlli modificando il valore della proprietà **Name** nella finestra **Proprietà** .  
  
> [!NOTE]  
>  Nell'assegnazione di nomi ai controlli host non è possibile usare parole riservate. Se ad esempio si aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro e si cambia il nome in **System**, si verificheranno degli errori durante la compilazione del progetto.  
  
### <a name="deleting-host-controls"></a>Eliminazione di controlli host  
 Nei progetti a livello di documento, è possibile eliminare i controlli host in fase di progettazione selezionando il controllo nel foglio di lavoro di Excel o nel documento di Word e premendo CANC. Per eliminare i controlli **in Excel è tuttavia necessario usare la finestra di dialogo** Definisci nome <xref:Microsoft.Office.Tools.Excel.NamedRange> .  
  
 Se si aggiunge un controllo host a un documento in fase di progettazione, non rimuoverlo a livello di codice in fase di esecuzione perché al successivo tentativo di utilizzo del controllo nel codice verrà generata un'eccezione. Il metodo `Delete` di un controllo host rimuove solo i controlli host aggiunti al documento in fase di esecuzione. Se si chiama il metodo `Delete` di un controllo host creato in fase di progettazione, viene generata un'eccezione.  
  
 Ad esempio, il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> di un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> consente di eliminare correttamente l'oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> solo se è stato aggiunto a livello di codice al foglio di lavoro, operazione nota come creazione di controlli host in modo dinamico. I controlli host creati dinamicamente possono essere rimossi anche passando il nome del controllo al metodo `Remove` della proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> o <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> . Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Se un utente finale elimina un controllo host dal documento in fase di esecuzione, la soluzione potrebbe non riuscire con risultati imprevisti. Per proteggere i controlli host dall'eliminazione è possibile usare le funzionalità di protezione dei documenti. Per altre informazioni, vedere [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Non rimuovere i controlli a livello di codice usando il gestore eventi `Shutdown` del documento o del foglio di lavoro. Gli elementi dell'interfaccia utente non sono più disponibili quando si verifica l'evento `Shutdown` . Se si vogliono rimuovere i controlli prima della chiusura dell'applicazione, aggiungere il codice a un altro gestore eventi, ad esempio `BeforeClose` o `BeforeSave`.  
  
### <a name="programming-against-host-control-events"></a>Programmazione per gli eventi dei controlli host  
 Uno dei modi in cui i controlli host estendono gli oggetti Office è tramite l'aggiunta di eventi. Ad esempio, anche se l'oggetto <xref:Microsoft.Office.Interop.Excel.Range> in Excel e l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> in Word non contengono eventi, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] estende tali oggetti aggiungendo eventi programmabili. È possibile accedere a questi eventi e codificarli nello stesso modo in cui si accede agli eventi dei controlli presenti in Windows Form, ovvero tramite l'elenco a discesa degli eventi di Visual Basic e la pagina delle proprietà degli eventi in C#. Per altre informazioni, vedere [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Non è necessario impostare la proprietà <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Application> in Excel su **false**. Impostando questa proprietà su **false** si impedisce a Excel di generare eventi, inclusi gli eventi dei controlli host.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  