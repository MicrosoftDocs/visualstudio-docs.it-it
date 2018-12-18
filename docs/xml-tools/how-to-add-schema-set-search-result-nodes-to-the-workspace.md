---
title: "Procedura: aggiungere nodi dei risultati ricerca Set dello Schema per l'area di lavoro | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13d13c659dc100320460f6e2fed33271c260663f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro
In questo argomento viene illustrato come aggiungere nodi evidenziati in XML Schema Explorer come risultato di una ricerca per parole chiave nell'area di lavoro.  
  
> [!NOTE]
>  Possono essere aggiunti solo nodi globali per il [dell'area di lavoro](../xml-tools/xml-schema-designer-workspace.md).  
  
 In questo esempio viene utilizzato l'esempio [Schema ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi  
  
1.  Seguire i passaggi in [procedura: creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) barra degli strumenti e fare clic sul pulsante di ricerca.  
  
     ![Ricerca di parola chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.  
  
3.  Aggiungere i risultati della ricerca all'area di lavoro, fare clic il **Aggiungi nodi evidenziati all'area di lavoro** pulsante del riquadro dei risultati di riepilogo.  
  
     ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Il `purchaseOrder` nodo e `PurchaseOrderType` nodo vengono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.