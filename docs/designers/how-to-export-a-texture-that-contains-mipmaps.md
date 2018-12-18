---
title: 'Procedura: Esportare una trama che contiene mipmap | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ef8f94ae451902c8f7b5e5d2b5f3156d01107589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Procedura: esportare una trama che contiene mipmap
La pipeline di contenuti immagine può generare mipmap da un'immagine di origine come parte della fase di compilazione del progetto. Se non è necessario specificare manualmente il contenuto dell'immagine di ogni livello MIP, operazione che è possibile eseguire per ottenere alcuni effetti, la creazione di mipmap in fase di compilazione garantisce che il contenuto mipmap sia sempre sincronizzato e consente di eliminare i costi di prestazione per generare mipmap in fase di esecuzione.  
  
 Questo documento illustra le attività seguenti:  
  
-   Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.  
  
-   Configurazione di pipeline di contenuti immagine per generare mipmap.  
  
## <a name="exporting-mipmaps"></a>Esportazione di mipmap  
 La creazione di mipmap offre un livello di dettaglio automatico sullo spazio della schermata per aree con trame in giochi 3D o in app. Migliora le prestazioni di rendering di un gioco o di un'app pre-elaborando versioni a campionamento ridotto di una trama in modo che l'intera trama non debba essere elaborata ogni volta che viene campionata.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Per esportare una trama che contiene mipmap  
  
1.  Iniziare con una trama di base. Caricare un file d'immagine esistente oppure crearne uno nuovo, come illustrato in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per supportare le mipmap, specificare una trama la cui larghezza e altezza corrispondano a un valore esponenziale con base due, ad esempio, 64 x 64, 256 x 256 o 512 x 512.  
  
2.  Configurare il file di trama appena creato in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato e quindi scegliere **Proprietà**. Nella pagina **Proprietà di configurazione**, **Generale**, impostare la proprietà **Tipo di elemento** su **Image Content Pipeline** (Pipeline di contenuti immagine). Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).  
  
3.  Configurare la pipeline di contenuti immagine per generare mipmap. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Genera MIP** su **Sì (/generatemips)**.  
  
4.  Fare clic sul pulsante **OK** .  
  
 Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, includendo i livelli MIP. Il risultato viene copiato nella directory di output del progetto.