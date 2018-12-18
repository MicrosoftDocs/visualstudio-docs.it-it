---
title: 'Procedura: utilizzare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni | Documenti Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58c8d74e29144a525eb33031fb98e25051d0305f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni
  Utilizzando un file di risorse, è possibile fornire nomi localizzati, definire proprietà e applicare autorizzazioni per oggetti definiti in un modello di integrazione applicativa dei dati. Per specificare queste informazioni, aggiungere un **risorse di integrazione applicativa dei dati Business** elemento a un progetto che contiene un **modello di integrazione applicativa dei dati di Business** elemento. Specificare nomi, proprietà e autorizzazioni modificando l'XML del file di risorse.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Per aggiungere un file di risorse di integrazione applicativa dei dati a un progetto SharePoint  
  
1.  In **Esplora**, espandere la cartella del progetto SharePoint e quindi selezionare la cartella che contiene il modello di integrazione applicativa dei dati.  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
3.  Espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
4.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere **elemento risorse di connettività dati**.  
  
5.  Nel **nome** , specificare il nome del file di risorse e quindi scegliere il **Aggiungi** pulsante.  
  
     Un file di risorse con estensione bdcr verrà aggiunto al progetto e aperto per la modifica.  
  
6.  Aggiungere l'XML per definire i nomi localizzati, le proprietà e le autorizzazioni che si desidera applicare al modello di integrazione applicativa dei dati.  
  
     Per informazioni su come definire questi elementi, vedere [modello e i file di risorse](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Creazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  