---
title: Fasi della Pipeline grafica | Documenti Microsoft
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 393661fba27341ec858aa5c099ea9d131e42273a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-pipeline-stages"></a>Fasi pipeline grafica
La finestra Fasi Pipeline grafica aiuta a comprendere come una singola chiamata di disegno viene trasformata in ogni fase della pipeline grafica Direct3D.  
  
 Questa è la finestra Fasi pipeline:  
  
 ![Un oggetto 3D passa attraverso le fasi della pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Informazioni sulla finestra Fasi pipeline grafica  
 La finestra Fasi pipeline visualizza i risultati di ogni fase della pipeline grafica, separati per ogni chiamata di disegno. In genere i risultati delle fasi nella parte centrale della pipeline sono nascosti e questo rende difficile individuare le cause di un problema di rendering. Visualizzando separatamente ogni fase, la finestra Fasi pipeline consente di individuare facilmente l'origine del problema, ad esempio se una fase di vertex shader ha fatto sì che un oggetto venisse disegnato fuori dallo schermo.  
  
 Dopo avere identificato la fase in cui si verifica il problema, è possibile usare gli altri strumenti di Analizzatore grafica per esaminare il modo in cui i dati sono stati interpretati o trasformati. I problemi di rendering visualizzati nelle fasi della pipeline sono spesso correlati a descrittori di formato vertici non corretti, a programmi shader con bug o a uno stato non configurato correttamente.  
  
### <a name="links-to-related-graphics-objects"></a>Collegamenti a oggetti grafici correlati  
 A volte per capire perché una chiamata di disegno interagisce in un determinato modo con la pipeline grafica sono necessarie informazioni di contesto aggiuntive. Per semplificare la ricerca di queste informazioni, la finestra Fasi pipeline grafica contiene collegamenti a uno o più oggetti che forniscono ulteriore contesto correlato a ciò che accade nella pipeline grafica.  
  
-   In Direct3D 12 questo oggetto è in genere un elenco di comandi.  
  
-   In Direct3D 11 questo oggetto è in genere un contesto dei dispositivi grafici.  
  
 Questi collegamenti fanno parte della firma dell'evento grafico corrente situato nell'angolo superiore sinistro della finestra Fasi pipeline grafica. Seguire i collegamenti per accedere ad altri dettagli sull'oggetto.  
  
### <a name="viewing-and-debugging-shader-code"></a>Visualizzazione e debug del codice dello shader  
 Si può visualizzare il codice per Vertex Shader, Hull Shader, Domain Shader, Geometry Shader o Pixel Shader oppure eseguirne il debug, usando i controlli nella parte inferiore della fase corrispondente all'interno della finestra Fasi pipeline.  
  
#### <a name="to-view-a-shaders-source-code"></a>Per visualizzare il codice sorgente di uno shader  
  
-   Nel **fasi Pipeline grafica** finestra, individuare la fase dello shader che corrisponde allo shader da esaminare. Quindi, sotto l'immagine di anteprima, seguire il collegamento del titolo fase dello shader, ad esempio, seguire il collegamento **Vertex Shader obj: 30** per visualizzare il codice sorgente del vertex shader.  
  
    > [!TIP]
    >  Il numero dell'oggetto, **obj: 30**, identifica lo shader nell'intera interfaccia di Analizzatore grafica, ad esempio la finestra Cronologia pixel e tabella di oggetto.  
  
#### <a name="to-debug-a-shader"></a>Per eseguire il debug di uno shader  
  
-   Nel **fasi Pipeline grafica** finestra, individuare la fase dello shader che corrisponde allo shader da sottoporre a debug. Quindi, sotto l'immagine di anteprima, scegliere **Avvia debug**. Questo punto di ingresso nel debugger HLSL corrisponde per impostazione predefinita alla prima chiamata dello shader per la fase corrispondente, ovvero il primo vertice, primitiva o pixel elaborato durante questa chiamata di disegno. Le chiamate dello shader per uno specifico pixel o vertice è possibile accedere tramite il **cronologia Pixel grafica**.  
  
### <a name="the-pipeline-stages"></a>Fasi della pipeline  
 Nella finestra Fasi pipeline vengono visualizzate solo le fasi della pipeline che erano attive durante la chiamata di disegno. Ogni fase della pipeline grafica trasforma l'input dalla fase precedente e passa il risultato alla fase successiva. La prima fase, ovvero Assemblaggio input, estrae i dati di indici e vertici forniti dall'app e li usa come input. L'ultima fase, ovvero Unione output, combina i pixel di cui è stato eseguito il rendering con il contenuto corrente del buffer frame o della destinazione di rendering per produrre l'immagine finale visualizzata sullo schermo.  
  
> [!NOTE]
>  COMPUTE shader non sono supportati nel **fasi Pipeline grafica** finestra.  
  
 **Assemblaggio input**  
 Assemblaggio input legge i dati di indici e vertici specificati dall'app e li assembla per l'hardware grafico.  
  
 Nella finestra Fasi pipeline, l'output di Assemblaggio input viene visualizzato come modello wireframe. Per poter esaminare i risultati, selezionare **assemblaggio Input** nel **fasi Pipeline grafica** consente di visualizzare i vertici assemblati in 3D completo usando l'Editor di modelli.  
  
> [!NOTE]
>  Se il `POSITION` semantica non è presente nell'output dell'assemblaggio input, quindi viene visualizzato nulla nella **assemblaggio Input** fase.  
  
 **Vertex Shader**  
 La fase Vertex shader elabora i vertici, in genere eseguendo operazioni come trasformazioni, rivestimento e illuminazione. Produce lo stesso numero di vertici che accetta come input.  
  
 Nella finestra Fasi pipeline, l'output di Vertex shader viene visualizzato come immagine raster wireframe. Per poter esaminare i risultati, selezionare **Vertex Shader** nel **fasi Pipeline grafica** windows per visualizzare i vertici elaborati nell'Editor di immagini.  
  
> [!NOTE]
>  Se il `POSITION` o `SV_POSITION` semantica non è presente nell'output di vertex shader, quindi viene visualizzato nulla nella **Vertex Shader** fase.  
  
 **Hull Shader** (Direct3D 11 e Direct3D 12 solo)  
 La fase Hull shader elabora i punti di controllo che definiscono una superficie di ordine inferiore, ad esempio un quadrato, un triangolo o una linea. Come output, produce patch geometriche di ordine superiori e costanti patch che vengono passate alla fase del mosaico a funzione fissa.  
  
 La fase Hull shader non viene visualizzata nella finestra Fasi pipeline.  
  
 **Fase del mosaico** (Direct3D 11 e Direct3D 12 solo)  
 La fase del mosaico è un'unità hardware a funzione fissa (non programmabile) che preelabora il dominio rappresentato dall'output dello Hull shader. Come output, crea uno schema di campionamento del dominio e un set di primitive più piccole, punti, linee e triangoli, che connettono in questi campioni.  
  
 La fase del mosaico non viene visualizzata nella finestra Fasi pipeline.  
  
 **Domain Shader** (Direct3D 11 e Direct3D 12 solo)  
 La fase Domain shader elabora patch geometriche di ordine superiore provenienti da Hull shader, insieme a fattori a mosaico dalla fase del mosaico. I fattori a mosaico possono essere includere fattori di input della fase di mosaico così come fattori di output. Come output, calcola la posizione del vertice di un punto sulla patch di output in base ai fattori a mosaico.  
  
 La fase Domain shader non viene visualizzata nella finestra Fasi pipeline.  
  
 **Geometry Shader**  
 La fase Geometry shader elabora intere primitive, quali punti, linee o triangoli, insieme a informazioni opzionali sui vertici per le primitive adiacenti. A differenza dei vertex shader, i geometry shader possono produrre più o meno primitive che accettano come input.  
  
 Nella finestra Fasi pipeline, l'output di Geometry Shader viene visualizzato come immagine raster wireframe. Per poter esaminare i risultati, selezionare **Geometry Shader** nel **fasi Pipeline grafica** consente di visualizzare le primitive elaborate nell'Editor di immagini.  
  
 **Fase Output flusso**  
 La fase di output del flusso può intercettare primitive trasformate prima della rasterizzazione e scriverle in memoria. Da questa posizione, i dati possono essere riutilizzati come input per le prime fasi della pipeline grafica o essere nuovamente letti dalla CPU.  
  
 La fase Output flusso non viene visualizzata nella finestra Fasi pipeline.  
  
 **Fase di rasterizzazione**  
 La fase di rasterizzazione è un'unità hardware a funzione fissa (non programmabile) che converte le primitive vettoriali, come punti, linee e triangoli, in un'immagine raster, eseguendo una conversione per linee di scansione. Durante la rasterizzazione i vertici vengono trasformati nello spazio del ritaglio omogeneo e tagliati. Come output, viene eseguito il mapping dei pixel shader e gli attributi dei vertici della primitiva vengono interpolati e preparati per il pixel shader.  
  
 La fase di rasterizzazione non viene visualizzata nella finestra Fasi pipeline.  
  
 **Pixel Shader**  
 La fase Pixel shader elabora primitive rasterizzate insieme a dati di vertici interpolati per generare valori per pixel come colore e profondità.  
  
 Nella finestra Fasi pipeline, l'output di Pixel shader viene visualizzato come un'immagine raster a colori. Per poter esaminare i risultati, selezionare **Pixel Shader** nel **fasi Pipeline grafica** consente di visualizzare le primitive elaborate nell'Editor di immagini.  
  
 **Unione output**  
 La fase di unione output combina l'effetto dei pixel di cui è stato appena eseguito il rendering con il contenuto esistente dei buffer corrispondenti, ad esempio di colori, di profondità e di stencil, per produrre nuovi valori in questi buffer.  
  
 Nella finestra Fasi pipeline, l'output di Unione output viene visualizzato come un'immagine raster a colori. Per richiedere informazioni dettagliate sui risultati, selezionare **unione Output** nel **fasi Pipeline grafica** consente di visualizzare il buffer frame unito.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Vertex shader e anteprima di Geometry shader  
 Quando si seleziona la fase dello shader vertex o la geometria di **fasi Pipeline** finestra, è possibile visualizzare l'input e output da shader nel Pannello di seguito.  In questo caso, sono disponibili informazioni dettagliate relative all'elenco di vertici fornito per gli shader dopo l'assemblaggio dalla fase assemblaggio input.  

 ![Visualizzatore del buffer di input delle fasi del vertex shader](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Per visualizzare i risultati della fase Vertex shader, scegliere l'anteprima corrispondente per visualizzare un wireframe rasterizzato a dimensioni intere della mesh dopo la trasformazione.  
  
 ![Anteprima dei risultati delle fasi del vertex shader](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procedure dettagliate: debug degli errori di rendering dovuti allo sfondo](walkthrough-debugging-rendering-errors-due-to-shading.md)