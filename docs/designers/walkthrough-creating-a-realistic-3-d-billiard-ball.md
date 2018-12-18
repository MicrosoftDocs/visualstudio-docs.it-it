---
title: 'Procedura dettagliata: creazione di una palla da biliardo tridimensionale realistica | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd49879c6c23981bc88eb4309fb6c7da8e215bd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>Procedura dettagliata: creazione di una palla da biliardo tridimensionale realistica
In questa procedura dettagliata viene illustrato come creare una palla da biliardo tridimensionale realistica utilizzando la Modalità progettazione shader e l'editor di immagini in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'aspetto tridimensionale della palla da biliardo viene raggiunto combinando diverse tecniche di shader con le risorse appropriate di trama.  
  
 Questo documento illustra le attività seguenti:  
  
-   Creazione dell'aspetto di base di una palla da biliardo utilizzando la forma e la trama.  
  
-   Aggiunta di profondità tramite il modello di illuminazione Lambert.  
  
-   Miglioramento dell'aspetto di base tramite l'utilizzo delle evidenziazioni speculari.  
  
-   Creazione di un senso di spazio tramite il riflesso dell'ambiente.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre dei componenti e delle abilità seguenti:  
  
-   Uno strumento per l'assemblaggio di trame in una mappa cubo, come lo strumento Trama di DirectX incluso in DirectX SDK del giugno 2010.  
  
-   Conoscenza dell'editor di immagini in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Conoscenza della Progettazione shader in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>Creazione dell'aspetto di base con la forma e la trama  
 In computer grafica gli elementi più semplici dell'aspetto sono forma e colore. In una simulazione sul computer, è normale utilizzare un modello tridimensionale per rappresentare la forma di un oggetto reale. Il dettaglio del colore viene quindi applicato alla superficie del modello tramite una mappa di trama.  
  
 In genere, potrebbe essere necessario chiedere a un esperto di creare un modello tridimensionale da poter utilizzare, ma poiché una palla da biliardo è una comune sfera, nella finestra di Progettazione shader è già incorporato un modello adeguato.  
  
 Una sfera è la forma di anteprima predefinita nella finestra di Progettazione shader. Se al momento si sta utilizzando una forma differente per visualizzare in anteprima lo shader, tornare alla sfera.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>Per visualizzare in anteprima lo shader utilizzando una sfera  
  
-   Nella barra degli strumenti Progettazione shader, scegliere **Anteprima con sfera.**  
  
 Nel prossimo passaggio verrà creato un programma shader che applica una trama al modello, ma è necessario innanzitutto creare una trama da utilizzare. In questa procedura dettagliata viene illustrato come creare una trama utilizzando l'editor di immagini incluso in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È tuttavia possibile utilizzare qualsiasi editor di immagini in grado di salvare la trama in un formato appropriato.  
  
 Assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Per creare una trama palla da biliardo utilizzando l'editor di immagini  
  
1.  Creare una trama da usare. Per informazioni su come aggiungere una trama al progetto, vedere la sezione Introduzione in [Editor di immagini](../designers/image-editor.md).  
  
2.  Impostare la dimensione dell'immagine in modo che la larghezza sia due volte l'altezza. Questa operazione è necessaria a causa della modalità con cui viene eseguito il mapping di una trama sulla superficie sferica della palla da biliardo. Per ridimensionare l'immagine, nella finestra **Proprietà**, specificare i nuovi valori per le proprietà **Larghezza** e **Altezza**. Ad esempio, impostare la larghezza su 512 e l'altezza su 256.  
  
