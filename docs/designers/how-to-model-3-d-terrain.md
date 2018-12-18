---
title: 'Procedura: Creare un modello di terreno 3D | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cccd65c62d8b5a0f75052c3121e313507ad5d8b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-model-3-d-terrain"></a>Procedura: Modellare un modello tridimensionale
Questo documento illustra come usare l'editor dei modelli per creare un modello di terreno 3D.  
  
 Questo documento illustra le attività seguenti:  
  
-   Aggiunta di oggetti a una scena  
  
-   Selezione di facce e punti  
  
-   Traslazione delle selezioni  
  
-   Utilizzo dello strumento **Suddividi faccia**  
  
-   Aggiunta di un frame a un oggetto nell'area di progettazione  
  
## <a name="creating-a-3-d-terrain-model"></a>Creazione di un modello di terreno 3D  
 È possibile creare un terreno 3D suddividendo un piano in modo da creare facce aggiuntive e quindi manipolando i vertici in modo da creare caratteristiche del terreno interessanti.  
  
 Al termine, il modello dovrebbe risultare simile al seguente:  
  
 ![Scena 3D che illustra un modello di terreno](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
 Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Per creare un modello di terreno 3D  
  
1.  Creare un modello 3D da utilizzare. Per informazioni su come aggiungere un modello al progetto, vedere la sezione Introduzione in [Editor dei modelli](../designers/model-editor.md).  
  
2.  Aggiungere un piano alla scena. Nella **casella degli strumenti**, in **Forme**, selezionare **Piano** e spostarlo nell'area di progettazione.  
  
    > [!TIP]
    >  Per semplificare l'utilizzo dell'oggetto piano è possibile inserirlo in un frame nell'area di progettazione. In modalità **Seleziona** selezionare l'oggetto piano nella barra degli strumenti dell'editor dei modelli scegliere il pulsante **FrameObject**.  
  
3.  Passare alla modalità di selezione icona. Nella barra degli strumenti dell'editor dei modelli scegliere **Seleziona icona**.  
  
4.  Suddividere il piano. In modalità di selezione icona scegliere una volta il piano per attivarlo per la selezione e quindi sceglierlo di nuovo per selezionarne l'icona. Nella barra degli strumenti dell'editor dei modelli scegliere **Suddividi faccia**. In questo modo vengono aggiunti nuovi vertici al piano in modo che risulti suddiviso in quattro parti uguali.  
  
5.  Creare altre suddivisioni. Con le nuove icone ancora selezionate, scegliere **Suddividi faccia** altre due volte. Viene così creato un totale di 64 icone. Creando più suddivisioni, è possibile aumentare ulteriormente il livello di dettaglio del terreno.  
  
6.  Passare alla modalità di selezione punto. Nella barra degli strumenti Editor modello scegliere **Seleziona punto**.  
  
7.  Modificare un punto per creare una caratteristica del terreno. In modalità di selezione punto selezionare uno dei punti e scegliere lo strumento **Trasla** nella barra degli strumenti dell'editor dei modelli. Nell'area di progettazione viene visualizzata una casella che rappresenta il punto. Usare la freccia verde per spostare la casella e modificare l'altezza del punto. Ripetere questo passaggio per tutti gli altri punti con l'obiettivo di creare funzionalità del terreno interessanti.  
  
    > [!TIP]
    >  È possibile selezionare contemporaneamente più punti per modificarli in modo uniforme.  
  
 Il modello di terreno è completo. Di seguito viene nuovamente illustrato il modello finale con l'ombreggiatura Phong applicata.  
  
 ![Scena 3D che illustra un modello di terreno](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
 È possibile usare questo modello di terreno per illustrare l'effetto dello shader con sfumatura descritto in [Procedura: Creare uno shader con sfumatura basata sulla geometria](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor dei modelli](../designers/model-editor.md)