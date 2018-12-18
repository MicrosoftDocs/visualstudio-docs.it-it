---
title: 'Procedura: creare un modello di integrazione applicativa dei dati | Documenti Microsoft'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6b4e01a61ac3802edc2dc6e5f6ab3680d39e7704
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-bdc-model"></a>Procedura: creare un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati (BDC) utilizzando il modello per questo tipo di elemento e quindi aggiungere il modello a qualsiasi progetto SharePoint. Per ulteriori informazioni, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md). Per ulteriori informazioni su come progettare il modello, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Per creare un progetto di integrazione applicativa dei dati  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
    > [!NOTE]  
    >  Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic, scegliere **File**, **nuovo progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  In presenza di **Visual Basic** o **Visual c#**, scegliere **Office/SharePoint**, **soluzioni SharePoint**.  
  
3.  Nel **modelli** riquadro, scegliere il **SharePoint 2013 - progetto vuoto** elemento e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** apre.  
  
4.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, specificare l'URL di un sito di SharePoint nel computer locale, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **Fine** pulsante.  
  
     Si testerà il modello nel sito di SharePoint specificato.  
  
    > [!IMPORTANT]  
    >  Poiché i modelli di integrazione applicativa dei dati supportano solo soluzioni farm, è necessario distribuire il progetto come soluzione farm.  
  
     Viene creato un progetto SharePoint vuoto.  
  
5.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **Office/SharePoint** nodo.  
  
7.  Nell'elenco dei modelli di SharePoint, scegliere **(solo soluzione Farm) modello di integrazione applicativa dei dati Business**.  
  
8.  Nel **nome** , specificare un nome per il modello di integrazione applicativa dei dati e quindi scegliere il **Aggiungi** pulsante.  
  
     Oggetto **modello di integrazione applicativa dei dati di Business** elemento viene aggiunto al progetto. Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione di integrazione applicativa dei dati. Per ulteriori informazioni, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un modello di integrazione applicativa dei dati Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Procedura: utilizzare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  