---
title: Creazione di un modello di integrazione applicativa dei dati Business | Documenti Microsoft
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
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ab375e95d1deccb614a7908ec7608ffcb0da2e9c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="creating-a-business-data-connectivity-model"></a>Creazione di un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati (BDC) o personalizzare un modello di integrazione applicativa dei dati esistente con Visual Studio. Ogni progetto di SharePoint può contenere solo un modello. Per ulteriori informazioni, vedere [l'integrazione di dati di Business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="creating-a-new-model"></a>Creazione di un nuovo modello  
 Per creare un nuovo modello, creare un **modello di integrazione applicativa dei dati di Business** di progetto o aggiungere un **modello di integrazione applicativa dei dati di Business** elemento un **progetto SharePoint vuoto**.  
  
> [!NOTE]  
>  È necessario disporre di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installato nel computer.  
  
 Visual Studio aggiunge una cartella del progetto. Questa cartella include il nome specificato per il **modello di integrazione applicativa dei dati di Business** elemento il **Aggiungi nuovo elemento** la finestra di dialogo. Se si crea un nuovo **modello di integrazione applicativa dei dati di Business** la cartella di nomi di progetto, Visual Studio **BdcModel1**.  
  
 Visual Studio aggiunge i seguenti file nella nuova cartella:  
  
|File|Descrizione|  
|----------|-----------------|  
|File di definizione del modello|Contiene codice XML che definisce le entità, metodi, oggetti di sistema Line-of-Business (LOB) e altri metadati che descrivono il modello.<br /><br /> Modificare i metadati in questo file usando la finestra di progettazione di integrazione applicativa dei dati, **Esplora integrazione applicativa dei dati**, **Dettagli metodo di integrazione applicativa dei dati** finestra e **proprietà** finestra.|  
|File di codice di entità servizio|Contiene metodi che recuperano, aggiornano ed eliminare le istanze di entità predefinito.|  
  
 Per definire le proprietà di un'entità, modificare il file di codice di entità. Per ulteriori informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Per recuperare, aggiornare ed eliminare le istanze di un'entità, aggiungere codice al file di codice servizio dell'entità. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando si compila il progetto, Visual Studio crea un assembly. Assicurarsi di non aggiungere altri elementi al progetto con cui aggiungere il codice dell'assembly del progetto (ad esempio: un **flusso di lavoro sequenziale** elemento o un **Web Part** elemento). Il codice per l'elemento non verrà eseguito quando si distribuisce la soluzione perché il pacchetto della soluzione non copiare l'assembly nella global assembly cache.  Il pacchetto della soluzione consente di distribuire l'assembly solo nel database di integrazione applicativa dei dati in SharePoint.  
  
> [!NOTE]  
>  Quando si esegue il debug del progetto, Visual Studio copia dell'assembly in entrambi i percorsi nel computer locale.  
  
## <a name="adding-an-existing-model"></a>Aggiunta di un modello esistente  
 È possibile importare un modello che è stato creato utilizzando altri strumenti, ad esempio SharePoint Designer. È possibile scegliere di importare un modello esistente al progetto nelle situazioni seguenti:  
  
-   Per personalizzare un modello che è già stato distribuito a una server farm di SharePoint.  
  
-   Per creare un pacchetto e distribuire un modello esistente in più server farm di SharePoint.  
  
 In entrambi i casi, i sistemi LOB definiti nel modello da importare non sono interessati e continueranno a funzionare come previsto. Per aggiungere un modello esistente a un progetto SharePoint, utilizzare Visual Studio **Aggiungi elemento esistente** la finestra di dialogo. Per ulteriori informazioni, vedere [procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 È possibile aggiungere un sistema LOB di assembly di .NET Framework di tipo per il modello importato selezionando un'opzione di **LobSystem di assembly .NET aggiungere**. Ciò consente di scrivere codice personalizzato e utilizzare una finestra di progettazione per definire i metadati per il modello importato.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)|Viene illustrato come creare un nuovo modello di integrazione applicativa dei dati.|  
|[Procedura: Aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Viene illustrato come importare un modello esistente in un progetto SharePoint.|  
|[Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Viene descritto come fornire stringhe che vengono unite con i metadati del modello quando il modello è utilizzato da una Web Part o una pagina Web.|  
|[Procedura: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Viene illustrato come includere un assembly personalizzato nella funzionalità.|  
  
  