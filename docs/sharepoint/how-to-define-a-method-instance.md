---
title: 'Procedura: definire un''istanza del metodo | Documenti Microsoft'
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: aa5f1adcaacacd2b9e08d4c12cdcafbd5f561200
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
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
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  