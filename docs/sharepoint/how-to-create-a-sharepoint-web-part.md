---
title: 'Procedura: creare una Web Part di SharePoint | Documenti Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27826859d2bac9b247132e7fcb2c3721b6d38092
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Procedura: creare una web part di SharePoint
  È possibile creare e personalizzare una web part aggiungendo un **Web Part** elemento a qualsiasi progetto SharePoint e quindi modificando il file di codice per la web part o tramite una finestra di progettazione. Per ulteriori informazioni, vedere [procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Per creare una Web Part di SharePoint  
  
1.  Creare o aprire un progetto SharePoint.  
  
     Per ulteriori informazioni, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto SharePoint in **Esplora** e quindi scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
4.  Nell'elenco dei modelli di SharePoint, scegliere **Web Part**.  
  
5.  Nel **nome** , specificare un nome per la web part e quindi scegliere il **Aggiungi** pulsante.  
  
     La web part viene visualizzata **Esplora**. Per ulteriori informazioni sui file che include una web part, vedere [creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  In **Esplora**, aprire il file di codice per la web part appena creata.  
  
     Se ad esempio il nome della Web part è WebPart1, aprire WebPart1.vb (in Visual Basic) o WebPart1.cs (in C#).  
  
7.  Nel file di codice aggiungere controlli al metodo <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Per un esempio, vedere [procedura dettagliata: creazione di una Web Part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procedura dettagliata: Creazione di una Web Part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  