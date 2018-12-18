---
title: 'Procedura: Creare un modello 3D di base | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b9a7bfb1d2eb3f54da0953a78d1e9630ed00aab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-3-d-model"></a>Procedura: Creare un modello tridimensionale di base
In questo documento viene illustrato come utilizzare l'editor modello per creare un modello 3D di base.  
  
 Questo documento illustra le attività seguenti:  
  
-   Aggiunta di oggetti a una scena  
  
-   Selezione di facce e bordi  
  
-   Traslazione delle selezioni  
  
-   Utilizzo degli strumenti **Suddividi faccia** e **Estrudi faccia**  
  
-   Utilizzo del comando **Triangolazione**  
  
## <a name="creating-a-basic-3-d-model"></a>Creazione di un modello 3D di base  
 È possibile utilizzare l'editor modello per creare e modificare modelli e scene 3D per il gioco o l'applicazione. Nei passaggi seguenti viene illustrato come utilizzare l'editor modello per creare un modello 3D semplificato di una casa. Un modello semplificato può essere utilizzato come alternativa temporanea agli asset grafici finali ancora in fase di creazione, come mesh per il rilevamento dei conflitti o come modello a basso livello di dettaglio da utilizzare quando l'oggetto da esso rappresentato è troppo distante per beneficiare di un rendering più dettagliato.  
  
 Al termine, il modello dovrebbe risultare simile al seguente:  
  
 ![Modello completato della casa semplificata](../designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Per creare un modello 3D semplificato di una casa  
  
1.  Creare un modello 3D da utilizzare. Per informazioni su come aggiungere un modello al progetto, vedere la sezione Introduzione in [Editor dei modelli](../designers/model-editor.md).  
  
2.  Aggiungere un cubo alla scena. Nella finestra **Casella degli strumenti**, in **Forme**, selezionare **Cubo** e spostarlo nell'area di progettazione.  
  
3.  Passare alla selezione della faccia. Nella barra degli strumenti dell'editor dei modelli scegliere **Seleziona icona**.  
  
4.  Suddividere la parte superiore del cubo. In modalità di selezione icona scegliere una volta il cubo per attivarlo per la selezione, quindi scegliere la parte superiore del cubo per selezionare la faccia superiore. Nella barra degli strumenti dell'editor dei modelli scegliere **Suddividi faccia**. In questo modo vengono aggiunti nuovi vertici alla parte superiore del cubo che la dividono in quattro parti uguali.  
  
     ![La parte superiore del cubo è stata suddivisa](../designers/media/gfx_model_demo_house_subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Estrudere due lati adiacenti del cubo, ad esempio i lati frontale e destro. In modalità di selezione icona, scegliere una volta il cubo per attivarlo per la selezione, quindi scegliere un lato del cubo. Tenendo premuto CTRL, scegliere un altro lato del cubo adiacente al lato selezionato per primo e nella barra degli strumenti dell'editor dei modelli scegliere **Estrudi faccia**.  
  
     ![I lati del cubo sono stati estrusi](../designers/media/gfx_model_demo_house_extrude.png "gfx_model_demo_house_extrude")  
  
6.  Estendere una delle estrusioni. Scegliere una delle facce appena estruse e nella barra degli strumenti dell'editor dei modelli scegliere lo strumento **Traslazione** e spostare il manipolatore della traslazione nella stessa direzione dell'estrusione.  
  
     ![Una lato del cubo è stato ulteriormente estruso.](../designers/media/gfx_model_demo_house_extend.png "gfx_model_demo_house_extend")  
  
7.  Eseguire la triangolazione del modello. Nella barra degli strumenti dell'editor dei modelli scegliere **Avanzate**, **Strumenti**, **Triangolazione**.  
  
8.  Creare il tetto della casa. Passare alla modalità di selezione bordo scegliendo **Seleziona bordo** nella barra degli strumenti dell'editor dei modelli e quindi scegliere il cubo per attivarlo. Durante la selezione dei bordi visualizzati qui, tenere premuto il tasto CTRL.  
  
     ![Bordi che formeranno il picco del tetto](../designers/media/gfx_model_demo_house_edges.png "gfx_model_demo_house_edges")  
  
     Una volta selezionati i bordi, nella barra degli strumenti dell'editor dei modelli scegliere lo strumento **Traslazione** e spostare il manipolatore della traslazione verso l'alto per creare il tetto della casa.  
  
 Il modello semplificato della casa è completato. Di seguito viene nuovamente mostrato il modello finale a cui è stata applicata l'ombreggiatura semplice:  
  
 ![Modello completato della casa semplificata](../designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Come passaggio successivo, è possibile applicare uno shader a questo modello 3D. Per informazioni, vedere [Procedura: Applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un modello di terreno 3D](../designers/how-to-model-3-d-terrain.md)   
 [Editor dei modelli](../designers/model-editor.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)