---
title: 'Procedura: esaminare il modello di contenuto di nodi utilizzando la visualizzazione modello di contenuto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4856554b92f5689e17141004b7d4e0ffe5e781cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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