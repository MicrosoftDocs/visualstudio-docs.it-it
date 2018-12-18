---
title: 'Procedura: aggiungere un metodo Creator | Documenti Microsoft'
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0424c6561b063b17f384215021a1300122dcbb1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-creator-method"></a>Procedura: aggiungere un metodo Creator
  Un metodo Creator aggiunge nuovi dati all'origine dati di un'entità. Il servizio di integrazione applicativa dei dati (BDC) chiama questo metodo quando gli utenti scelgono di **nuovo elemento** pulsante della barra multifunzione di un elenco che è basato sul modello. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Per aggiungere un metodo Creator  
  
1.  Nella finestra di progettazione di integrazione applicativa dei dati, scegliere un'entità.  
  
2.  Nella barra dei menu, scegliere **vista**, **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Il **Dettagli metodo di integrazione applicativa dei dati** verrà visualizzata la finestra. Per ulteriori informazioni su tale finestra, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nel **aggiungere un metodo** scegliere **Crea metodo Creator**.  
  
     Visual Studio aggiunge i seguenti elementi al modello e questi elementi vengono visualizzati nel **Dettagli metodo di integrazione applicativa dei dati** finestra.  
  
    -   Un metodo denominato **crea**.  
  
    -   Un parametro di input per il metodo.  
  
    -   Un parametro restituito del metodo.  
  
    -   Descrittori per i parametri di tipo.  
  
    -   Un'istanza del metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Esplora**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
     File di codice servizio dell'entità verrà aperto nell'Editor di codice. Per ulteriori informazioni sui file di codice servizio dell'entità, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Aggiungere codice al metodo Creator che aggiunge dati all'origine dati. Nell'esempio seguente aggiunge un contatto al database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore di `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  