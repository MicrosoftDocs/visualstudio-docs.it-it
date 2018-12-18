---
title: Cenni preliminari sugli strumenti di progettazione del modello di integrazione applicativa dei dati | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 89b497221e17402567970588a5b55a49fec3d705
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="bdc-model-design-tools-overview"></a>Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati
  È possibile progettare un modello di integrazione applicativa dei dati (BDC) utilizzando la finestra di progettazione di integrazione applicativa dei dati, il **Dettagli metodo di integrazione applicativa dei dati** finestra e **Esplora integrazione applicativa dei dati**.  
  
 Il **Esplora integrazione applicativa dei dati** consente di esplorare il modello, eseguire ricerche nel modello e definire i descrittori di tipo.  
  
## <a name="bdc-designer"></a>Finestra di progettazione di integrazione applicativa dei dati  
 La finestra di progettazione di integrazione applicativa dei dati consente di definire le entità nel modello e disporre visivamente le relazioni tra loro. Utilizzare la finestra di progettazione di integrazione applicativa dei dati per eseguire le attività seguenti:  
  
-   Aggiungere entità al modello.  
  
-   Rimuovere le entità dal modello.  
  
-   Definire le relazioni tra entità.  
  
 Per aprire la finestra di progettazione di integrazione applicativa dei dati, fare doppio clic sul file modello nel progetto o aprire il menu di scelta rapida per il file del modello e quindi scegliere **aprire**. Aggiungere un'entità al modello trascinando o copiando un **entità** dal **della casella degli strumenti** nella finestra di progettazione. Per creare un'associazione tra due entità, scegliere il **associazione** controllo il **della casella degli strumenti**, scegliere la prima entità, quindi la seconda entità.  
  
## <a name="bdc-method-details-window"></a>Finestra Dettagli metodo di integrazione applicativa dei dati  
 Utilizzare il **Dettagli metodo di integrazione applicativa dei dati** finestra per definire i parametri, le istanze e descrittori di filtro di un metodo.  
  
 È possibile generare rapidamente metodi Finder, Finder specifico, autore, Updater e Deleter il **Dettagli metodo di integrazione applicativa dei dati** finestra. Quando si generano questi metodi, Visual Studio aggiunge i metadati, ad esempio parametri, istanze e descrittori del tipo, il metodo. È possibile modificare i metadati per soddisfare il proprio scenario specifico.  
  
 Per aprire la **Dettagli metodo di integrazione applicativa dei dati** finestra, nella barra dei menu, scegliere **vista**, **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
 Per visualizzare i metodi di **Dettagli metodo di integrazione applicativa dei dati** finestra, scegliere l'entità nella finestra di progettazione di integrazione applicativa dei dati. I metodi dell'entità selezionata vengono visualizzati nel **Dettagli metodo di integrazione applicativa dei dati** finestra. Se non si sceglie un'entità nella finestra di progettazione di integrazione applicativa dei dati, il **Dettagli metodo di integrazione applicativa dei dati** finestra viene visualizzata alcuna informazione.  
  
 Espandere o comprimere i nodi di **Dettagli metodo di integrazione applicativa dei dati** finestra per definire parametri, le istanze e descrittori di filtro. Utilizzare il **Esplora integrazione applicativa dei dati** per definire i descrittori di tipo.  
  
## <a name="bdc-explorer"></a>Esplora integrazione applicativa dei dati  
 Il **Esplora integrazione applicativa dei dati** Visualizza gli elementi che costituiscono il modello. Per aprire la **Esplora integrazione applicativa dei dati**, sulla barra dei menu, scegliere **vista**, **altre finestre**, **Esplora integrazione applicativa dei dati**. Per esplorare il modello, espandere i nodi di **Esplora integrazione applicativa dei dati**. Ogni nodo rappresenta un elemento nel codice XML del file di modello.  
  
 Mentre si selezionano nodi nel **Esplora integrazione applicativa dei dati**, vengono visualizzate le proprietà di ogni nodo che si sceglie nel **proprietà** finestra. Molte di queste proprietà corrispondono agli attributi nel file di modello. È possibile cercare il modello utilizzando la casella di ricerca nella parte superiore del **Esplora integrazione applicativa dei dati**.  
  
> [!NOTE]  
>  Il **Esplora integrazione applicativa dei dati** non visualizza gli identificatori, proprietà personalizzate, le stringhe localizzate, gruppi di associazioni, azioni, descrittori di filtro, elenchi di controllo di azioni e i valori di parametro predefiniti.  
  
### <a name="defining-type-descriptors"></a>Definizione di descrittori di tipo  
 Utilizzare il **Esplora integrazione applicativa dei dati** per definire i descrittori di tipo. Le soluzioni di integrazione applicativa dei dati consente di definire un descrittore di tipo una sola volta e riusare quindi tale descrittore di tipo in un' posizione nel modello. A tale scopo, è possibile copiare un descrittore di tipo e incollarlo in qualsiasi altro parametro o descrittore di tipo.  
  
> [!NOTE]  
>  Le modifiche a un descrittore di tipo originale non influiscono le copie del descrittore di tipo.  
  
 Per ulteriori informazioni, vedere [procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)   
 [Procedura dettagliata: Creazione di un elenco esterno in SharePoint utilizzando i dati di Business](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrazione di dati di Business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Creazione di un modello di integrazione applicativa dei dati Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  