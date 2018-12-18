---
title: Estensione di progetti SharePoint | Documenti Microsoft
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
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>Estensione di progetti SharePoint
  Creare un'estensione di progetto quando si desidera personalizzare le funzionalità a livello di progetto dei progetti di SharePoint. Ad esempio, aggiungere le proprietà di progetto personalizzato oppure rispondere agli eventi a livello di progetto che vengono generati quando si sviluppa una soluzione di SharePoint in Visual Studio.  
  
## <a name="creating-project-extensions"></a>Creazione di estensioni di progetto  
 Per estendere un elemento di progetto, creare un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Per ulteriori informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Quando si crea un'estensione di progetto, è anche possibile aggiungere le funzionalità seguenti per i progetti SharePoint:  
  
-   Aggiungere una voce di menu di scelta rapida. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per un nodo di progetto SharePoint in **Esplora** chiavi per il pulsante destro del nodo o scegliendolo e quindi premendo MAIUSC + F10. Per ulteriori informazioni, vedere [procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Aggiungere una proprietà personalizzata. La proprietà viene visualizzata nel **proprietà** finestra quando si sceglie un progetto SharePoint in **Esplora**. Per ulteriori informazioni, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Per una procedura dettagliata viene illustrato come creare, distribuire e testare un'estensione di progetto, vedere [procedura dettagliata: creazione di un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Informazioni sulla relazione tra le estensioni di progetto e le istanze del progetto  
 Quando si crea un'estensione di progetto, l'estensione viene caricato quando si apre qualsiasi tipo di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include diversi modelli di progetto SharePoint, ad esempio le definizioni di elenco, tipi di contenuto e i ricevitori di eventi. Tuttavia, è solo un tipo di progetto SharePoint. I tipi di progetto che vengono visualizzati nel **nuovo progetto** la finestra di dialogo sono solo i modelli che raggruppano uno o più elementi di progetto SharePoint. Poiché è presente un solo tipo di progetto SharePoint, le estensioni create per un progetto si applicano a tutti i progetti SharePoint. È possibile, ad esempio, creare un'estensione che si applica solo a un **tipo di contenuto** progetto.  
  
 Per accedere a una specifica istanza del progetto, gestire uno del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> gli eventi del *projectService* parametro nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo. Ad esempio, per determinare quando un progetto SharePoint viene aggiunto a una soluzione, gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Per ulteriori informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Procedura dettagliata: Creazione di un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Distribuzione e l'estensione dei pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  