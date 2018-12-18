---
title: "Procedura: creare un'associazione tra entità | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c341586fbd2a22f38385a6c613058318f5c2d6a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-association-between-entities"></a>Procedura: creare un'associazione tra entità
  È possibile definire relazioni tra entità nel modello (Applicativa dei dati) tramite la creazione di associazioni. Visual Studio genera metodi che forniscono i consumer del modello con informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.  
  
 È possibile creare due tipi di associazioni nella finestra di progettazione di integrazione applicativa dei dati: associazioni basato su chiave esterne e associazioni senza chiave esterna. Per ulteriori informazioni, vedere [creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Per creare un'associazione tra entità  
  
1.  Nel **BusinessDataConnectivity** scheda della finestra il **della casella degli strumenti**, scegliere il **associazione** elemento.  
  
2.  Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità di origine, quindi l'entità di destinazione.  
  
     Il **Editor di associazione** viene visualizzato.  
  
3.  Se si desidera creare un'associazione basata su chiavi esterne, selezionare il **associazione chiave esterna** casella di controllo.  
  
    1.  Nel **ID origine** colonna del **Mapping identificatori** tabella, scegliere l'identificatore accanto a ogni descrittore di tipo corrispondente visualizzato nella **campo** colonna.  
  
         Ad esempio, nel **ID origine** colonna, selezionare `ContactID` accanto al `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descrittore di tipo e il `ReadItem.salesOrder.SalesOrder.ContactID` descrittore di tipo.  
  
4.  Se si desidera creare un'associazione senza chiave esterna, deselezionare il **associazione chiave esterna** casella di controllo.  
  
5.  Fare clic sul pulsante **OK** .  
  
6.  Nella finestra di progettazione di integrazione applicativa dei dati, verrà visualizzata una linea che rappresenta l'associazione tra entità di origine e l'entità di destinazione.  
  
     Visual Studio aggiunge un metodo AssociationNavigator per la classe di servizio dell'entità di destinazione e la classe di servizio dell'entità di origine. Per ulteriori informazioni sui metodi di navigazione di associazione, vedere [operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Nel metodo AssociationNavigator dell'entità di origine, aggiungere il codice che restituisce una raccolta di entità di destinazione.  
  
8.  Nel metodo AssociationNavigator dell'entità di destinazione, aggiungere il codice che restituisce l'entità di origine correlati.  
  
     Per esempi di metodi AssociationNavigator, vedere [creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)   
 [Progettazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)   
 [Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  