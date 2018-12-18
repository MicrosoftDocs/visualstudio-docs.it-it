---
title: 'Procedura: creare una pagina applicazione | Documenti Microsoft'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9429f2834997ce5ad2c3359fb04c164995dd2e12
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-application-page"></a>Procedura: creare una pagina applicazione
  È possibile creare una pagina Web ASP.NET per uno o più siti di SharePoint. In SharePoint, queste pagine sono dette pagine dell'applicazione. A differenza di una pagina del sito, una pagina dell'applicazione contiene codice che viene eseguito dopo la pagina. Per ulteriori informazioni, vedere [la creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Per creare una pagina dell'applicazione  
  
1.  In Visual Studio aprire o creare un progetto SharePoint.  
  
     Per ulteriori informazioni, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
3.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
4.  Nel **Aggiungi nuovo elemento** finestra di dialogo, espandere il **SharePoint** nodo, quindi scegliere il **2010** elemento.  
  
5.  Nell'elenco dei modelli di SharePoint, scegliere **pagina applicazione**.  
  
6.  Nel **nome** , specificare un nome per la pagina dell'applicazione e quindi scegliere il **Aggiungi** pulsante.  
  
     Visual Studio aggiunge diverse cartelle e file al progetto. Per ulteriori informazioni su questi file, vedere [la creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     Nel **origine** visualizzazione della finestra di progettazione Visual Web Developer, il file della pagina ASP.NET è disponibile. È possibile progettare la pagina aggiungendo i controlli dal **della casella degli strumenti** e inserendoli nei segnaposti del contenuto. Per ulteriori informazioni, vedere [visualizzazione origine, progettazione della pagina Web](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Se si desidera gestire gli eventi di controllo, aggiungere il codice al file di codice per la pagina applicazione.  
  
     Il file di codice viene visualizzato se si espande il nodo per il file della pagina ASP.NET e presenta un'estensione cs o vb, a seconda del linguaggio del progetto. Per un esempio end-to-end di come creare una pagina applicazione, vedere [procedura dettagliata: creazione di una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  