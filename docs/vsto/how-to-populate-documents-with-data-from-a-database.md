---
title: 'Procedura: popolare documenti con dati da un Database | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bfbdb5b71a84ea2f3ab9a86cc2d2df33213e5a98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Procedura: popolare documenti con dati da un database
  È possibile accedere ai dati dei progetti a livello di documento per Microsoft Office con la stessa procedura usata per accedere ai dati dei progetti Windows Form. Per inserire dati da un database nella soluzione si usano infatti gli stessi strumenti e lo stesso codice e per visualizzare i dati è possibile usare i controlli Windows Form.  
  
 Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli associati a dati nei progetti di componente aggiuntivo VSTO in fase di esecuzione, vedere [procedura dettagliata: Data Binding semplice in VSTO aggiuntivo progetto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [Binding di dati a Word 2007 contenuto controlli con Visual Studio Tools per Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>Aggiunta di un controllo a un documento in fase di progettazione  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>Per popolare un documento con dati da un database  
  
1.  Aprire un progetto a livello di documento Word in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con il documento aperto nella finestra di progettazione.  
  
2.  Aprire il **origini dati** finestra e creare un'origine dati da un database. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
3.  Trascinare il campo desiderato dal **origini dati** della finestra del documento.  
  
 Al documento viene aggiunto un controllo contenuto. Il tipo di controllo contenuto dipende dal tipo di dati del campo selezionato. Per altre informazioni, vedere [Content Controls](../vsto/content-controls.md).  
  
 È possibile aggiungere un controllo diverso selezionando il campo dei dati nel **origini dati** finestra e quindi scegliendo un controllo diverso dall'elenco a discesa.  
  
## <a name="objects-in-the-project"></a>Oggetti del progetto  
 Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:  
  
-   Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per ulteriori informazioni, vedere [strumenti Dataset in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Un oggetto TableAdapter che connette il dataset tipizzato al database. Per ulteriori informazioni, vedere [creare e configurare gli oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
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
 [Procedura: aggiornare un'origine dati con i dati da un controllo Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Utilizzo dei file di Database locale nella panoramica di soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connessione ai dati nelle applicazioni Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  