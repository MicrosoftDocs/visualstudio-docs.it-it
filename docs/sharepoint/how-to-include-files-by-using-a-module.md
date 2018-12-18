---
title: 'Procedura: includere file mediante un modulo | Documenti Microsoft'
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
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ebefc0420eba48fdc53e68482a96a575111e536f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-files-by-using-a-module"></a>Procedura: includere file mediante un modulo
  *I moduli* (da non confondere con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli) sono contenitori che consentono di distribuire i file, ad esempio pagine master ASPX, file di testo o immagini in SharePoint.  
  
 È possibile scegliere di distribuire un file in una raccolta documenti o come un normale file (ad esempio default.aspx) all'esterno di una raccolta documenti. Per aggiungere un file in una raccolta documenti, specificare `Type="GhostableInLibrary"` come attributo di **File** elemento. Questa impostazione indica a SharePoint per creare un elemento di elenco da utilizzare con il file quando viene aggiunto alla raccolta. Per distribuire un file all'esterno di una raccolta documenti, specificare `Type="Ghostable"` oppure omettere semplicemente il **tipo** attributo.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Aggiunta di un modulo a una soluzione di SharePoint  
  
#### <a name="to-add-a-module"></a>Per aggiungere un modulo  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire o creare un progetto SharePoint.  
  
     Per ulteriori informazioni, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Nell'elenco dei modelli di SharePoint, scegliere il **modulo** modello, quindi scegliere il **Aggiungi** pulsante.  
  
     Con questo passaggio viene creato un nodo nel progetto denominato Module1.  
  
4.  In Module1 eliminare il file Sample.txt.  
  
     Sample è incluso in tutti i nuovi moduli, ad esempio a scopo e non è necessaria. Si noti che anche l'eliminazione del file rimuove la voce dal file Elements.xml del modulo.  
  
5.  Se si desidera che i file per distribuire in una determinata struttura di cartelle in SharePoint, creare queste cartelle in Module1 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliendo il nodo Module1, quindi, nella barra dei menu, scegliendo **progetto**, **New Cartella**.  
  
6.  Scegliere la cartella in cui si desidera aggiungere il file, quindi nella barra dei menu scegliere **progetto**, **Aggiungi elemento esistente**.  
  
7.  Scegliere uno o più file che si desidera distribuire in SharePoint e quindi scegliere il **Aggiungi** pulsante.  
  
     Quando si aggiunge un file al progetto, viene automaticamente aggiunta una voce per tale file Elements.xml del modulo. Quando viene distribuito il progetto, i file vengono copiati nel server SharePoint, rispetto alla directory radice del progetto, specificata dal **File** dell'elemento **Url** attributo, ad esempio `Url="Module1/New Folder/SomeFile.doc`. Se si desidera modificare il percorso di distribuzione per un file, di spostare in un'altra cartella **Esplora** o modificare il relativo **Url** impostazione.  
  
8.  Per qualsiasi file che si desidera visualizzare in una raccolta documenti, aggiungere il `Type="GhostableInLibrary"` attributo per la voce nel file Elements.xml. Ad esempio,  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Distribuire il progetto.  
  
     Copiare i file nei percorsi specificati in SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Assemblaggio e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  