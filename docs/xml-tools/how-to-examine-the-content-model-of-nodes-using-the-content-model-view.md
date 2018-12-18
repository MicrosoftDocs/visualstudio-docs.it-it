---
title: 'Procedura: esaminare il modello di contenuto di nodi utilizzando la visualizzazione modello di contenuto | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4b2430cd90a63d02503a99e26c893a3f59a5246
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procedura: esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto
In questo argomento viene descritto come esaminare i nodi tramite il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto  
  
1.  Creare un nuovo file XML Schema.  
  
2.  Fare clic su **usare l'Editor XML per visualizzare e modificare il file XML Schema sottostante** nella visualizzazione iniziale.  
  
3.  Copiare il codice di esempio di XML Schema da [XML Schema di esempio: Schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md) e incollarlo per sostituire il codice che è stato aggiunto il nuovo file XSD per impostazione predefinita.  
  
4.  Selezionare il `purchaseOrder` elemento in Schema Explorer facendo clic con il `purchaseOrder` elemento nell'Editor XML e selezionando **Mostra in XML Explorer**.  
  
5.  Fare doppio clic su di `purchaseOrder` in XML Explorer e selezionare **Mostra nella visualizzazione modello di contenuto**.  
  
     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.  
  
6.  Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.  
  
     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.  
  
7.  Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.  
  
8.  Fare clic su di **Mostra documentazione** sulla barra degli strumenti XSD per attivare o disattivare documentazione. È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.  
  
9. Fare clic su di Rick il `purchaseOrder` nodo e selezionare **genera XML di esempio** per visualizzare il documento di istanza XML.