---
title: 'Procedura: Creare uno shader con colore di base'
description: Informazioni su come usare la finestra di progettazione shader e il linguaggio di Graph shader diretto per creare uno shader con colore flat che imposta il colore finale su un valore di colore RGB costante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b3c90496050754cc79c8bd774c0faa246e21512
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917046"
---
# <a name="how-to-create-a-basic-color-shader"></a>Procedura: Creare uno shader con colore di base

Questo articolo illustra come usare la finestra di progettazione shader e il linguaggio DGSL (Directed Graph Shader Language) per creare uno shader con colore uniforme. Questo shader imposta il colore finale su un valore di colore RGB costante.

## <a name="create-a-flat-color-shader"></a>Creare uno shader con colore uniforme

È possibile implementare uno shader con colore uniforme scrivendo il valore di colore di una costante di colore RGB nel colore di output finale.

Prima di iniziare, assicurarsi che siano visualizzate la finestra **Proprietà** e la **casella degli strumenti**.

1. Creare uno shader DGSL da utilizzare. Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione Introduzione in [Finestra di progettazione shader](../designers/shader-designer.md).

2. Eliminare il nodo **Colore punto**. Usare lo strumento **Seleziona** per selezionare il nodo **Colore punto** e scegliere **Modifica** > **Elimina** nella barra dei menu.

3. Aggiungere un nodo **Costante colore** al grafico. Nella **casella degli strumenti**, in **Costanti**, selezionare **Costante colore** e spostarlo nell'area di progettazione.

4. Specificare un valore di colore per il nodo **Costante colore**. Usare lo strumento **Seleziona** per selezionare il nodo **Costante colore** e quindi specificare un valore di colore nella proprietà **Output** della finestra **Proprietà**. Per arancione, specificare un valore di (1.0, 0,5, 0,2, 1.0).

5. Connettere la costante di colore al colore finale. Per creare le connessioni, spostare il terminale **RGB** del nodo **Costante colore** nel terminale **RGB** del nodo **Colore finale** e quindi spostare il terminale **Alfa** del nodo **Costante colore** nel terminale **Alfa** del nodo **Colore finale**. Queste connessioni impostano il colore finale sulla costante di colore definita nel passaggio precedente.

La figura seguente illustra il grafico shader completato e un'anteprima dello shader applicato a un cubo.

> [!NOTE]
> Nella figura è stato specificato un colore arancione per illustrare meglio l'effetto dello shader.

![Grafico shader e risultato in un modello 3&#45;D](../designers/media/digit-flat-color-effect.png)

Alcune forme potrebbero produrre anteprime migliori per alcuni shader. Per altre informazioni su come visualizzare in anteprima gli shader nella finestra di progettazione shader, vedere [Finestra di progettazione shader](../designers/shader-designer.md).

## <a name="see-also"></a>Vedi anche

- [Procedura: applicare uno shader a un modello 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Procedura: esportare uno shader](../designers/how-to-export-a-shader.md)
- [Finestra di progettazione shader](../designers/shader-designer.md)
- [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)
