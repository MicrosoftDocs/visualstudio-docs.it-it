---
title: 'Procedura: popolare documenti con dati da oggetti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: baac72889a34474157bd89e151f6e63c19968fbb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Procedura: Popolare documenti con i dati di oggetti
  L'accesso ai dati di un oggetto dati è uguale sia nei progetti a livello di documento per Microsoft Office Word, sia nei progetti Windows Form. Per inserire i dati di un oggetto nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile usare i controlli Windows Form. Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Per popolare il documento con i dati di un oggetto, è necessario completare tre passaggi di base:  
  
-   Aggiungere al documento un controllo che è possibile associare ai dati.  
  
-   Aggiungere un oggetto dati al documento.  
  
-   Connettere l'oggetto dati a BindingSource   
  
## <a name="adding-a-data-object"></a>Aggiunta di un oggetto dati  
  
#### <a name="to-add-a-data-object"></a>Per aggiungere un oggetto dati  
  
-   Aprire la finestra **Origini dati** e creare un'origine dati da un oggetto. Per altre informazioni, vedere [Add new data sources](/visualstudio/data-tools/add-new-data-sources) (Aggiungere nuove origini dati).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Connessione dell'oggetto dati a BindingSource  
 Nei progetti a livello di documento i controlli vengono aggiunti al documento e associati ai dati in fase di progettazione.  
  
 Nei progetti di componente aggiuntivo VSTO è possibile creare controlli e associarli in fase di esecuzione.  
  
### <a name="document-level-projects"></a>Progetti a livello di documento  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Per connettere l'oggetto dati a BindingSource  
  
1.  Trascinare il campo dati desiderato dalla finestra **Origini dati** al documento in modo da creare automaticamente un controllo.  
  
2.  Nel codice creare un'istanza del tipo di oggetto selezionato per l'origine dati.  
  
3.  Assegnare l'istanza alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Progetti a livello di applicazione  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Per connettere l'oggetto dati a BindingSource  
  
1.  Nel codice creare un'istanza del tipo di oggetto associato all'origine dati.  
  
2.  Creare un'istanza di un oggetto <xref:System.Windows.Forms.BindingSource>.  
  
3.  Assegnare l'istanza dell'origine dati alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.  
  
4.  Aggiungere l'origine dati come data binding al controllo.  
  
## <a name="see-also"></a>Vedere anche  
 
 [Aggiungere nuove origini dati](/visualstudio/data-tools/add-new-data-sources)   
 [Associare controlli Windows Form ai dati in Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: aggiornare un'origine dati con i dati da un controllo Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Connessione ai dati nelle applicazioni Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  