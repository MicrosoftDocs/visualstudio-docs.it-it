---
title: Estensione di progetti SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 622596249e92d73dd4f504a445d43405847e9629
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
 Quando si crea un'estensione di progetto, l'estensione viene caricato quando si apre qualsiasi tipo di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include vari modelli di progetto SharePoint, ad esempio le definizioni di elenco e i tipi di contenuto, ricevitori di eventi. Tuttavia, è solo un tipo di progetto SharePoint. I tipi di progetto che vengono visualizzati nel **nuovo progetto** la finestra di dialogo sono solo i modelli che raggruppano uno o più elementi di progetto SharePoint. Poiché è presente un solo tipo di progetto SharePoint, le estensioni create per un progetto si applicano a tutti i progetti SharePoint. È possibile, ad esempio, creare un'estensione che si applica solo a un **tipo di contenuto** progetto.  
  
 Per accedere a una specifica istanza del progetto, gestire uno del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> gli eventi del *projectService* parametro nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo. Ad esempio, per determinare quando un progetto SharePoint viene aggiunto a una soluzione, gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Per ulteriori informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Procedura dettagliata: Creazione di un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Distribuzione ed estensione dei pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  