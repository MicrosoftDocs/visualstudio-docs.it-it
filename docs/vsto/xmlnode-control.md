---
title: XMLNode (controllo) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b21f6f4e84672d195b6147f73c513c1995200a03
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="xmlnode-control"></a>Controllo XMLNode
  **Importante** le informazioni in questo argomento relative a Microsoft Word sono presentato in modo esclusivo per il vantaggio e uso di singoli utenti e organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che utilizzano o lo sviluppo programmi che vengono eseguiti in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di una funzionalità specifica relativi a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word potrebbero non essere lette o utilizzate dal singoli individui o organizzazioni negli Stati Uniti o relativi territori, che utilizza o lo sviluppo di programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti con licenza prima di tale data o acquistati e concesso in licenza di fuori degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo rappresenta un nodo XML mappato che espone gli eventi e può essere associato ai dati. Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo viene creato solo quando un elemento dello schema non ripetuto viene mappato a un documento di Microsoft Office Word. Dopo la creazione del nodo XML di Visual Studio, è possibile programmare utilizzandolo direttamente senza dover passare attraverso il modello a oggetti.  
  
 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo può essere eliminato solo eliminando il mapping dell'elemento in Word.  
  
## <a name="binding-data-to-the-control"></a>Data binding al controllo  
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo supporta il data binding semplice. Il nodo XML deve essere associato a un'origine dati tramite il <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> proprietà. Se i dati in set di dati associato vengono aggiornati, il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo riflette le modifiche.  
  
## <a name="formatting"></a>Formattazione  
 La formattazione che può essere applicato a un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto può essere applicato a un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Sono inclusi i tipi di carattere, gli stili di sottolineatura e gli stili di carattere.  
  
## <a name="events"></a>Eventi  
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.XMLNode>:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Confronto di eventi  
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Ad esempio, potrebbe essere un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo denominato `Customer` che include un elemento figlio <xref:Microsoft.Office.Tools.Word.XMLNode> controllo denominato `Company`, e `Company` ha due figlio <xref:Microsoft.Office.Tools.Word.XMLNode> controlli denominati `CompanyName` e `CompanyRegion` come indicato di seguito:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato `CompanyName` o `CompanyRegion` perché sono entrambe all'interno del contesto di `Company`. In questo caso, è possibile scrivere codice nel <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento di `Company`.  
  
 Nella maggior parte dei casi, quando il cursore viene spostato un <xref:Microsoft.Office.Tools.Word.XMLNode> controllare sia la <xref:Microsoft.Office.Tools.Word.XMLNode.Select> e <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> vengono generati eventi. Nella tabella seguente vengono illustrate le differenze tra questi eventi.  
  
|Selezionare l'evento|Evento ContextEnter|  
|------------------|------------------------|  
|Si verifica quando il cursore viene posizionato all'interno di un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Si verifica quando il cursore viene posizionato all'interno di un <xref:Microsoft.Office.Tools.Word.XMLNode> o uno dei nodi figlio, da un'area all'esterno del contesto del nodo. In altre parole, viene generato solo quando cambia il contesto.|  
  
 Ad esempio, quando si sposta il cursore da `Customer` in `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento per `Customer`, `Company`, e `CompanyName` viene generato. Se poi si sposta il cursore da `CompanyName` a `CompanyRegion`, solo il <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento per `CompanyRegion` viene generato perché si è ancora all'interno del contesto di entrambi `Company` e `Customer`.  
  
 Le stesse differenze esistono tra la <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> evento e <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> evento.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes (controllo)](../vsto/xmlnodes-control.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Procedura: mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  