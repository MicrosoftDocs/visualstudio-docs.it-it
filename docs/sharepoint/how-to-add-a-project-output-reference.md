---
title: "Procedura: aggiungere un riferimento all'Output del progetto | Documenti Microsoft"
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
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8be3cd7576dcd42391c2f1bda1bd2d997ea958ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Procedura: aggiungere un riferimento all'output del progetto
  Per distribuire gli assembly di progetto SharePoint non (o file con estensione xap nei progetti Silverlight) in SharePoint, aggiungerli come un riferimento all'output del progetto.  
  
 Questo processo crea una dipendenza di compilazione di soluzioni tra i due progetti. Progetti associati riferimenti all'output del progetto vengono compilati prima della compilazione e distribuzione del progetto SharePoint.  
  
### <a name="to-add-a-project-output-reference"></a>Per aggiungere un riferimento all'Output del progetto  
  
1.  Caricare una soluzione che contiene almeno un progetto SharePoint e un progetto di SharePoint non.  
  
2.  In **Esplora**, scegliere un elemento nel nodo di progetto SharePoint.  
  
3.  Nel **proprietà** finestra, scegliere il **riferimenti all'Output del progetto** proprietà, quindi scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP. Ellisse di progettazione per dispositivi mobili NET")) accanto a essa.  
  
4.  Nel **riferimenti all'Output del progetto** finestra di dialogo scegliere la **Aggiungi** pulsante.  
  
5.  Nel riquadro proprietà, scegliere la freccia accanto al **tipo di distribuzione** proprietà, quindi scegliere un valore appropriato per l'elemento di SharePoint non viene fatto riferimento, ad esempio **ElementFile**.  
  
6.  Scegliere la freccia accanto a **nome progetto**, scegliere il nome dell'elemento di progetto non SharePoint, quindi il **OK** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica sui pacchetti e informazioni sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  