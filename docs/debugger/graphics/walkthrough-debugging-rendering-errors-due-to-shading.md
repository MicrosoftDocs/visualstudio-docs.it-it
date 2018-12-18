---
title: 'Procedura dettagliata: Debug degli errori a causa dello sfondo di Rendering | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 55638339935639c5d7bcb726f981b7edecdcadca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Procedure dettagliate: debug degli errori di rendering dovuti allo sfondo
Questa procedura dettagliata descrive come usare Diagnostica grafica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per esaminare un problema dovuto a un oggetto colorato in modo non corretto a causa di un bug dello shader.  
  
 Questa procedura dettagliata illustra come:  
  
-   Esaminare il documento del log di grafica per identificare i pixel che presentano il problema.  
  
-   Usare la finestra **Cronologia pixel grafica** per esaminare in dettaglio lo stato dei pixel.  
  
-   Usare il **debugger HLSL** per esaminare pixel shader e vertex shader.  
  
## <a name="scenario"></a>Scenario  
 Una colorazione non corretta per gli oggetti si verifica in genere quando un vertex shader passa informazioni errate o incomplete a un pixel shader.  
  
 In questo scenario, è stato aggiunto di recente un oggetto all'app, oltre a nuovi vertex shader e pixel shader per trasformare l'oggetto e assegnargli un aspetto univoco. Quando si esegue l'app durante un test, l'oggetto viene visualizzato in nero a tinta unita. Usando gli strumenti di Diagnostica della grafica, è possibile acquisire il problema in un log di grafica in modo da poter eseguire il debug dell'app. Nell'app, il problema si presenta nel modo seguente:  
  
 ![L'oggetto viene eseguito il rendering con colori non corretti. ] (media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Analisi  
 Utilizzando gli strumenti di diagnostica della grafica, è possibile caricare il documento del log di grafica per controllare i frame acquisiti durante il test.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Per esaminare un frame in un log di grafica  
  
1.  In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]caricare un log di grafica contenente un frame che mostra il modello mancante. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]viene visualizzata una nuova finestra del documento del log di grafica. Nella parte superiore di questa finestra è presente l'output della destinazione di rendering del frame selezionato. Nella parte inferiore è presente **Elenco frame**, che visualizza ogni frame acquisito come immagine di anteprima.  
  
