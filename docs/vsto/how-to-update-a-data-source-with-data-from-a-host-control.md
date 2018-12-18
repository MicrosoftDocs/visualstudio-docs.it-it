---
title: 'Procedura: aggiornare un''origine dati con i dati da un controllo Host | Documenti Microsoft'
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
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 20e0e896389abc48d3f0b08136f06b90748b161d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host
  È possibile associare un controllo host a un'origine dati e aggiornare l'origine dati con le modifiche apportate ai dati nel controllo. Questo processo prevede due passaggi principali:  
  
1.  Aggiornare l'origine dati in memoria con i dati modificati nel controllo. In genere, l'origine dati in memoria è un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>o un altro oggetto dati.  
  
2.  Aggiornare il database con i dati modificati nell'origine dati in memoria. Ciò è possibile solo se l'origine dati è connessa a un database back-end, ad esempio un database SQL Server o Microsoft Office Access.  
  
 Per ulteriori informazioni sui controlli host e l'associazione dati, vedere [elementi Host e Cenni preliminari sui controlli Host](../vsto/host-items-and-host-controls-overview.md) e [associazione dei dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="updating-the-in-memory-data-source"></a>Aggiornamento dell'origine dati in memoria  
 Per impostazione predefinita, i controlli host che consentono il data binding semplice (ad esempio i controlli contenuto in un documento di Word o un controllo di intervallo denominato in un foglio di lavoro di Excel) non salvano le modifiche all'origine dati in memoria. In altre parole, quando un utente finale modifica un valore in un controllo host e successivamente si sposta dal controllo, il nuovo valore del controllo non viene salvato nell'origine dati.  
  
 Per salvare i dati nell'origine dati, è possibile scrivere codice che consenta di aggiornare l'origine dati in risposta a un evento specifico in fase di esecuzione oppure configurare il controllo in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore nel controllo.  
  
 Non è necessario salvare le modifiche apportate a <xref:Microsoft.Office.Tools.Excel.ListObject> nell'origine dati in memoria. Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ai dati, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> salva automaticamente le modifiche nell'origine dati in memoria senza che sia richiesto codice aggiuntivo.  
  
#### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Per aggiornare l'origine dati in memoria in fase di esecuzione  
  
-   Chiamare il metodo <xref:System.Windows.Forms.Binding.WriteValue%2A> dell'oggetto <xref:System.Windows.Forms.Binding> che associa il controllo all'origine dati.  
  
     Nell'esempio seguente le modifiche apportate a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in un foglio di lavoro di Excel vengono salvate nell'origine dati. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-updating-the-in-memory-data-source"></a>Aggiornamento automatico dell'origine dati in memoria  
 È anche possibile configurare un controllo in modo da aggiornare automaticamente l'origine dati in memoria. In un progetto a livello di documento, questa operazione può essere eseguita tramite codice o tramite la finestra di progettazione. In un progetto di componente aggiuntivo VSTO è necessario usare il codice.  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite codice  
  
1.  Utilizzare la modalità DataSourceUpdateMode del <xref:System.Windows.Forms.Binding> oggetto che associa il controllo all'origine dati. Per aggiornare l'origine dati è possibile procedere in due modi:  
  
    -   Per aggiornare l'origine dati quando il controllo viene convalidato, impostare questa proprietà su System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Per aggiornare l'origine dati quando cambia il valore della proprietà del controllo con associazione a dati, impostare questa proprietà su DataSourceUpdateMode.  
  
        > [!NOTE]  
        >  L'opzione DataSourceUpdateMode non si applicano ai controlli host di Word perché Word non notifiche non offerta documento o modifica del controllo. ma può essere usata per i controlli Windows Form nei documenti di Word.  
  
     L'esempio seguente configura un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore del controllo. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite la finestra di progettazione  
  
1.  In Visual Studio, aprire il documento di Word o la cartella di lavoro di Excel nella finestra di progettazione.  
  
2.  Fare clic sul controllo desiderato per aggiornare automaticamente l'origine dati.  
  
3.  Nella finestra **Proprietà** espandere la proprietà **(DataBindings)** .  
  
4.  Accanto al **(avanzate)** proprietà, fare clic sul pulsante con i puntini di sospensione (![schermata VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "schermata VisualStudioEllipsesButton")).  
  
5.  Nella finestra di dialogo **Formattazione e associazione avanzata** fare clic nell'elenco a discesa **Modalità aggiornamento origine dati** e selezionare uno dei valori seguenti:  
  
    -   Per aggiornare l'origine dati quando il controllo viene convalidato, selezionare **OnValidation**.  
  
    -   Per aggiornare l'origine dati quando si modifica il valore della proprietà del controllo associata ai dati, selezionare **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  L'opzione **OnPropertyChanged** non si applica ai controlli host di Word perché Word non fornisce notifiche relative alle modifiche al documento o al controllo, ma può essere usata per i controlli Windows Form nei documenti di Word.  
  
6.  Chiudere la finestra di dialogo **Formattazione e associazione avanzata** .  
  
## <a name="updating-the-database"></a>Aggiornamento del database  
 Se l'origine dati in memoria è associata a un database, è necessario aggiornare il database in base alle modifiche apportate all'origine dati. Per ulteriori informazioni sull'aggiornamento di un database, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md) e [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
#### <a name="to-update-the-database"></a>Per aggiornare il database  
  
1.  Chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per il controllo <xref:System.Windows.Forms.BindingSource> .  
  
     L'oggetto <xref:System.Windows.Forms.BindingSource> viene generato automaticamente quando un controllo associato a dati viene aggiunto a un documento o a una cartella di lavoro in fase di progettazione. L'oggetto <xref:System.Windows.Forms.BindingSource> connette il controllo al set di dati tipizzato nel progetto. Per altre informazioni, vedere [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     L'esempio di codice seguente presuppone che il progetto contenga un oggetto <xref:System.Windows.Forms.BindingSource> denominato `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Chiamare il `Update` metodo dell'oggetto TableAdapter generate nel progetto.  
  
     Il TableAdapter viene generato automaticamente quando si aggiunge un controllo con associazione a dati a un documento o una cartella di lavoro in fase di progettazione. Il TableAdapter connette il dataset tipizzato nel progetto per il database. Per altre informazioni, vedere [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Esempio di codice seguente si presuppone di disporre di una connessione alla tabella Customers nel database Northwind e che il progetto contiene un oggetto TableAdapter denominato `customersTableAdapter` e un set di dati tipizzato denominato `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Salvare i dati nel database](../data-tools/save-data-back-to-the-database.md)    
 [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Procedura: scorrere i record del Database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Procedura: popolare fogli di lavoro con dati da un Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Popolare documenti con dati specificati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  