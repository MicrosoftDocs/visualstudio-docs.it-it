---
title: 'Procedura: aggiungere un parametro a un metodo | Documenti Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 388ce91d8500cf21c4a4989b8db9106a4d19693d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Procedura: aggiungere un parametro a un metodo
  Usare un parametro per passare le informazioni nel metodo o per restituire informazioni da un metodo. Tutti i metodi devono avere almeno un parametro. Per ulteriori informazioni sulla progettazione di un parametro per supportare il tipo di metodo che si desidera creare, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando si aggiunge un parametro a un metodo, Visual Studio aggiunge il `<Parameter>` elemento al codice XML del file modello nel progetto. Per ulteriori informazioni sugli attributi di un `<Parameter>` elemento, vedere [parametro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Per aggiungere un parametro a un metodo  
  
1.  Aggiungere un metodo a un'entità.  
  
2.  Nella barra dei menu, scegliere **vista**, **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Il **Dettagli metodo di integrazione applicativa dei dati** verrà visualizzata la finestra. Per ulteriori informazioni, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nel **Dettagli metodo di integrazione applicativa dei dati** finestra, espandere il nodo del metodo e quindi espandere il **parametri** nodo.  
  
4.  Nel **aggiungere un parametro** scegliere **Crea parametro**.  
  
     Un nuovo parametro verrà visualizzata sotto il **parametri** nodo.  
  
5.  Nella barra dei menu, scegliere **vista**, **finestra proprietà**.  
  
6.  Nel **proprietà** finestra, impostare il **nome** proprietà a un nome significativo. Ad esempio, se il metodo restituirà i clienti, si potrebbe assegnare al metodo **GetCustomers**.  
  
7.  Nel **Dettagli metodo di integrazione applicativa dei dati** finestra, aprire l'elenco visualizzato per la direzione del parametro e quindi scegliere **In**, **InOut**, **Out**, o **restituire**.  
  
     Per ulteriori informazioni sulla direzione che scegliere per il tipo di metodo che si sta creando, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modificare il descrittore di tipo del parametro. Per ulteriori informazioni, vedere [procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procedura: definire una metodo di istanza](../sharepoint/how-to-define-a-method-instance.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  