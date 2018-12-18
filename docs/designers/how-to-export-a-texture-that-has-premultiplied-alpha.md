---
title: 'Procedura: Esportare una trama con valori alfa premoltiplicati | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f0c8267d1153cf5ea112573e8af5c82ad7e8e805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Procedura: esportare una trama con alfa premoltiplicati
La pipeline di contenuti immagine può generare trame con valori alfa premoltiplicati da un'immagine di origine. Queste trame possono essere più semplici da usare e più solide delle trame che non contengono valori alfa premoltiplicati.  
  
 Questo documento illustra le attività seguenti:  
  
-   Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.  
  
-   Configurazione della pipeline di contenuti immagine per generare valori alfa premoltiplicati.  
  
## <a name="premultiplied-alpha"></a>Valori alfa premoltiplicati  
 I valori alfa premoltiplicati offrono diversi vantaggi rispetto ai valori convenzionali non premoltiplicati, perché rappresentano meglio l'interazione reale di luce con materiali fisici separando il contributo di colore del texel (il colore che viene aggiunto all'immagine) dalla traslucidità (la quantità di colore sottostante consentita). Alcuni dei vantaggi dell'uso di valori alfa premoltiplicati sono:  
  
-   La fusione con valori alfa premoltiplicati è un'operazione associativa. Il risultato della fusione di più trame traslucide è simile, indipendentemente dall'ordine in cui vengono fuse le trame.  
  
-   Grazie alla natura associativa della fusione con valori alfa premoltiplicati, il rendering a più passaggi degli oggetti traslucidi risulta semplificato.  
  
-   Tramite l'uso di valori alfa premoltiplicati, la fusione correttiva pura (impostando alfa su zero) e la fusione interpolata linearmente possono essere realizzate contemporaneamente. Ad esempio, in un sistema di particelle, una particella Fuoco fusa in modo cumulativo può diventare una particella Fumo semitrasparente che viene fusa tramite l'interpolazione lineare. Senza valori alfa premoltiplicati, sarebbe necessario disegnare le particelle Fuoco separatamente dalle particelle Fumo e modificare lo stato di rendering tra le chiamate di disegno.  
  
-   Le trame che usano valori alfa premoltiplicati vengono compresse con una qualità superiore alle altre e non presentano bordi offuscati o "effetti aureola"causati dalla fusione di trame che non usano valori alfa premoltiplicati.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Per creare una trama che usa valori alfa premoltiplicati  
  
1.  Iniziare con una trama di base. Caricare un file d'immagine esistente oppure crearne uno nuovo, come illustrato in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md).  
  
2.  Configurare il file di trama in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni**, aprire il menu di scelta rapida del file della trama e scegliere **Proprietà**. Nella pagina **Proprietà di configurazione**, **Generale**, impostare la proprietà **Tipo di elemento** su **Image Content Pipeline** (Pipeline di contenuti immagine). Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).  
  
3.  Configurare la pipeline di contenuti immagine per generare valori alfa premoltiplicati. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Convert to pre-multiplied alpha format** (Converti in formato alfa premoltiplicato) su **Sì (/generatepremultipliedalpha)**.  
  
4.  Fare clic sul pulsante **OK** .  
  
 Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato. Ciò include la conversione dell'immagine nel formato alfa premoltiplicato. Il risultato viene copiato nella directory di output del progetto.