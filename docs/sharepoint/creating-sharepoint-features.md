---
title: Creazione di funzionalità SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b0a8de8b36d41684e00c9b679672d90909540107
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-sharepoint-features"></a>Creazione di funzionalità SharePoint
  È possibile utilizzare una funzionalità di SharePoint per raggruppare gli elementi di progetto SharePoint correlati per semplificare la distribuzione. È possibile creare funzionalità, impostare gli ambiti e contrassegnare altre funzionalità come dipendenze utilizzando la finestra di progettazione di funzionalità di SharePoint. La finestra di progettazione genera inoltre un manifesto, ovvero un file XML che descrive ogni funzionalità.  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>Aggiunta di funzionalità della soluzione SharePoint  
 È possibile aggiungere una funzionalità per la soluzione SharePoint tramite Esplora soluzioni o Esplora pacchetti. È possibile utilizzare uno dei metodi seguenti per aggiungere una funzionalità.  
  
-   In **Esplora**, aprire il menu di scelta rapida per **funzionalità**, quindi scegliere **Aggiungi funzionalità**.  
  
-   In **Esplora pacchetti**, aprire il menu di scelta rapida per il pacchetto e quindi scegliere **Aggiungi funzionalità**.  
  
## <a name="using-the-feature-designer"></a>Utilizzando la finestra di progettazione di funzionalità  
 Una soluzione di SharePoint può contenere uno o più funzionalità di SharePoint, vengono raggruppate sotto il nodo di funzionalità in Esplora soluzioni. Ogni funzionalità ha il proprio **Progettazione funzionalità** che è possibile utilizzare per personalizzare le proprietà della funzionalità. Per ulteriori informazioni, vedere [procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Per distinguere le funzionalità uno da altro, è possibile configurare le proprietà della funzionalità come il titolo, descrizione, versione e ambito.  
  
### <a name="feature-designer-options"></a>Opzioni della finestra di progettazione di funzionalità  
 Dopo aver creato una funzionalità, è possibile utilizzare la finestra di progettazione di funzionalità per personalizzarlo.  
  
 Nella tabella seguente vengono descritte le proprietà di funzionalità che vengono visualizzate nella finestra di progettazione di funzionalità.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|Titolo|Facoltativo. Il titolo predefinito della funzionalità è impostato su *SolutionName * * FeatureName*.|  
|Descrizione|Facoltativo. Descrizione della funzionalità di SharePoint.|  
|Ambito|Obbligatorio. Se una funzionalità viene creata utilizzando **Esplora**, per impostazione predefinita, l'ambito è impostato sul Web.<br /><br /> -Farm: Attivare una funzionalità per un'intera server farm.<br /><br /> -Sito: Attivare una funzionalità per tutti i siti web in una raccolta siti.<br /><br /> -Web: Attivare una funzionalità per un sito web specifico.<br /><br /> -WebApplication: Attivare una funzionalità per tutti i siti web in un'applicazione web.|  
|Elementi nella soluzione|Tutti gli elementi di SharePoint che può essere aggiunto alla funzionalità.|  
|Elementi nella funzionalità|Gli elementi di progetto SharePoint che sono stati aggiunti alla funzionalità.|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>Aggiunta e rimozione di elementi di progetto SharePoint  
 È possibile selezionare gli elementi di progetto SharePoint che si desidera aggiungere una funzionalità di SharePoint per la distribuzione. Utilizzare il **Progettazione funzionalità** per aggiungere e rimuovere elementi alle funzionalità e visualizzare il manifesto della funzionalità. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="adding-feature-dependencies"></a>Aggiunta di dipendenze delle funzionalità  
 È possibile configurare il manifesto delle funzionalità in modo che il server SharePoint attiva alcune funzionalità prima dell'attivazione della funzionalità. Ad esempio, se la funzionalità di SharePoint dipende da altre funzionalità per la funzionalità o dati, il server di SharePoint può provare attivare le funzionalità che dipende dalla propria funzionalità. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Procedura: Aggiungere e rimuovere dipendenze di funzionalità](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  