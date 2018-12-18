---
title: 'Procedura: popolare fogli di lavoro con dati da un Database | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 31f0bd40b38ed85631874556908a41e21b860ecd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Procedura: popolare fogli di lavoro con dati da un database
  È possibile accedere a dati nei progetti di Office a livello di documento nello stesso modo di accedere ai dati nei progetti Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, possono sfruttare i controlli chiamati controlli host, ossia oggetti nativi di Microsoft Office Excel che sono stati migliorati con eventi e funzionalità di associazione dati. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli associati a dati nei progetti a livello di applicazione in fase di esecuzione, vedere [procedura dettagliata: Data Binding complesso in VSTO aggiuntivo progetto](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [modo in cui si ricerca per categorie: trasferimento dati in un foglio di lavoro Excel?](http://go.microsoft.com/fwlink/?LinkID=130277), e [How Do ricerca per categorie: utilizzare Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Aggiunta di un controllo con associazione a dati a un foglio di lavoro in fase di progettazione  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Per popolare un foglio di lavoro con i dati da un database  
  
1.  Aprire un progetto a livello di documento di Excel in Visual Studio, aprire il foglio di lavoro nella finestra di progettazione.  
  
2.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
3.  Trascinare il campo o la tabella da cui si desidera il **origini dati** finestra al foglio di lavoro.  
  
 Uno dei seguenti controlli viene creato nel foglio di lavoro:  
  
-   Se si trascina un campo, un <xref:Microsoft.Office.Tools.Excel.NamedRange> nel foglio di lavoro viene creato. Per ulteriori informazioni, vedere [controllo NamedRange](../vsto/namedrange-control.md).  
  
-   Se si trascina una tabella, una <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro viene creato. Per altre informazioni, vedere [ListObject Control](../vsto/listobject-control.md).  
  
 È possibile aggiungere un controllo diverso selezionando la tabella o campo di **origini dati** finestra e quindi scegliendo un controllo diverso dall'elenco a discesa.  
  
## <a name="objects-in-the-project"></a>Oggetti del progetto  
 Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:  
  
-   Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per ulteriori informazioni, vedere [strumenti Dataset in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Un oggetto TableAdapter che connette il dataset tipizzato al database. Per altre informazioni, vedere [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   TableAdapterManager utilizzato per coordinare gli adattatori di tabella nel set di dati per abilitare gli aggiornamenti gerarchici. Per ulteriori informazioni, vedere [aggiornamento gerarchico](../data-tools/hierarchical-update.md) e [TableAdapterManager riferimento](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati. È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.  
  
#### <a name="to-scroll-through-the-records"></a>Per scorrere i record  
  
-   Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Per informazioni su come inviare aggiornamenti al set di dati tipizzato e al database, vedere [procedura: aggiornare un'origine dati con i dati da un controllo Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Aggiungere nuove origini dati](/visualstudio/data-tools/add-new-data-sources)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: popolare documenti con dati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Procedura: aggiornare un'origine dati con i dati da un controllo Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Procedura relativa al trasferimento dei dati in un foglio di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Procedura per usare i dati di Database in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  