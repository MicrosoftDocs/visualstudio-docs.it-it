---
title: 'Procedura: aggiungere e rimuovere cartelle mappate | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 29809344ee8a3f446589ba84f2fc47b1cf407582
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Procedura: aggiungere e rimuovere cartelle mappate
  Alcune cartelle utilizzate comunemente in SharePoint, ad esempio immagini e layout di annidamento nella gerarchia dei file. È possibile eseguire il mapping di queste cartelle in un progetto di SharePoint per accedervi più facilmente. Cartelle mappate sono le cartelle nel progetto di SharePoint che corrispondono al percorso fisico dei file nell'installazione di SharePoint Server.  
  
 Quando si distribuisce un'applicazione di SharePoint, il contenuto della cartella mappata e tutte le relative sottocartelle vengono copiate dal pacchetto della soluzione (con estensione wsp) nel server che esegue SharePoint nel percorso specificato nella struttura di cartelle di SharePoint. Questo percorso è determinato dal **percorso di distribuzione** proprietà che è impostato per la cartella mappata. Tutte le sottocartelle della cartella mappata sono relativi **percorso di distribuzione** della cartella mappata. Si noti che il **percorso di distribuzione** determina di proprietà, non il nome della cartella mappata, in cui gli elementi da distribuire.  
  
 È possibile aggiungere cartelle mappate a un progetto tramite i comandi sulla barra dei menu o nel menu di scelta rapida per il progetto. È possibile utilizzare il **cartella mappata "Immagini" di SharePoint aggiungere** e **aggiungere SharePoint "Layout" cartella** i comandi da aggiungere a quelli associati le cartelle utilizzate più spesso. È possibile mappare una delle altre cartelle SharePoint disponibile per il progetto utilizzando il **Aggiungi cartella mappata di SharePoint** dal menu di scelta rapida e quindi specificare le cartelle di **Aggiungi cartella mappata di SharePoint** la finestra di dialogo.  
  
## <a name="adding-mapped-folders-to-a-project"></a>Aggiunta di cartelle mappate a un progetto  
 La procedura seguente viene descritto come aggiungere due cartelle mappate a un progetto di visual web part. Per iniziare, si crea un progetto di visual web part.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Per aggiungere le cartelle mappate a un progetto  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il il **Visual Basic** o **Visual c#** nodo, espandere il **Office/SharePoint** nodo, quindi Scegliere il **soluzioni SharePoint** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere il **Web Part visiva di SharePoint 2013** modello.  
  
4.  Nel **nome** immettere **TestProject1**, quindi scegliere il **OK** pulsante.  
  
5.  Nel **Personalizzazione guidata SharePoint**, scegliere il **fine** pulsante per mantenere le impostazioni predefinite.  
  
6.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **cartella mappata "Immagini" di SharePoint aggiungere**.  
  
     Una cartella denominata **immagini** viene visualizzato nel progetto e contiene una sottocartella denominata TestProject1. Questa cartella mappata conterrà le immagini per il progetto di visual web part.  
  
7.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi cartella mappata di SharePoint** per visualizzare il **Aggiungi Cartella mappata di SharePoint** la finestra di dialogo.  
  
8.  Nella visualizzazione albero delle cartelle che sono disponibili per il mapping, scegliere il **risorse** cartella, quindi scegliere il **OK** pulsante.  
  
     Una cartella denominata **risorse** viene visualizzata nel progetto. Questa cartella è possibile archiviare gli elementi, ad esempio i file di risorse di stringa. Le sottocartelle possono essere utile per organizzare il contenuto di una cartella mappata, ma vengono creati automaticamente quando si aggiunge una cartella mappata tramite il **Aggiungi cartella mappata di SharePoint** comando. Per aggiungere una sottocartella, scegliere il **risorse** cartella, quindi nella barra dei menu, scegliere **progetto**, **nuova cartella**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Modifica del percorso di distribuzione di una cartella mappata  
 Per impostazione predefinita, le cartelle mappate vengono aggiunti a posizioni specifiche relativo al percorso di installazione radice di SharePoint, indica il token {SharePointRoot}. Tuttavia, è possibile modificare questo percorso modificando il **percorso di distribuzione** proprietà della cartella mappata. Per ogni cartella mappata ha il proprio **percorso di distribuzione** proprietà.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Per modificare il percorso di distribuzione di una cartella mappata  
  
1.  Nel progetto creato in precedenza, scegliere una cartella mappata.  
  
2.  Nel **proprietà** finestra, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) sul pulsante di **distribuzione percorso** proprietà.  
  
3.  Nel **Aggiungi cartella mappata di SharePoint** la finestra di dialogo, passare alla cartella che si desidera scegliere la cartella mappata.  
  
4.  Scegliere il nodo e quindi scegliere il **OK** pulsante.  
  
## <a name="renaming-or-removing-mapped-folders"></a>La ridenominazione o rimozione di cartelle mappate  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Per rinominare o rimuovere una cartella mappata  
  
1.  Nel progetto creato in precedenza, scegliere una cartella mappata.  
  
2.  Per rinominare la cartella mappata, aprire il menu di scelta rapida, scegliere **rinominare**, immettere il nuovo nome e quindi premere INVIO.  
  
     In alternativa, è possibile scegliere la cartella mappata che si desidera rinominare, aprire il **proprietà** finestra e quindi impostare il valore della **nome della cartella** proprietà per il nuovo nome.  
  
3.  Per rimuovere una cartella mappata dal progetto, aprire il menu di scelta rapida, scegliere **eliminare**, quindi scegliere il **OK** pulsante nella finestra di dialogo per confermare la rimozione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  