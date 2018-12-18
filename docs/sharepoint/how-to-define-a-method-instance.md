---
title: "Procedura: definire un'istanza del metodo | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44a31af455b09db5fb359339cee8da7b3ca0c77e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-method-instance"></a>Procedura: definire un'istanza di metodo
  Nel modello, è necessario definire almeno un'istanza di metodo per ogni metodo.  
  
 Aggiungere un'istanza del metodo usando il **Dettagli metodo di integrazione applicativa dei dati** finestra. Quando si aggiunge l'istanza del metodo, Visual Studio aggiunge un `<MethodInstance>` elemento al codice XML del file modello nel progetto. Per ulteriori informazioni sugli attributi di un `<MethodInstance>` elemento, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Per definire un'istanza del metodo  
  
1.  Nel **Dettagli metodo di integrazione applicativa dei dati** finestra, espandere il nodo di un metodo e quindi espandere il **istanze** nodo.  
  
2.  Nel **aggiungere un'istanza del metodo** scegliere **Crea istanza Finder**.  
  
     Verrà visualizzata una nuova istanza di metodo sotto il **istanze** nodo.  
  
3.  Nella barra dei menu, scegliere **vista**, scegliere **finestra proprietà**.  
  
4.  Nel **proprietà** finestra, impostare le proprietà dell'istanza del metodo. Per ulteriori informazioni su ogni proprietà, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  