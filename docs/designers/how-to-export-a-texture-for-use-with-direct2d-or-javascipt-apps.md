---
title: 'Procedura: Esportare una trama da usare con app Direct2D o Javascript | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cce24e1daeeded8482d43b64a3c81aebd06e22bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Procedura: Esportare una trama da usare con app Direct2D o Javascript
La pipeline di contenuti immagine può generare trame compatibili con le convenzioni di rendering interne di Direct2D. Le trame di questo genere sono adatte alle app che usano Direct2D e alle app UWP create mediante JavaScript.  
  
 Questo documento illustra le attività seguenti:  
  
-   Configurazione dell'immagine di origine che deve essere elaborata dalla pipeline di contenuti immagine.  
  
-   Configurazione della pipeline di contenuti immagine per generare una trama che è possibile usare in un'app JavaScript o Direct2D.  
  
    -   Generare un file con estensione dds compresso a blocchi.  
  
    -   Generare il valore alfa premoltiplicato.  
  
    -   Disabilitare la generazione di mipmap.  
  
## <a name="rendering-conventions-in-direct2d"></a>Convenzioni di rendering in Direct2D  
 Le trame usate nel contesto di Direct2D devono essere conformi alle convenzioni di rendering interne di Direct2D seguenti:  
  
-   Direct2D implementa la trasparenza e la traslucidità usando il valore alfa premoltiplicato. Le trame usate con Direct2D devono contenere i valori alfa premoltiplicati, anche se la trama non usa la trasparenza o la traslucidità. Per altre informazioni sul valore alfa premoltiplicato, vedere [Procedura: Esportare una trama con alfa premoltiplicati](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   La trama deve essere fornita in formato dds, usando uno dei formati di compressione a blocchi seguenti:  
  
    -   Compressione BC1_UNORM  
  
    -   Compressione BC2_UNORM  
  
    -   Compressione BC3_UNORM  
  
-   Le mipmap non sono supportate.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Per creare una trama compatibile con le convenzioni di rendering Direct2D  
  
1.  Iniziare con una trama di base. Caricare un'immagine esistente oppure crearne una nuova, come descritto in [Procedura: Creare una trama di base](../designers/how-to-create-a-basic-texture.md). Per supportare la compressione a blocchi in formato dds, specificare una trama con valori di larghezza e altezza multipli di quattro, ad esempio 100x100, 128x128 o 256x192. Poiché il mapping MIP non è supportato, la trama non deve essere quadrata e le dimensioni non devono essere una potenza di due.  
  
2.  Configurare il file di trama in modo che venga elaborato dalla pipeline di contenuti immagine. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato e quindi scegliere **Proprietà**. Nella pagina **Proprietà di configurazione**, **Generale**, impostare la proprietà **Tipo di elemento** su **Image Content Pipeline** (Pipeline di contenuti immagine). Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e che l'opzione **Exclude From Build** (Escludi da compilazione) sia impostata su **No**, quindi scegliere il pulsante **Applica**. Viene visualizzata la pagina delle proprietà di configurazione **Image Content Pipeline** (Pipeline di contenuti immagine).  
  
3.  Impostare il formato di output su uno dei formati compressi a blocchi. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Comprimi** su **BC3_UNORM compression (/compress:BC3_UNORM)** (Compressione BC3_UNORM (/compress:BC3_UNORM)). È possibile scegliere uno degli altri formati BC1, BC2 o BC3, in base alle specifiche esigenze. Direct2D attualmente non supporta le trame BC4, BC5, BC6 o BC7. Per altre informazioni sui diversi formati BC, vedere [Block Compression (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx) (Compressione a blocchi (Direct3D 10)).  
  
    > [!NOTE]
    >  Il formato di compressione specificato determina il formato del file generato dalla pipeline di contenuti immagine. Questo si differenzia dalla proprietà **Formato** dell'immagine di origine nell'editor di immagini, che determina il formato del file di immagine di origine così com'è archiviato su disco, ovvero il *formato di lavoro*. In genere, non è consigliabile usare un formato di lavoro compresso.  
  
4.  Configurare la pipeline di contenuti immagine in modo da generare output che usa il valore alfa premoltiplicato. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Convert to pre-multiplied alpha format** (Converti in formato alfa premoltiplicato) su **Sì (/generatepremultipliedalpha)**.  
  
5.  Configurare la pipeline di contenuti immagine in modo che non generi mipmap. Nella pagina **Proprietà di configurazione**, **Image Content Pipeline** (Pipeline di contenuti immagine), **Generale**, impostare la proprietà **Genera MIP** su **No**.  
  
6.  Fare clic sul pulsante **OK** .  
  
 Quando si compila il progetto, la pipeline di contenuti immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, generando anche valori alfa premoltiplicato. Il risultato viene copiato nella directory di output del progetto.