---
title: L'aggiornamento di progetti di Excel e Word che si esegue la migrazione a .NET Framework 4 o .NET Framework 4.5 | Documenti Microsoft
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 974071c68edd685bd23b29d6d37c520f50a78078
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="updating-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aggiornamento di progetti di Excel e Word di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5
  Se il progetto di Excel o di Word usa una qualsiasi delle funzionalità seguenti, è necessario modificare il codice se il framework di destinazione viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva:  
  
-   [Metodi GetVstoObject e HasVstoObject](#GetVstoObject)  
  
-   [Classi generate in progetti a livello di documento](#generatedclasses)  
  
-   [Controlli Windows Form in documenti](#winforms)  
  
-   [Eventi dei controlli contenuto di Word](#ccevents)  
  
-   [Classi OLEObject e OLEControl](#ole)  
  
-   [Proprietà Controls.Item(Object)](#itemproperty)  
  
-   [Raccolte che derivano da CollectionBase](#collections)  
  
 È anche necessario rimuovere gli ExcelLocale1033Attribute e i riferimenti alla classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy dai progetti di Excel ridestinati al [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Visual Studio non rimuove questo attributo o il riferimento alla classe.  
  
## <a name="removing-the-excellocale1033-attribute-from-excel-projects"></a>Rimozione di ExcelLocale1033Attribute da progetti di Excel  
 ExcelLocale1033Attribute è stata rimossa dalla parte di Visual Studio 2010 Tools per Office Runtime usata per le soluzioni destinate al [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Common Language Runtime (CLR) in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive passa sempre l'ID impostazioni locali 1033 al modello a oggetti di Excel e non è più possibile usare questo attributo per disattivare questo comportamento. Per altre informazioni, vedere [Globalization and Localization of Excel Solutions](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
#### <a name="to-remove-the-excellocale1033attribute"></a>Per rimuovere ExcelLocale1033Attribute  
  
1.  Con il progetto aperto in Visual Studio, aprire **Esplora soluzioni**.  
  
2.  Nel nodo **Proprietà** (per C#) o **Progetto personale** (per Visual Basic) fare doppio clic sul file di codice AssemblyInfo per aprirlo nell'editor di codice.  
  
    > [!NOTE]  
    >  Per visualizzare il file di codice AssemblyInfo nei progetti di Visual Basic, è necessario fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni** .  
  
3.  Individuare ExcelLocale1033Attribute e rimuoverlo dal file o impostarlo come commento.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="removing-a-reference-to-the-excellocal1033proxy-class"></a>Rimozione di un riferimento alla classe ExcelLocal1033Proxy  
 Progetti creati con Microsoft Visual Studio 2005 Tools per Microsoft Office System creano un'istanza di Excel <xref:Microsoft.Office.Interop.Excel.Application> oggetto utilizzando la classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy. Questa classe è stata rimossa dalla parte di Visual Studio 2010 Tools per Office Runtime usata per le soluzioni che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Di conseguenza, è necessario rimuovere o impostare come commento la riga di codice che fa riferimento a questa classe.  
  
#### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Per rimuovere il riferimento alla classe ExcelLocal1033Proxy  
  
1.  Aprire il progetto in Visual Studio e quindi aprire **Esplora soluzioni**.  
  
2.  In **Esplora soluzioni**aprire il menu di scelta rapida per ThisAddin.cs (per C#) o ThisAddin.vb (per Visual Basic) e quindi scegliere **Visualizza codice**.  
  
3.  Nell'area `VSTO generated code` dell'editor di codice rimuovere o impostare come commento la riga di codice seguente.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Aggiornamento del codice che usa i metodi GetVstoObject e HasVstoObject  
 Nei progetti destinati a .NET Framework 3.5, i metodi GetVstoObject e HasVstoObject sono disponibili come metodi di estensione in uno degli oggetti nativi seguenti nel progetto: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, o <xref:Microsoft.Office.Interop.Excel.ListObject>. Quando si chiamano questi metodi, non è necessario passare un parametro. Esempio di codice seguente viene illustrato come utilizzare il metodo GetVstoObject aggiuntivo un VSTO di Word destinato a .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva è necessario modificare il codice per accedere ai metodi in uno dei modi seguenti:  
  
-   È comunque possibile accedere a questi metodi come metodi di estensione nell'oggetto <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>o <xref:Microsoft.Office.Interop.Excel.ListObject> . Tuttavia, è ora necessario passare l'oggetto restituito dalla proprietà Globals. factory a questi metodi.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   In alternativa, è possibile accedere ai metodi per l'oggetto restituito dalla proprietà Globals. Factory. Quando si accede ai metodi in questo modo, è necessario passare l'oggetto nativo che si vuole estendere al metodo.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Aggiornamento del codice che usa istanze delle classi generate in progetti a livello di documento  
 Nei progetti a livello di documento destinati a .NET Framework 3.5 le classi generate nei progetti derivano dalle classi seguenti nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva i tipi nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] elencati sopra sono interfacce anziché classi. Le classi generate nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva derivano dalle nuove classi seguenti nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Se il codice nel progetto fa riferimento a un'istanza di una delle classi generate come classe base da cui deriva, è necessario modificare il codice.  
  
 Ad esempio, in un progetto Cartella di lavoro di Excel destinato a .NET Framework 3.5 potrebbe essere presente un metodo helper che esegue alcune attività nelle istanze delle classi `Sheet`*n* generate nel progetto.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Se si ridestina il progetto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, è necessario apportare una delle modifiche seguenti al codice:  
  
-   Modificare tutto il codice che chiama il metodo `DoSomethingToSheet` per passare la proprietà <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> di un oggetto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> nel progetto. Questa proprietà restituisce un oggetto <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Modificare il parametro del metodo `DoSomethingToSheet` in modo da richiedere invece un oggetto <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Aggiornamento del codice che usa controlli Windows Form nei documenti  
 È necessario aggiungere un **utilizzando** (c#) o **importazioni** istruzione (Visual Basic) per il <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> dello spazio dei nomi all'inizio di qualsiasi file di codice che usa la proprietà di controlli per aggiungere Windows Form controlli a livello di codice per il documento o foglio di lavoro.  
  
 Nei progetti destinati a .NET Framework 3.5, i metodi che aggiungono controlli Windows Form (ad esempio, il metodo AddButton) vengono definiti nel <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> classi.  
  
 Nei progetti destinati il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, questi metodi sono metodi di estensione che sono disponibili le proprietà di controlli. Per usare questi metodi di estensione, il file di codice in cui vengono usati i metodi deve includere un'istruzione **using** e **Imports** per lo spazio dei nomi <xref:Microsoft.Office.Tools.Excel> e <xref:Microsoft.Office.Tools.Word> . Questa istruzione viene generata automaticamente in nuovi progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Poiché tuttavia non viene aggiunta automaticamente nei progetti destinati a .NET Framework 3.5, è necessario aggiungerla quando si ridestina il progetto.  
  
 Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Aggiornamento del codice che gestisce eventi dei controlli contenuto di Word  
 Nei progetti destinati a .NET Framework 3.5 questi eventi vengono gestiti dal delegato <xref:System.EventHandler%601> generico. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva questi eventi vengono ora gestiti da altri delegati.  
  
 La tabella seguente elenca gli eventi dei controlli contenuto di Word e i delegati a essi associati nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva.  
  
|event|Delegato da usare in progetti di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Aggiornamento del codice che usa le classi OLEObject e OLEControl  
 Nei progetti destinati a .NET Framework 3.5, è possibile aggiungere controlli personalizzati (come controlli utente Windows Form) a un documento o foglio di lavoro utilizzando le classi OLEObject e OLEControl.  
  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva queste classi sono state sostituite dalle interfacce <xref:Microsoft.Office.Tools.Excel.ControlSite> e <xref:Microsoft.Office.Tools.Word.ControlSite> . È necessario modificare il codice che fa riferimento a OLEObject e OLEControl invece fare riferimento a <xref:Microsoft.Office.Tools.Excel.ControlSite> e <xref:Microsoft.Office.Tools.Word.ControlSite>. A parte i nuovi nomi, questi controlli si comportano allo stesso modo che nei progetti destinati a .NET Framework 3.5.  
  
 Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Aggiornamento del codice che usa la proprietà Controls.Item(Object)  
 Nei progetti destinati a .NET Framework 3.5, è possibile utilizzare la proprietà Item (Object) della raccolta Microsoft.Office.Tools.Word.Document.Controls o Microsoft.Office.Tools.Excel.Worksheet.Controls per determinare se un documento o foglio di lavoro include un controllo specificato.  
  
 Nei progetti destinati il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, la proprietà Item (Object) è stata rimossa da queste raccolte. Per determinare se un documento o foglio di lavoro contiene un controllo specifico, utilizzare invece il metodo del <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> o <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> raccolta invece.  
  
 Per ulteriori informazioni sulla raccolta di controlli di documenti e fogli di lavoro, vedere [aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Aggiornamento del codice che usa raccolte derivate da CollectionBase  
 Nei progetti destinati a .NET Framework 3.5 diversi tipi di raccolta nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derivare il <xref:System.Collections.CollectionBase> classe, ad esempio SmartTagCollection, Microsoft, e ControlCollection.  
  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva questi tipi di raccolta sono ora interfacce che non derivano da <xref:System.Collections.CollectionBase>. In questi tipi di raccolta non sono più disponibili alcuni membri, come <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>e <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Controlli contenuto](../vsto/content-controls.md)   
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  