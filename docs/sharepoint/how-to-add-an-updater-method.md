---
title: 'Procedura: aggiungere un metodo Updater | Documenti Microsoft'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc7c946a89c8ba05ffed443816d6ce4e9056b88b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-an-updater-method"></a>Procedura: aggiungere un metodo Updater
  È possibile consentire agli utenti aggiornare i dati di business in un elenco esterno di SharePoint tramite la creazione di un *Updater* metodo. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Per creare un metodo Updater  
  
1.  Nella finestra di progettazione di integrazione applicativa dei dati, scegliere un'entità.  
  
2.  Nella barra dei menu, scegliere **vista**, **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati. Per ulteriori informazioni su questa finestra, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nel **aggiungere un metodo** scegliere **Crea metodo Updater**.  
  
     Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nella finestra Dettagli metodo di integrazione applicativa dei dati.  
  
    -   Un metodo denominato **aggiornamento**.  
  
    -   Un parametro di input per il metodo.  
  
    -   Un descrittore di tipo per il parametro. Per impostazione predefinita, Visual Studio Usa il descrittore di tipo di entità definito per il metodo Finder (ad esempio: Contact).  
  
    -   Un'istanza del metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Se l'identificatore del tipo di entità rappresenta un campo in una tabella di database che viene generato automaticamente, impostare il **campo pre-Updater** proprietà **True**.  
  
4.  In **Esplora**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
     File di codice servizio dell'entità verrà aperto nell'Editor di codice. Per ulteriori informazioni su tale file, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Aggiungere codice al metodo Update per aggiornare i dati. Nell'esempio seguente aggiorna le informazioni per un contatto nel database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore di `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  