3.  Disegnare una trama per la palla da biliardo, tenendo presente il modo in cui la trama viene mappata su una sfera.  
  
     La trama dovrebbe essere simile a quella seguente:  
  
     ![Trama per la palla da biliardo](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4.  Facoltativamente, è possibile ridurre i requisiti di archiviazione della trama. È possibile eseguire questa operazione riducendo la larghezza della trama in modo che corrisponda all'altezza. In questo modo la trama viene compressa lungo la larghezza, ma dal momento che la trama è mappata alla sfera, verrà espansa quando verrà eseguito il rendering della palla da biliardo. Dopo il ridimensionamento, la trama dovrebbe essere simile alla seguente:  
  
     ![Trama del biliardo compressa in un quadrato](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
 È ora possibile creare uno shader che applica questa trama al modello.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Per creare uno shader con trama di base  
  
1.  Creare uno shader DGSL da utilizzare. Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione Introduzione in [Finestra di progettazione shader](../designers/shader-designer.md).  
  
     Per impostazione predefinita, un grafico shader è simile al seguente:  
  
     ![Grafico shader predefinito](../designers/media/gfx_shader_demo_billiard_step_0.png "gfx_shader_demo_billiard_step_0")  
  
2.  Modificare lo shader predefinito in modo da applicare il valore di un esempio di trama al pixel corrente. Il grafico di shader dovrebbe avere un aspetto simile al seguente:  
  
     ![Grafico shader per l'applicazione di una trama a un oggetto](../designers/media/gfx_shader_demo_billiard_step_1.png "gfx_shader_demo_billiard_step_1")  
  
3.  Applicare la trama creata nella procedura precedente configurando le proprietà della trama. Impostare il valore della proprietà **Trama** del nodo **Campione trama** su **Trama1**, quindi specificare il file di trama utilizzando la proprietà **Nome file** del gruppo di proprietà **Trama1** nella stessa finestra della proprietà.  
  
 Per ulteriori informazioni su come applicare una trama allo shader, vedere [Procedura: Creare uno shader con trama di base](../designers/how-to-create-a-basic-texture-shader.md).  
  
 La palla da biliardo dovrebbe ora risultare simile alla seguente:  
  
 ![Primo piano della palla da biliardo con trama](../designers/media/gfx_shader_demo_.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>Creazione di profondità con il modello di illuminazione Lambert  
 Per ora, è stata creata una palla da biliardo facilmente riconoscibile. Tuttavia, appare piana e non interessante (più simile un'immagine di un fumetto di una palla da biliardo che a una replica convincente). L'aspetto piano deriva dallo shader semplicistico, che si comporta come se ogni pixel sulla superficie della palla da biliardo ricevesse la stessa quantità di luce.  
  
 Nel mondo reale, la luce appare più luminosa su superfici rivolte direttamente verso una sorgente di luce e meno luminosa su superfici disposte obliquamente rispetto alla sorgente di luce. Il motivo è che, quando la superficie si trova direttamente di fronte alla sorgente di luce, l'energia nei raggi di luce è distribuita su una area di superficie più piccola. Mentre la superficie si allontana dalla sorgente di luce, la stessa quantità di energia viene distribuita in un'area sempre più grande. Una superficie non rivolta verso una fonte di luce non riceve alcuna energia, dando come risultato un aspetto completamente scuro. Questa varianza nella luminosità sulla superficie di un oggetto è un segnale visivo importante che consente di individuare la forma di un oggetto. Senza di essa, l'oggetto appare piatto.  
  
 In computer grafica, i *modelli di illuminazione*, ovvero approssimazioni semplificate di interazioni complesse di illuminazione reale, vengono utilizzati per replicare l'aspetto dell'illuminazione reale. Il modello di illuminazione di Lambert varia la quantità di luce diffusa riflessa sulla superficie di un oggetto, come descritto nel paragrafo precedente. È possibile aggiungere il modello di illuminazione di Lambert allo shader per conferire alla palla da biliardo un aspetto 3D più realistico.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>Per aggiungere l'illuminazione di Lambert allo shader  
  
-   Modificare lo shader per modulare il valore dell'esempio di trama dal valore di illuminazione di Lambert. Il grafico di shader dovrebbe avere un aspetto simile al seguente:  
  
     ![Grafico shader con illuminazione Lambert](../designers/media/gfx_shader_demo_billiard_step_2.png "gfx_shader_demo_billiard_step_2")  
  
-   Facoltativamente, è possibile regolare la modalità di comportamento dell'illuminazione configurando la proprietà **MaterialDiffuse** del grafico di shader. Per accedere alle proprietà del grafico di shader, scegliere un'area vuota dell'area di progettazione, quindi nella finestra **Proprietà** individuare la proprietà a cui si desidera accedere.  
  
 Per ulteriori informazioni su come applicare una illuminazione di Lambert allo shader, vedere [Procedura: Creare uno shader con trama di base](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Con l'illuminazione di Lambert applicata, la palla da biliardo dovrebbe risultare simile alla seguente:  
  
 ![Primo piano della palla da biliardo con trama e illuminata](../designers/media/gfx_shader_demo_billiard_ball_2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>Miglioramento dell'aspetto di base con le evidenziazioni speculari  
 Il modello di illuminazione di Lambert genera il senso di forma e dimensione che era assente nello shader a sola trama. Tuttavia, la palla da biliardo ha ancora un aspetto piatto.  
  
 Una palla da biliardo vera in genere ha una finitura brillante che riflette una parte della luce che ricade su di essa. Parte di questa luce riflessa produce evidenziazioni speculari, che simulano le proprietà riflettenti di una superficie. A seconda delle proprietà di completamento, le evidenziazioni possono essere localizzate o ampie, intense o delicate. Queste reflection speculari vengono modellate mediante la relazione tra una sorgente di luce, l'orientamento della superficie e la posizione della fotocamera. Ciò significa che l'evidenziazione è più intensa quando l'orientamento della superficie riflette la sorgente di luce direttamente nella fotocamera, mentre è meno intensa quando la reflection è meno diretta.  
  
 Il modello di illuminazione di Phong si basa sul modello di illuminazione di Lambert per includere le evidenziazioni speculari, come descritto nel paragrafo precedente. È possibile aggiungere il modello di illuminazione di Phong allo shader per conferire alla palla da biliardo una finitura simulata che produce un aspetto più interessante.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>Per aggiungere evidenziazioni speculari allo shader  
  
1.  Modificare lo shader per includere il contributo speculare tramite la fusione aggiuntiva. Il grafico di shader dovrebbe avere un aspetto simile al seguente:  
  
     ![Grafico shader con illuminazione speculare](../designers/media/gfx_shader_demo_billiard_step_3.png "gfx_shader_demo_billiard_step_3")  
  
2.  Facoltativamente, è possibile regolare la modalità di comportamento dell'evidenziazione speculare configurando le proprietà speculari (**MaterialSpecular** e **MaterialSpecularPower**) del grafico di shader. Per accedere alle proprietà del grafico di shader, scegliere un'area vuota dell'area di progettazione, quindi nella finestra **Proprietà** individuare la proprietà a cui si desidera accedere.  
  
 Per ulteriori informazioni su come applicare evidenziazioni speculari allo shader, vedere [Procedura: Creare uno shader con trama di base](../designers/how-to-create-a-basic-phong-shader.md).  
  
 Con l'illuminazione speculare applicata, la palla da biliardo dovrebbe risultare simile alla seguente:  
  
 ![Primo piano della palla da biliardo con illuminazione speculare](../designers/media/gfx_shader_demo_billiard_ball_3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>Creazione di un senso di spazio tramite il riflesso dell'ambiente  
 Con le evidenziazioni speculari applicate, l'aspetto della palla da biliardo sarà piuttosto convincente. Ha la forma giusta, il processo di disegno appropriato e la finitura corretta. Tuttavia, esiste anche un'altra tecnica che farà apparire la palla da biliardo più come parte del suo ambiente.  
  
 Se si esamina da vicino una palla da biliardo reale, è possibile vedere che la sua superficie lucida non presenta solo evidenziazioni speculari, ma riflette anche vagamente un'immagine dell'ambiente circostante. È possibile simulare la reflection utilizzando un'immagine dell'ambiente come trama e combinandola con la trama propria del modello per determinare il colore finale di ogni pixel. A seconda del tipo di completamento desiderato, è possibile combinare più o meno della trama di reflection con il resto dello shader. Ad esempio, uno shader che simula una superficie altamente riflettente come un'immagine speculare può utilizzare solo la trama di reflection, ma lo shader che simula una reflection meno evidente come quella presente in una palla da biliardo può combinare solo una piccola parte del valore della trama di reflection con il resto del calcolo di shader.  
  
 Naturalmente, non è possibile applicare solo l'immagine riflessa al modello allo stesso modo in cui si applica il mapping della trama del modello. In caso affermativo, la reflection dell'ambiente si sposterebbe con la palla da biliardo, come se vi fosse incollata. Poiché una reflection può provenire da qualsiasi direzione, è necessario un modo per fornire un valore del mapping della reflection per qualsiasi angolo e per mantenere il mapping di reflection orientato in base all'ambiente. Per rispondere a queste esigenze, è possibile utilizzare un tipo speciale di mappa di trama, chiamato *mappa cubo*, che dispone di sei trame disposte per formare i lati di un cubo. Nel cubo, è possibile puntare a qualsiasi direzione per individuare un valore di trama. Se le trame su ogni lato del cubo contengono immagini dell'ambiente, è possibile simulare eventuali riflessi mediante il campionamento della posizione corretta sulla superficie del cubo. Mantenendo il cubo allineato alla terra, si otterrà una reflection accurata dell'ambiente. Per determinare la posizione di campionatura del cubo, è sufficiente calcolare la reflection del vettore della fotocamera dalla superficie dell'oggetto, quindi utilizzarla come coordinate della trama tridimensionale. L'utilizzo di mappe cubo in questo modo è una tecnica comune nota come *mapping dell'ambiente*.  
  
 Il mapping dell'ambiente fornisce un'approssimazione efficace di reflection reali, come descritto nei paragrafi precedenti. È possibile sfumare le reflection mappate all'ambiente nello shader per conferire alla palla da biliardo una finitura simulata che la fa sembrare più integrata con la scena.  
  
 Il primo passaggio consiste nella creazione della trama della mappa cubo. In molti tipi di app il contenuto della mappa cubo non deve essere perfetto per essere efficace, specialmente quando la reflection è poco evidente o non occupa uno spazio rilevante sullo schermo. Ad esempio, molti giochi utilizzano mapping del cubo precedentemente elaborati per il mapping dell'ambiente e utilizzano solo quello più vicino a ogni oggetto riflettente, sebbene questo significhi che la reflection non è corretta. Anche una vaga approssimazione è spesso sufficiente per avere un effetto convincente.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Per creare le trame per un mapping dell'ambiente tramite l'editor di immagini  
  
1.  Creare una trama da usare. Per informazioni su come aggiungere una trama al progetto, vedere la sezione Introduzione in [Editor di immagini](../designers/image-editor.md).  
  
2.  Impostare la dimensione dell'immagine in modo che la larghezza sia uguale all'altezza e una potenza di due nelle dimensioni; ciò è necessario a causa della modalità con cui una mappa cubo è indicizzata. Per ridimensionare l'immagine, nella finestra **Proprietà**, specificare i nuovi valori per le proprietà **Larghezza** e **Altezza**. Ad esempio, impostare il valore delle proprietà **Larghezza** e **Altezza** su 256.  
  
3.  Utilizzare una tinta unita per riempire la trama. Questa trama sarà la parte inferiore della mappa cubo, che corrisponde alla superficie del tavolo da biliardo. Ricordare il colore utilizzato per la trama successiva.  
  
4.  Creare una seconda trama con la stessa dimensione della prima. La trama verrà ripetuta sui quattro lati della mappa cubo, che corrispondono alla superficie e ai lati di un tavolo da biliardo e all'area intorno al tavolo da biliardo. Assicurarsi di disegnare la superficie del tavolo da biliardo in questa trama utilizzando lo stesso colore della trama inferiore. La trama dovrebbe essere simile alla seguente:  
  
     ![Trama per i lati della mappa cubo](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
     Tenere presente che una mappa di reflection non deve essere fotorealistica per essere efficace; ad esempio, la mappa cubo utilizzata per creare le immagini di questo articolo contiene esattamente quattro caselle invece di sei.  
  
5.  Creare una terza trama con la stessa dimensione delle altre. Questa trama sarà la parte superiore della mappa cubo, che corrisponde all'area sopra il tavolo da biliardo. Per rendere questa parte della reflection più interessante, è possibile disegnare una luce sopraelevata per aumentare le evidenziazioni speculari aggiunte allo shader nella procedura precedente. La trama dovrebbe essere simile alla seguente:  
  
     ![Trama per la parte superiore della mappa cubo](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
 Dopo aver creato le singole trame per i lati della mappa cubo, è possibile utilizzare uno strumento per assemblarli in una mappa cubo che può essere memorizzata in una singola trama di .dds. È possibile utilizzare qualsiasi programma per creare la mappa cubo, a condizione che si possa salvare la mappa nel formato di trama .dds. In questa procedura dettagliata viene illustrato come creare una trama utilizzando lo strumento Trama di DirectX, incluso in DirectX SDK del giugno 2010.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Per assemblare una mappa cubo utilizzando lo strumento Trama di DirectX  
  
1.  Nello strumento Trama di DirectX, scegliere **File**, **New Texture** (Nuova trama) dal menu principale. Verrà visualizzata la finestra di dialogo **New Texture** (Nuova trama).  
  
2.  Nello gruppo **Texture Type** (Tipo trama), scegliere **Cubemap Texture** (Trama mappa cubo).  
  
3.  Nel gruppo **Dimensioni**, immettere il valore corretto per **Larghezza** e **Altezza**, quindi scegliere **OK**. Verrà visualizzato un nuovo documento a trama. Per impostazione predefinita, la trama mostrata per prima nel documento di trama corrisponde alla faccia del cubo **Positive X** (X positivo).  
  
4.  Caricare la trama creata per il lato del cubo di trama sulla faccia del cubo. Nel menu principale, scegliere **File**, **Open Onto This Cubemap Face** (Apri in questa faccia cubo), selezionare la trama creata per il lato del cubo, quindi scegliere **Apri**.  
  
5.  Ripetere il passaggio 4 per le facce del cubo **Negative X** (X negativo), **Positive Z** (Z positivo) e **Negative Z** (Z negativo). A tal fine, è necessario visualizzare la faccia che si desidera caricare. Per visualizzare un'altra faccia della mappa cubo, dal menu principale scegliere **Visualizza**, **Cube Map Face** (Faccia mappa cubo), quindi selezionare la faccia che si desidera visualizzare.  
  
6.  Per la faccia del cubo **Positive Y** (Y positivo), caricare la trama creata per la parte superiore del cubo di trama.  
  
7.  Per la faccia del cubo **Negative Y** (Y negativo), caricare la trama creata per la parte inferiore del cubo di trama.  
  
8.  Salvare la trama.  
  
 Il layout della mappa cubo avrà un aspetto simile a quello seguente:  
  
 ![Layout della mappa cubo dell'ambiente](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
 L'immagine nella parte superiore è la faccia del cubo Y (+Y) positiva, al centro, da sinistra a destra, ci sono le facce del cubo -X, +Z e -Z, mentre nella parte inferiore c'è la faccia del cubo -Y.  
  
 Ora è possibile modificare lo shader per integrare l'esempio di mappa cubo nel resto dello shader.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>Per aggiungere il mapping dell'ambiente allo shader  
  
1.  Modificare lo shader per includere il mapping dell'ambiente utilizzando la fusione aggiuntiva. Il grafico di shader dovrebbe avere un aspetto simile al seguente:  
  
     ![Primo piano di entrambi i tipi di nodi shader riflettenti](../designers/media/gfx_shader_demo_billiard_step_4b.png "gfx_shader_demo_billiard_step_4b")  
  
     Si noti che è possibile utilizzare un nodo **Multiply-Add** (Aggiunta multipla) per semplificare il grafico di shader.  
  
     Questa è una visualizzazione più dettagliata dei nodi di shader che implementano il mapping dell'ambiente:  
  
     ![Grafico shader con mapping dell'ambiente](../designers/media/gfx_shader_demo_billiard_step_4a.png "gfx_shader_demo_billiard_step_4a")  
  
2.  Applicare la trama creata nella procedura precedente configurando le proprietà della trama del mapping del cubo. Impostare il valore della proprietà **Trama** del nodo **Campione mappa cubi** su **Trama2**, quindi specificare il file di trama utilizzando la proprietà **Nome file** del gruppo di proprietà **Trama2**.  
  
3.  Facoltativamente, è possibile regolare la riflettività della palla da biliardo configurando la proprietà **Output** del nodo **Costante**. Per accedere alle proprietà del nodo, selezionarlo e quindi nella finestra **Proprietà** individuare la proprietà a cui si desidera accedere.  
  
 Con il mapping dell'ambiente applicato, la palla da biliardo risulterà simile alla seguente:  
  
 ![Primo piano della palla da biliardo con mappa dell'ambiente](../designers/media/gfx_shader_demo_billiard_ball_4.png "gfx_shader_demo_billiard_ball_4")  
  
 In questa immagine finale, osservare come gli effetti aggiunti convergono per creare una palla da biliardo molto convincente. La forma, la trama e l'illuminazione creano l'aspetto di base di un oggetto 3D e le evidenziazioni e i riflessi speculari abbelliscono la palla da biliardo e la rendono parte dell'ambiente che la circonda.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Esportare uno shader](../designers/how-to-export-a-shader.md)   
 [Procedura: Applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)   
 [Editor di immagini](../designers/image-editor.md)   
 [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)