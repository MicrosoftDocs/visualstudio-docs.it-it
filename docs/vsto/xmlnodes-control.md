---
title: XMLNodes (controllo) | Documenti Microsoft
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
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1a3759070d406e721a12e01950e0e99cea40d1fc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnodes-control"></a>Controllo XMLNodes
  **Importante** le informazioni in questo argomento relative a Microsoft Word sono presentata esclusivamente per il vantaggio e l'uso di singoli utenti e organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che utilizzano o lo sviluppo i programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio 2010, Microsoft la rimozione di un'implementazione di una particolare funzionalità correlata a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word potrebbero non essere lette o utilizzate dal singoli individui o organizzazioni negli Stati Uniti o relativi territori, che utilizza o lo sviluppo di programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti con licenza prima di tale data o acquistati e concesso in licenza di fuori degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo è una raccolta di oggetti del nodo XML mappati che espone gli eventi. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo viene creato solo quando un elemento ripetuto dello schema viene mappato a un documento di Microsoft Office Word. Se l'elemento ripetuto contiene elementi figlio, ognuno degli elementi figlio viene creata anche come un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.  
  
 Dopo Visual Studio crea la raccolta di nodi XML, è possibile programmare il controllo direttamente senza dover passare attraverso il modello a oggetti. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo può essere eliminato solo eliminando il mapping dell'elemento dal documento.  
  
> [!NOTE]  
>  Se si accede a un elemento figlio del <xref:Microsoft.Office.Tools.Word.XMLNodes> controllare tramite il <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> proprietà, viene restituito un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto anziché da un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Per altre informazioni, vedere [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Data binding al controllo  
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non supporta l'associazione dati. In questo modo il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non dispone di funzionalità di associazione di dati complessi e data binding semplice non può rappresentare dati ripetuti.  
  
## <a name="formatting"></a>Formattazione  
 La formattazione da applicare al testo all'interno del documento può essere applicata a un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.  
  
## <a name="events"></a>Eventi  
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo sono:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Confronto di eventi  
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo. Ad esempio, potrebbe essere un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo denominato `Customer` che include un elemento figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo denominato `Company`, e `Company` ha due figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli denominati `CompanyName` e `CompanyRegion` come indicato di seguito:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato `CompanyName` o `CompanyRegion` perché sono entrambe all'interno del contesto di `Company`. In questo caso, è possibile scrivere codice nel <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento di `Company`.  
  
 Nella maggior parte dei casi, quando il cursore viene spostato un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllare sia la <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> e <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> vengono generati eventi. La tabella seguente illustra le differenze tra questi eventi.  
  
|Selezionare l'evento|Evento ContextEnter|  
|------------------|------------------------|  
|Si verifica quando il cursore viene posizionato all'interno di uno dei nodi del <xref:Microsoft.Office.Tools.Word.XMLNodes> insieme.|Si verifica quando il cursore viene posizionato all'interno di uno dei nodi o i relativi nodi discendenti del <xref:Microsoft.Office.Tools.Word.XMLNodes> insieme, da un'area all'esterno del contesto del nodo. In altre parole, viene generato solo quando cambia il contesto e possono essere generati per più annidato <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli.|  
  
 Ad esempio, quando si sposta il cursore da `Customer` in `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> gli eventi per `Customer`, `Company`, e `CompanyName` vengono generati. Se poi si sposta il cursore da `CompanyName` a `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento solo per `CompanyRegion` viene generato, perché il contesto è lo stesso per entrambi `Company` e `Customer`. È possibile avere più `Company` nodi nel documento. Se si sposta il cursore dal `CompanyName` nodo di uno `Company` per il `CompanyName` nodo di un altro `Company`, il contesto è lo stesso, in modo che solo il <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> viene generato l'evento.  
  
 Le stesse differenze esistono tra la <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> evento e <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.  
  
## <a name="see-also"></a>Vedere anche  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode (controllo)](../vsto/xmlnode-control.md)   
 [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Procedura: mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  