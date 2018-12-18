---
title: Inviare un processo per eseguire il training del modello in Azure Batch per intelligenza artificiale
description: training modello cloud
keywords: intelligenza artificiale, visual studio, training modello, cloud
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: ec0db69bbde1e2abab7022759ed0f7a3d2a88530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Eseguire il training dei modelli di intelligenza artificiale in Azure Batch per intelligenza artificiale

Azure Batch per intelligenza artificiale è un servizio gestito che consente ai data scientist e ai ricercatori che operano nel settore dell'intelligenza artificiale di eseguire il training di modelli di intelligenza artificiali e altri modelli di machine learning in cluster di macchine virtuali di Azure, incluse le macchine virtuali con supporto GPU. È sufficiente descrivere i requisiti del processo, specificare dove trovare l'input e dove archiviare l'output. Tutti gli altri aspetti vengono gestiti da Azure Batch per intelligenza artificiale. [Altre informazioni su Azure Batch per intelligenza artificiale](https://docs.microsoft.com/azure/batch-ai/overview)

È integrato con Visual Studio Tools for AI, quindi è supportata la scalabilità orizzontale dinamica dei modelli di training in Azure.  Dopo aver [installato Visual Studio Tools for AI](installation.md) è facile creare un nuovo progetto Python usando i file recipe predefiniti nella raccolta di esempi di Azure Machine Learning.

1. Avviare Visual Studio. Aprire **Esplora server** scegliendo il menu **AI Tools** (Strumenti AI) e quindi **Select Cluster** (Seleziona cluster).

    ![Selezione del cluster](media\train-model\select-cluster.png)


2. Espandere **AI Tools** (Strumenti AI). Tutte le risorse di Batch per intelligenza artificiale disponibili verranno rilevate automaticamente e visualizzate in Esplora server.

    ![Raccolta di esempi](media\train-model\batchai.png)

3. Selezionare **Visualizza > Team Explorer...**  per aprire la finestra **Team Explorer** in cui è possibile connettersi a GitHub o a Visual Studio Team Services oppure clonare un repository.

    ![Finestra Team Explorer che mostra Visual Studio Team Services, GitHub e la clonazione di un repository](media\train-model\team-explorer.png)

4. Nel campo URL in **Repository Git locali** immettere `https://github.com/Microsoft/samples-for-ai`, immettere una cartella per i file clonati e selezionare **Clona**.

    > [!Tip]
    > La cartella immessa in Team Explorer è specifica per ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in Team Explorer non crea automaticamente una sottocartella con il nome del repository.

5. Dopo il completamento della clonazione fare clic su **File > Apri soluzione > Progetto/Soluzione**

    ![Raccolta di esempi](media\train-model\open-solution.png)

5. Aprire **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** nella directory in cui è stato clonato il repository

    ![Raccolta di esempi](media\train-model\tensorflowexamples.png)

5. Impostare il progetto MNIST come **Progetto di avvio**

    ![Raccolta di esempi](media\train-model\mnist-startup.png)

1. **Fare clic con il pulsante destro del mouse sul progetto **MNIST e scegliere **Invia progetto**

    ![Raccolta di esempi](media\train-model\submit-job.png)

1. Selezionare il cluster **Azure Batch per intelligenza artificiale** e quindi fare clic su **Importa**. Selezionare il file `AzureBatchAI_TF_MNIST.json` per inserire velocemente alcuni valori predefiniti, ad esempio l'immagine di Docker da usare. Fare quindi clic su **Invia**.

    ![Raccolta di esempi](media\train-model\submit-batch.png)