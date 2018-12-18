---
title: 'Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f374bbbdf30a80bdea70b789da5d5febbeee7a82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Procedura dettagliata: oggetti mancanti a causa dello sfondo Vertex
Questa procedura dettagliata illustra come usare gli strumenti di Diagnostica della grafica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per esaminare un problema dovuto a un oggetto mancante a causa di un errore che si verifica durante la fase Vertex shader.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Uso dell' **Elenco eventi di grafica** per individuare le possibili origini del problema.  
  
-   Uso della finestra **Fasi pipeline grafica** per controllare l'effetto delle chiamate dell'API Direct3D `DrawIndexed` .  
  
-   Uso del **debugger HLSL** per esaminare il vertex shader.  
  
-   Uso di **Stack di chiamate eventi di grafica** per individuare l'origine di una costante HLSL non corretta.  
  
## <a name="scenario"></a>Scenario  
 Una delle cause comuni di un oggetto mancante in un'app 3D si verifica quando il vertex shader trasforma i vertici dell'oggetto in modo non corretto o imprevisto. Ad esempio, l'oggetto potrebbe essere ridimensionato con dimensioni molto piccole o trasformato in modo da essere visualizzato dietro la camera, anziché di fronte.  
  
 Quando in questo scenario l'app viene eseguita per essere testata, il rendering dello sfondo avviene nel modo previsto, ma uno degli oggetti non viene visualizzato. Usando gli strumenti di Diagnostica della grafica, è possibile acquisire il problema in un log di grafica in modo da poter eseguire il debug dell'app. Nell'app, il problema si presenta nel modo seguente:  
  
 ![L'oggetto non può essere visualizzato. ] (media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Analisi  
 Usando gli strumenti di Diagnostica della grafica è possibile caricare il file di log di grafica per esaminare i frame acquisiti durante il test.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Per esaminare un frame in un log di grafica  
  
1.  In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]caricare un log di grafica contenente un frame che mostra l'oggetto mancante. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]viene visualizzata una nuova scheda del log di grafica. Nella parte superiore di questa scheda è presente l'output della destinazione di rendering del frame selezionato. Nella parte inferiore è presente **Elenco frame**, che visualizza ogni frame acquisito come immagine di anteprima.  
  
