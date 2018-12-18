---
title: 'Procedura: creare un controllo utente per una pagina di applicazione di SharePoint Web Part o | Documenti Microsoft'
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7fc51bae65f67a3810c6db208e5f7c6f04183c22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint
  È possibile creare controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint in uso, nonché riutilizzare le funzionalità in questione all'interno del progetto. È possibile includere i controlli utente in una web part o in una pagina applicazione, aggiungere altri controlli ASP.NET e di SharePoint e definire proprietà e metodi per il controllo. Per ulteriori informazioni sui controlli utente, vedere [la creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [controlli utente e Server in SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Per creare un controllo utente per SharePoint  
  
1.  In Visual Studio aprire o creare un progetto SharePoint.  
  
     Vedere [modelli di elemento di progetto SharePoint e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
3.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
4.  Nel **installato** riquadro, scegliere il **Office/SharePoint** nodo.  
  
5.  Nell'elenco dei modelli di SharePoint, scegliere **controllo utente (solo soluzione Farm)**.  
  
    > [!NOTE]  
    >  I controlli utente possono essere utilizzati solo nelle soluzioni farm.  
  
6.  Nel **nome** , specificare un nome per il controllo utente e quindi scegliere il **Aggiungi** pulsante.  
  
     Visual Studio aggiunge diverse cartelle e file al progetto. Per ulteriori informazioni su questi file, vedere [la creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Per impostazione predefinita, il file di controllo utente viene visualizzato nel **origine** visualizzazione della finestra di progettazione di Visual Web Developer. In questa visualizzazione è possibile modificare il markup XML del controllo. È possibile passare a **progettazione** visualizzare se si desidera progettare visivamente il controllo trascinando i controlli dal **della casella degli strumenti**. Vedere [visualizzazione progettazione, progettazione pagine Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Se si desidera gestire eventi che si verificano nel controllo, aggiungere codice al file di codice del controllo utente.  
  
     Questo file viene visualizzato in **Esplora** nel file di controllo utente e ha un'estensione cs o vb, a seconda del linguaggio del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di controlli utente riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  