2.  In **Elenco frame**selezionare un frame in cui l'oggetto non ha l'aspetto corretto. La destinazione di rendering viene aggiornata per riflettere la selezione del frame. In questo scenario la finestra del documento del log di grafica ha il seguente aspetto:  
  
     ![Log grafico in Visual Studio. ] (media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")  
  
 Dopo aver selezionato un frame che dimostra il problema, è possibile usare la finestra **Cronologia pixel grafica** per diagnosticarlo. La finestra **Cronologia pixel grafica** mostra le primitive che potrebbero aver avuto un effetto su un pixel specifico, i relativi shader e gli effetti corrispondenti sulla destinazione di rendering, in ordine cronologico.  
  
#### <a name="to-examine-a-pixel"></a>Per esaminare un pixel  
  
1.  Aprire la finestra **Cronologia pixel grafica** . Scegliere **Cronologia pixel** sulla barra degli strumenti **Diagnostica grafica**.  
  
2.  Selezionare un pixel da esaminare. Nella finestra del documento del log di grafica selezionare uno dei pixel nell'oggetto non colorato correttamente:  
  
     ![Selezione di un pixel consente di visualizzare informazioni sulla relativa cronologia. ] (media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")  
  
     La finestra **Cronologia pixel grafica** viene aggiornata in base al pixel selezionato. In questo scenario la finestra **Cronologia pixel grafica** ha questo aspetto:  
  
     ![La cronologia pixel Mostra un evento DrawIndexed. ] (media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")  
  
     Si noti che il risultato del pixel shader è nero completamente opaco (0, 0, 0, 1) e che **Unione output** ha combinato questo risultato con il colore **Precedente** del pixel in modo che anche **Risultato** sia nero completamente opaco.  
  
 Dopo aver esaminato un pixel colorato in modo errato e aver appurato che il colore dell'output del pixel shader non è quello previsto, è possibile usare il debugger HLSL per esaminare il pixel shader e scoprire cosa è successo al colore dell'oggetto. È possibile usare il debugger HLSL per esaminare lo stato delle variabili HLSL durante l'esecuzione, eseguire il codice HLSL un'istruzione alla volta e impostare i punti di interruzione per facilitare la diagnosi del problema.  
  
#### <a name="to-examine-the-pixel-shader"></a>Per esaminare il pixel shader  
  
1.  Avviare il debug del pixel shader. Nella finestra **Cronologia pixel grafica** , nella primitiva dell'oggetto, accanto a **Pixel shader**scegliere il pulsante **Avvia debug** .  
  
2.  In questo scenario, poiché il pixel shader passa semplicemente il colore dal vertex shader, è facile concludere che il pixel shader non è l'origine del problema.  
  
3.  Posizionare il puntatore su `input.color`. Si noti che il relativo valore è nero completamente opaco (0, 0, 0, 1).  
  
     ![Il membro "color" di "input" è nero. ] (media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")  
  
     In questo scenario un'analisi rivela che il colore non corretto è probabilmente il risultato di un vertex shader che non fornisce informazioni corrette sul colore perché possano essere utilizzate dal pixel shader.  
  
 Una volta determinato che il vertex shader non fornisce probabilmente le informazioni corrette al pixel shader, il passaggio successivo consiste nell'esaminare il vertex shader.  
  
#### <a name="to-examine-the-vertex-shader"></a>Per esaminare il vertex shader  
  
1.  Avviare il debug del vertex shader. Nella finestra **Cronologia pixel grafica** , nella primitiva dell'oggetto, accanto a **Vertex shader**scegliere il pulsante **Avvia debug** .  
  
2.  Individuare la struttura di output del vertex shader, ovvero l'input per il pixel shader. In questo scenario, il nome di questa struttura è `output`. Esaminare il codice di vertex shader e notare che il membro `color` della struttura `output` è stato impostato in modo esplicito su nero completamente opaco, probabilmente a causa delle attività di debug di un utente.  
  
3.  Verificare che il membro del colore non venga mai copiato dalla struttura di input. Poiché il valore di `output.color` è impostato su nero completamente opaco immediatamente prima che il `output` struttura viene restituita, è consigliabile verificare che il valore di `output` non è stato correttamente inizializzato in una riga precedente. Eseguire il codice di vertex shader un'istruzione alla volta fino al raggiungimento della riga tramite cui si imposta `output.color` su nero durante l'analisi del valore di `output.color`. Si noti che il valore di `output.color` non viene inizializzato fino a quando non viene impostato su nero. In questo modo viene confermato che la riga di codice tramite cui si imposta `output.color` su nero deve essere modificata, anziché eliminata.  
  
     ![Il valore di "Color" è nero. ] (media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")  
  
 Una volta determinato che la causa del problema di rendering è che il vertex shader non fornisce un valore di colore corretto al pixel shader, è possibile utilizzare queste informazioni per correggere il problema. In questo scenario è possibile correggere l'errore modificando il codice seguente nel vertex shader  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 in  
  
```hlsl  
output.color = input.color;  
```  
  
 Questo codice passa semplicemente il colore del vertice dai vertici dell'oggetto senza modifiche. Vertex shader più complessi potrebbero modificare il colore prima di passarlo. Il codice corretto del vertex shader dovrebbe essere simile al seguente:  
  
 ![Codice corretto del vertex shader. ] (media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Dopo aver corretto il codice, ricompilare ed eseguire l'app per verificare che il problema di rendering sia stato risolto:  
  
 ![L'oggetto viene eseguito il rendering con colori corretti. ] (media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")