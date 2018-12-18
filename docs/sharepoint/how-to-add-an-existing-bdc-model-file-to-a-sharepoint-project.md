---
title: 'Procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f5f13377211a6b8a7a2035d85e1423be9d2bbb72
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint
  È possibile personalizzare, creare un pacchetto e ridistribuire un modello di integrazione applicativa dei dati tramite Visual Studio per aggiungere il file del modello (con estensione bdcm) a qualsiasi progetto farm di SharePoint. Per ulteriori informazioni, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Per aggiungere un file del modello di integrazione applicativa dei dati a un progetto SharePoint  
  
1.  In **Esplora**, scegliere la cartella di un progetto SharePoint.  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi elemento esistente**.  
  
3.  Nel **Aggiungi elemento esistente** la finestra di dialogo, selezionare il percorso del file di definizione del modello che si desidera aggiungere al progetto, scegliere il file e quindi scegliere il **Aggiungi** pulsante.  
  
     Se il modello non viene definito un *sistema Line-of-Business (LOB) di tipo assembly .NET*, il **LobSystem di assembly .NET aggiungere** verrà visualizzata la finestra di dialogo.  
  
4.  Se la finestra di dialogo viene visualizzata, effettuare una delle seguenti operazioni:  
  
    -   Se si desidera scrivere codice personalizzato e utilizzare una finestra di progettazione per definire i metadati per il modello importato, scegliere il **Sì** pulsante, denominare il sistema e quindi scegliere il **OK** pulsante.  
  
    -   In caso contrario, scegliere il **n** e quindi scegliere il **OK** pulsante.  
  
     Il **modello di integrazione applicativa dei dati di Business** elemento viene aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un modello di integrazione applicativa dei dati Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: utilizzare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  