2.  In **Elenco frame**selezionare un frame indicante che l'oggetto non è visualizzato. La destinazione di rendering viene aggiornata per riflettere la selezione del frame. In questo scenario la scheda del log di grafica ha un aspetto simile al seguente:  
  
     ![Log grafico in Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
 Dopo aver selezionato un frame che dimostra il problema, è possibile avviare la diagnosi tramite **Elenco eventi di grafica**. La finestra **Elenco eventi di grafica** contiene ogni chiamata API Direct3D effettuata per eseguire il rendering del frame attivo, ad esempio chiamate API per configurare lo stato del dispositivo, creare e aggiornare i buffer e disegnare gli oggetti visualizzati nel frame. Molti tipi di chiamate sono interessanti perché spesso, ma non sempre, si verifica una modifica corrispondente nella destinazione di rendering quando l'app funziona nel modo previsto, ad esempio le chiamate di disegno, invio, copia o eliminazione. Le chiamate di disegno sono particolarmente interessanti, perché ognuna rappresenta la geometria di cui l'app ha eseguito il rendering (anche le chiamate di invio possono eseguire il rendering della geometria).  
  
 Poiché è certo che in questo caso l'oggetto mancante non viene disegnato nella destinazione di rendering, sebbene il resto della scena venga disegnato come previsto, è possibile usare la finestra **Elenco eventi di grafica** insieme allo strumento **Fasi pipeline grafica** per determinare la chiamata di disegno che corrisponde alla geometria dell'oggetto mancante. La finestra **Fasi pipeline grafica** mostra la geometria inviata a ogni chiamata di disegno, indipendentemente dagli effetti sulla destinazione di rendering. Passando da una chiamata di disegno alla successiva, le fasi della pipeline vengono aggiornate per mostrare la geometria associata a ogni chiamata e l'output della destinazione di rendering viene aggiornato per mostrare lo stato della destinazione di rendering dopo il completamento della chiamata.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Per trovare la chiamata di disegno per la geometria mancante  
  
1.  Aprire la finestra **Elenco eventi di grafica** . Sulla barra degli strumenti **Diagnostica della grafica** scegliere **Elenco eventi**.  
  
2.  Aprire la finestra **Fasi pipeline grafica** . Sulla barra degli strumenti **Diagnostica della grafica** scegliere **Fasi pipeline**.  
  
3.  Passando da una chiamata di disegno alla successiva nella finestra **Elenco eventi di grafica** , esaminare la finestra **Fasi pipeline grafica** per individuare l'oggetto mancante. Per semplificare questa operazione, immettere "Draw" nella casella **Cerca** nell'angolo in alto a destra della finestra **Elenco eventi di grafica** . questo modo l'elenco viene filtrato in modo da contenere solo gli eventi nei cui titoli compare "Draw".  
  
     Nella finestra **Fasi pipeline grafica** la fase **Assembler input** mostra la geometria dell'oggetto prima che venga trasformata, mentre la fase **Vertex shader** mostra lo stesso oggetto una volta trasformato. In questo scenario, si avrà la certezza di aver trovato l'oggetto mancante quando l'oggetto viene visualizzato nella fase **Assembler input** ma non nella fase **Vertex shader** .  
  
    > [!NOTE]
    >  Se altre fasi della geometria, ad esempio la fase Hull shader, Domain shader o Geometry shader, elaborano l'oggetto, potrebbero essere la causa del problema. In genere, il problema è correlato alla prima fase il cui risultato non viene visualizzato o viene visualizzato in modo imprevisto.  
  
4.  Fermarsi quando si raggiunge la chiamata di disegno che corrisponde all'oggetto mancante. In questo scenario la finestra **Fasi pipeline grafica** indica che la geometria è stata inviata alla GPU (come indicato dalla presenza dell'anteprima Assemblaggio input), ma non è visualizzata nella destinazione di rendering perché qualcosa non ha funzionato durante la fase Vertex shader (come indicato dalla presenza dell'anteprima Vertex shader).  
  
     ![Evento DrawIndexed e relativo effetto sulla pipeline](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
 Dopo avere appurato che l'app ha inviato una chiamata di disegno per la geometria dell'oggetto mancante e aver scoperto che il problema si verifica durante la fase Vertex shader, è possibile usare il debugger HLSL per esaminare il vertex shader e scoprire cosa è successo alla geometria dell'oggetto. È possibile usare il debugger HLSL per esaminare lo stato delle variabili HLSL durante l'esecuzione, eseguire il codice HLSL un'istruzione alla volta e impostare i punti di interruzione per facilitare la diagnosi del problema.  
  
#### <a name="to-examine-the-vertex-shader"></a>Per esaminare il vertex shader  
  
1.  Avviare il debug della fase Vertex shader. Nella finestra **Fasi pipeline grafica** scegliere il pulsante **Avvia debug** per la fase **Vertex shader** .  
  
2.  Dato che la fase **Assemblaggio Input** sembra fornire dati validi al vertex shader e che la fase **Vertex shader** sembra non produrre alcun output, occorre esaminare la struttura di output del vertex shader, `output`. Durante l'esecuzione del codice HLSL un'istruzione alla volta, esaminare con attenzione il punto in cui viene modificato `output` .  
  
3.  Alla prima modifica di `output` viene scritto il membro `worldPos` .  
  
     ![Il valore di "output. worldpos" sembra ragionevole](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
     Dato che il relativo valore sembra ragionevole, si continua a eseguire il codice un'istruzione alla volta fino alla riga successiva che modifica `output`.  
  
4.  Alla successiva modifica di `output` viene scritto il membro `pos` .  
  
     ![Il valore di "output.pos" è stato azzerato](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
     Questa volta, il valore del membro `pos` (tutti zeri) sembra sospetto. A questo punto occorre stabilire come mai il valore di `output.pos` è composto da tutti zeri.  
  
5.  Si noti che `output.pos` prende il valore da una variabile denominata `temp`. Nella riga precedente, è possibile notare che il valore di `temp` è il risultato della moltiplicazione del valore precedente per una costante denominata `projection`. È possibile che il valore sospetto di `temp`sia il risultato di questa moltiplicazione. Posizionando il puntatore su `projection`si può notare che anche questo valore è composto da tutti zeri.  
  
     ![La matrice di proiezione contiene una trasformazione errata](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
     In questo scenario, un'ulteriore analisi rivela che il valore sospetto di `temp`è molto probabilmente causato dalla moltiplicazione per `projection`e dato che `projection` è una costante destinata a contenere una matrice di proiezione, è noto che non dovrebbe contenere tutti zeri.  
  
 Dopo aver determinato che la costante HLSL `projection`(passata nello shader dall'app) è l'origine probabile del problema, il passaggio successivo consiste nell'individuare la posizione nel codice sorgente dell'app in cui viene riempito il buffer costante. È possibile usare lo **Stack di chiamate eventi di grafica** per trovare questa posizione.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Per trovare la posizione in cui viene impostata la costante nel codice sorgente dell'app  
  
1.  Aprire la finestra **Stack di chiamate eventi di grafica** . Sulla barra degli strumenti **Diagnostica della grafica** scegliere **Stack di chiamate eventi di grafica**.  
  
2.  Spostarsi verso l'alto nello stack di chiamate nel codice sorgente dell'app. Nella finestra **Stack di chiamate eventi di grafica** scegliere la chiamata posizionata più in alto per verificare se il buffer costante viene riempito in quella posizione. In caso contrario, continuare a risalire lo stack di chiamate fino a trovare la posizione in cui viene riempito. In questo scenario, si scopre che il buffer costante viene riempito (tramite l'API Direct3D `UpdateSubresource` ) ancora più in alto nello stack di chiamate in una funzione denominata `MarbleMaze::Render`e che il relativo valore proviene da un oggetto buffer costante denominato `m_marbleConstantBufferData`:  
  
     ![Il codice che imposta il buffer dell'oggetto costante](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
    > [!TIP]
    >  Se si sta eseguendo contemporaneamente il debug dell'app, è possibile impostare un punto di interruzione in questa posizione e tale punto verrà raggiunto durante il rendering del frame successivo. È quindi possibile esaminare i membri di `m_marbleConstantBufferData` per confermare che il valore del membro `projection` viene impostato su tutti zeri quando viene riempito il buffer costante.  
  
 Dopo aver individuato la posizione in cui viene riempito il buffer costante e scoperto che i relativi valori provengono dalla variabile `m_marbleConstantBufferData`, il passaggio successivo consiste nel trovare la posizione in cui il membro `m_marbleConstantBufferData.projection` viene impostato su tutti zeri. È possibile usare **Trova tutti i riferimenti** per individuare rapidamente il codice che cambia il valore di `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Per trovare la posizione in cui viene impostato il membro projection nel codice sorgente dell'app  
  
1.  Trovare i riferimenti a `m_marbleConstantBufferData.projection`. Aprire il menu di scelta rapida per la variabile `m_marbleConstantBufferData`e quindi scegliere **Trova tutti i riferimenti**.  
  
2.  Per passare alla posizione della riga nel codice sorgente dell'app in cui viene modificato il membro `projection` , scegliere la riga nella finestra **Risultati ricerca simbolo** . Dato che il primo risultato corrispondente alla modifica del membro projection potrebbe non essere la causa del problema, è possibile che sia necessario esaminare varie aree del codice sorgente dell'app.  
  
 Dopo aver individuato la posizione in cui viene impostato `m_marbleConstantBufferData.projection` , è possibile esaminare il codice sorgente circostante per determinare l'origine del valore non corretto. In questo scenario, si scopre che il valore di `m_marbleConstantBufferData.projection` è impostato su una variabile locale denominata `projection` prima dell'inizializzazione su un valore fornito da `m_camera->GetProjection(&projection);` nel codice nella riga successiva.  
  
 ![La proiezione Marmo impostata prima dell'inizializzazione](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
 Per risolvere il problema, spostare la riga di codice che imposta il valore di `m_marbleConstantBufferData.projection` dopo la riga che inizializza il valore della variabile locale `projection`.  
  
 ![La corretta C &#43; &#43; codice sorgente](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
 Dopo aver corretto il codice, è possibile ricompilare ed eseguire l'app di nuovo per verificare che il problema di rendering sia stato risolto:  
  
 ![L'oggetto nuovamente visibile. ] (media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")