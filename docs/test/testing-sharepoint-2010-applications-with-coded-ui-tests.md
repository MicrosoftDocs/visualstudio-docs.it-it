---
title: Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 15970f48791078d498fa7a187546c1c7230d3cf0
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente
Includendo i test codificati dell'interfaccia utente in un'applicazione SharePoint è possibile verificare che l'intera applicazione, inclusi i controlli per l'interfaccia utente, siano correttamente funzionanti. I test codificati dell'interfaccia utente possono inoltre convalidare i valori e la logica dell'interfaccia utente.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Ulteriori informazioni sui test codificati dell'interfaccia utente  
 Per altre informazioni sui vantaggi associati all'uso dei test codificati dell'interfaccia utente, vedere [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md) e [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 5: Automating System Tests](http://go.microsoft.com/fwlink/?LinkID=255196) (Test per il recapito continuo con Visual Studio 2012 - Capitolo 5: automazione dei test di sistema).  
  
 **Note**  
  
-   ![Prerequisito](../test/media/prereq.png "Prereq") I test codificati dell'interfaccia utente per le applicazioni SharePoint sono supportati solamente con SharePoint 2010.  
  
-   ![Prerequisito](../test/media/prereq.png "Prereq") Il supporto per i controlli Visio e PowerPoint 2010 nell'applicazione SharePoint non è previsto.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Creazione di un test codificato dell'interfaccia utente per l'applicazione SharePoint  
 La[creazione dei test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md) per le applicazioni SharePoint 2010 è analoga alla creazione dei test per altri tipi di applicazioni. La registrazione e la riproduzione è supportata da tutti i controlli dell'interfaccia di modifica Web. L'interfaccia per selezionare le categorie e le Web part è costituita da soli controlli Web standard.  
  
 ![Web part di SharePoint](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Se si sta registrando l'azione, convalidare le azioni prima di generare il codice. Poiché esistono numerosi comportamenti associati al passaggio del mouse, l'opzione è attivata per impostazione predefinita. Assicurarsi di rimuovere i passaggi del mouse ridondanti dai test codificati dell'interfaccia utente. È possibile eseguire questa operazione modificando il codice del test o tramite l' [editor di test codificati dell'interfaccia utente](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Inclusione dei test dei controlli di Office 2010 in un'applicazione SharePoint  
 Per abilitare l'automazione di alcune Web part di Office 2010 nell'applicazione SharePoint, è necessario apportare alcune piccole modiche al codice.  
  
> [!WARNING]
>  Il supporto per i controlli Visio e PowerPoint 2010 non è previsto.  
  
### <a name="excel-2010-cell-controls"></a>Controlli della cella di Excel 2010  
 Per includere i controlli della cella di Excel, è necessario apportare alcune modifiche nel codice del test codificato dell'interfaccia utente.  
  
> [!WARNING]
>  L'inserimento del testo in una cella di Excel seguito da un'azione con tasto di direzione, non viene registrato correttamente. Utilizzare il mouse per selezionare le celle.  
  
 Se si eseguono azioni di registrazione su una cella vuota, è necessario modificare il codice facendo doppio clic sulla cella e quindi eseguendo un'operazione di impostazione del testo. Ciò è necessario perché un clic nella cella, seguita da qualsiasi azione della tastiera attiva la `textarea` all'interno della cella. Registrando un elemento `setvalue` sulla cella vuota viene eseguita la ricerca dell'elemento `editbox` che non è presente fino a quando la cella non viene selezionata. Ad esempio:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Se si eseguono azioni di registrazione su una cella non vuota, la registrazione diviene leggermente più complessa perché quando si aggiunge il testo in una cella, viene aggiunto un nuovo controllo \<div> come elemento figlio della cella. Il nuovo controllo \<div> contiene il testo appena immesso. Il registratore deve registrare le azioni nel nuovo controllo \<div>, ma non può perché il controllo \<div> non esiste finché il test non viene immesso. È necessario apportare manualmente le seguenti modifiche al codice per ovviare a questo problema.  
  
1.  Passare all'inizializzazione della cella e rendere primarie le proprietà `RowIndex` e `ColumnIndex` :  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Individuare l'elemento figlio `HtmlDiv` della cella:  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  Aggiungere il codice per un'azione doppio clic del mouse su `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Aggiungere il codice per impostare il testo su `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Abilitazione del test codificato dell'interfaccia utente delle web part Silverlight nell'applicazione SharePoint 2010  
 Il test di Silverlight non è supportato in Visual Studio 2012 e versioni successive. Tuttavia, per testare le Web part Silverlight nell'applicazione SharePoint 2010, è possibile installare un plug-in per Silverlight separato dalla raccolta Visual Studio Gallery.  
  
#### <a name="setting-up-your-machine"></a>Configurazione del computer  
  
1.  Assicurarsi di avere installato Visual Studio 2012.1 o versione successiva.  
  
2.  Installare il [plug-in del test dell'interfaccia utente di Microsoft Visual Studio per Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Installare [Fiddler](http://www.fiddler2.com/fiddler2/). Si tratta semplicemente di uno strumento che tiene traccia e registra il traffico HTTP.  
  
4.  Scaricare il [progetto fiddlerXap](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Decomprimerlo, compilarlo ed eseguire lo script "CopySLHelper.bat" per installare la DLL di supporto necessaria per testare le Web part Silverlight quando si usa lo strumento Fiddler.  
  
 Dopo avere configurato il computer, attenersi alla seguente procedura per avviare il test dell'applicazione SharePoint 2010 con le Web part Silverlight:  
  
#### <a name="testing-silverlight-web-parts"></a>Test delle web part Silverlight  
  
1.  Avviare Fiddle.  
  
2.  Cancellare la cache del browser. Questa operazione è necessaria perché il file web.config XAP, contenente la DLL di supporto dell'automazione dell'interfaccia utente di Silverlight, in genere viene memorizzato nella cache. È necessario assicurarsi dell'effettiva selezione del file XAP modificato e pertanto viene rimossa la cache del browser.  
  
3.  Aprire la pagina Web.  
  
4.  Avviare il registratore e generare il codice come per un normale test dell'applicazione Web.  
  
5.  È necessario verificare che il codice generato faccia riferimento a Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Per altre informazioni, vedere l'articolo relativo ai [test dell'interfaccia utente per SharePoint 2010 con Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Risorse esterne  
  
### <a name="blogs"></a>Blog  
 [test dell'interfaccia utente per SharePoint 2010 con Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Informazioni sulla logica di ricerca per i controlli Silverlight nel test codificato dell'interfaccia utente](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Recupero della proprietà di un controllo Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Indice del contenuto per il test codificato dell'interfaccia utente](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Materiale sussidiario  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 5: Automating System Tests](http://go.microsoft.com/fwlink/?LinkID=255196) (Test per il recapito continuo con Visual Studio 2012 - Capitolo 5: automazione dei test di sistema)  
  
### <a name="forum"></a>Forum  
 [Blog di Visual Studi ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Vedere anche

[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)  
[Creare soluzioni di SharePoint](/office-dev/office-dev/create-sharepoint-solutions)   
[Verifica e debug del codice di SharePoint](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
[Compilazione e debug delle soluzioni SharePoint](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
[Profilatura delle prestazioni di applicazioni di SharePoint](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
