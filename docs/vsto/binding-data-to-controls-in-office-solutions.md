---
title: Associazione dati ai controlli nelle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea9d344e3b36d9d46ea5a5adcb642e43687b75ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="binding-data-to-controls-in-office-solutions"></a>Associazione di dati ai controlli nelle soluzioni Office
  È possibile associare i controlli Windows Form e i *controlli host* in un documento di Microsoft Office Word o in un foglio di lavoro di Microsoft Office Excel a un'origine dati in modo da visualizzare automaticamente i dati. È possibile associare dati ai controlli nei progetti a livello di applicazione e a livello di documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 I controlli host consentono di estendere gli oggetti contenuti nei modelli a oggetti di Word ed Excel, ad esempio i controlli del contenuto in Word e gli intervalli denominati in Excel. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 I controlli Windows Form e i controlli host usano il modello di data binding di Windows Form, che supporta sia il *data binding semplice* , sia il *data binding complesso* a origini dati quali set di dati e tabelle dati. Per informazioni complete sul modello di data binding in Windows Form, vedere [Data Binding e Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [How Do ricerca per categorie: utilizzare Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>data binding semplice  
 Il data binding semplice si verifica quando una proprietà controllo è associata a un singolo elemento dati, come un valore in una tabella dati. Ad esempio, il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> ha una proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> che può essere associata a un campo in un set di dati. Quando il campo all'interno del set di dati viene modificato, cambia anche il valore nell'intervallo denominato. Tutti i controlli host, tranne <xref:Microsoft.Office.Tools.Word.XMLNodes> , supportano il data binding semplice. Il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> è una raccolta e pertanto non supporta il data binding.  
  
 Per eseguire il data binding semplice su un controllo host, aggiungere un <xref:System.Windows.Forms.Binding> alla proprietà DataBindings del controllo. Un oggetto <xref:System.Windows.Forms.Binding> rappresenta l'associazione semplice tra il valore di una proprietà del controllo e il valore dell'elemento dati.  
  
 L'esempio di codice seguente dimostra come associare la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> a un elemento dati in un progetto a livello di documento.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Per procedure dettagliate che illustrano il data binding semplice, vedere [procedura dettagliata: associazione dati semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) per un progetto a livello di documento e [procedura dettagliata: associazione dati semplice in VSTO aggiungere nel progetto ](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) per un progetto di componente aggiuntivo VSTO.  
  
