---
title: 'Procedura: importare una pagina Master o un tema | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e60977a44593953b4858ea0262befc61c3189cec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procedura: importare una pagina master o un tema
  È possibile assegnare pagine nel sito di SharePoint un aspetto coerente mediante la creazione e utilizzo di temi e pagine master. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non fornisce modelli per tali elementi, ma è possibile crearli in SharePoint Designer e importarle quindi in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [blocco predefinito: pagine e interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095) del sito Web Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Per importare una pagina master o un tema  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare o aprire un progetto SharePoint.  
  
     Per informazioni su come creare un progetto SharePoint, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
4.  Nell'elenco dei modelli di SharePoint, scegliere il **modulo** modello, quindi specificare un nome per il modulo.  
  
     Un modulo contiene file (ad esempio, la pagina master o file di tema) per la distribuzione in un percorso specificato in SharePoint.  
  
5.  Nel modulo, eliminare il file predefinito, denominato Sample.  
  
6.  Scegliere il nodo del modulo.  
  
7.  Nella barra dei menu, scegliere **progetto**, **Aggiungi elemento esistente**, quindi scegliere il file di tema o pagina master.  
  
     File della pagina master hanno estensione master e file di tema è un'estensione con estensione thmx.  
  
8.  Se si aggiunge una pagina master, modificare il relativo **risoluzione conflitti di distribuzione** impostando su **automatica** nelle proprietà del modulo.  
  
    > [!NOTE]  
    >  Se il nome della pagina master è identico al nome di una pagina master esistente che è contrassegnata come pagina Master predefinita o pagina Master personalizzata, possono verificarsi errori. Per informazioni su come risolvere questo problema, vedere [procedura dettagliata: importare una pagina Master personalizzata e una pagina del sito con un'immagine](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Nel modulo, aprire Elements.xml.  
  
     È necessario aggiornare il file Elements.xml per fare riferimento alla pagina master o un tema che è stato aggiunto.  
  
10. Per una pagina master, sostituire il markup del modulo esistente con il markup seguente.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Per un tema, sostituire il markup del modulo esistente con il markup seguente.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Assicurarsi di sostituire i valori segnaposto con i nomi effettivi del modulo e la pagina master o del tema.  
  
     L'attributo `Type="GhostableInLibrary"` indica che l'elemento viene aggiunto al database del contenuto e `Url` attributo del modulo specifica dove archiviare il file nel database del contenuto di SharePoint.  
  
11. Per modificare l'ambito di distribuzione per una pagina master, in **Esplora**, aprire il file di funzionalità nella finestra di progettazione di funzionalità e quindi scegliere un nuovo ambito di distribuzione dal **ambito** elenco.  
  
     Il valore **Web** significa che la pagina master si applica solo al sito Web attualmente specificato nel progetto. Il valore **sito** significa che la pagina master si applica la raccolta siti corrente, che include tutti i siti secondari e il sito web radice. Non si applicano gli altri valori.  
  
    > [!NOTE]  
    >  Poiché i temi si applicano solo a livello di raccolta siti, è consigliabile non impostare l'ambito di un tema a un valore diverso da **sito**. Possono verificarsi errori se viene usato un tema in un sito secondario.  
  
12. Nella barra dei menu, scegliere **compilare**, **Distribuisci soluzione**.  
  
13. Per verificare se i file sono stati distribuiti correttamente, aprire il sito di SharePoint, scegliere il **Azioni sito** menu, scegliere il **Impostazioni sito** comandi e quindi scegliere il **pagine Master**  collegamento o **temi** collegamento.  
  
     L'elenco di pagine master o temi viene visualizzata e contiene la pagina master o il tema è stato importato.  
  
## <a name="see-also"></a>Vedere anche  
 [Pagine master](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Creazione di pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Uso di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  