## <a name="complex-data-binding"></a>data binding complesso  
 Il data binding complesso si verifica quando una proprietà controllo è associata a più elementi dati, ad esempio più colonne in una tabella dati. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> per Excel è l'unico controllo host che supporta il data binding complesso. Esistono anche numerosi controlli Windows Form che supportano il data binding complesso, ad esempio il controllo <xref:System.Windows.Forms.DataGridView> .  
  
 Per eseguire il data binding complesso, impostare la proprietà DataSource del controllo a un oggetto origine dati supportata dal data binding complesso. Ad esempio, la proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> del controllo <xref:Microsoft.Office.Tools.Excel.ListObject> può essere associata a più colonne in una tabella dati. Tutti i dati nella tabella dati vengono visualizzati nel controllo <xref:Microsoft.Office.Tools.Excel.ListObject> e quando cambiano i dati nella tabella dati, cambia anche l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> . Per un elenco delle origini dati che è possibile usare per il data binding complesso, vedere [Data Sources Supported by Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 L'esempio di codice seguente crea un oggetto <xref:System.Data.DataSet> con due oggetti <xref:System.Data.DataTable> e popola una delle tabelle con dati. Il codice associa quindi l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> alla tabella che contiene i dati. Questo esempio si riferisce a un progetto a livello di documento di Excel.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Per procedure dettagliate che illustrano l'associazione dati complessa, vedere [procedura dettagliata: associazione dati complessa in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) per un progetto a livello di documento e [procedura dettagliata: associazione dati complessa in VSTO aggiungere nel progetto ](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) per un progetto di componente aggiuntivo VSTO.  
  
## <a name="displaying-data-in-documents-and-workbooks"></a>Visualizzazione dei dati in documenti e cartelle di lavoro  
 Nei progetti a livello di documento è possibile usare la finestra di dialogo **Origini dati** per aggiungere facilmente controlli associati a dati ai documenti o alle cartelle di lavoro, mediante una procedura analoga a quella usata per i Windows Form. Per ulteriori informazioni sull'utilizzo di **origini dati** finestra, vedere [controlli binding di Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [aggiungere nuove origini dati](../data-tools/add-new-data-sources.md).  
  
### <a name="dragging-controls-from-the-data-sources-window"></a>Trascinamento dei controlli dalla finestra Origini dati  
 Nel documento viene creato un controllo quando vi si trascina un oggetto dalla finestra **Origini dati** . Il tipo di controllo che viene creato varia a seconda del fatto che si associ una solo colonna o più colonne di dati.  
  
 Per Excel, nel foglio di lavoro viene creato un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per ogni campo e un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> per ogni intervallo di dati che include più righe e colonne. Questa impostazione predefinita può essere modificata selezionando la tabella o il campo nella finestra **Origini dati** e scegliendo un controllo diverso dall'elenco a discesa.  
  
 Viene aggiunto un controllo <xref:Microsoft.Office.Tools.Word.ContentControl> ai documenti. Il tipo di controllo contenuto dipende dal tipo di dati del campo selezionato.  
  
### <a name="binding-data-in-document-level-projects-at-design-time"></a>Data binding nei progetti a livello di documento in fase di progettazione  
 Gli argomenti seguenti mostrano esempi di data binding in fase di progettazione:  
  
-   [Procedura: Popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Procedura: Popolare documenti con dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Procedura: Popolare documenti con dati specificati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Procedura: Scorrere i record di un database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="binding-data-in-vsto-add-in-projects"></a>Data binding nei progetti di componente aggiuntivo VSTO  
 Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli solo in fase di esecuzione. Gli argomenti seguenti mostrano esempi di data binding in fase di esecuzione:  
  
-   [Procedura dettagliata: data binding semplice in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Procedura dettagliata: data binding complesso in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="updating-data-that-is-bound-to-host-controls"></a>Aggiornamento dei dati associati a controlli host  
 Il data binding tra un'origine dati e un controllo host comporta un aggiornamento bidirezionale dei dati. Nel data binding semplice, le modifiche apportate all'origine dati si riflettono automaticamente nel controllo host, mentre quelle apportate al controllo host richiedono una chiamata esplicita per aggiornare l'origine dati. Il motivo è che in alcuni casi le modifiche apportate a un campo associato a dati non vengono accettate se non sono accompagnate da modifiche a un altro campo associato a dati. Si considerino, ad esempio, due campi, uno relativo all'età e un altro relativo agli anni di esperienza. L'esperienza non può superare l'età. Non è possibile aggiornare l'età da 50 a 25 e poi l'esperienza da 30 a 10 a meno che le modifiche non vengano apportate contemporaneamente. Per risolvere il problema, i campi con data binding semplice non vengono aggiornati finché gli aggiornamenti non vengono inviati in maniera esplicita dal codice.  
  
 Per aggiornare un'origine dati da controlli host che consentono il data binding semplice, è necessario inviare gli aggiornamenti all'origine dati in memoria (ad esempio un oggetto <xref:System.Data.DataSet> o <xref:System.Data.DataTable>) e al database back-end, se usato nella soluzione.  
  
 Non è necessario aggiornare in modo esplicito l'origine dati in memoria quando si esegue il data binding complesso usando il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> . In quel caso, le modifiche vengono inviate automaticamente all'origine dati in memoria senza codice aggiuntivo.  
  
 Per altre informazioni, vedere [Procedura: Aggiornare un'origine dati con dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Vedere anche  
 [procedura per usare i dati di database in Excel](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Data binding e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Procedura: Creare un controllo con associazione semplice in un Windows Form](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Salvare i dati nel database](../data-tools/save-data-back-to-the-database.md)    
 [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [La memorizzazione nella cache di dati](../vsto/caching-data.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)  
  
  