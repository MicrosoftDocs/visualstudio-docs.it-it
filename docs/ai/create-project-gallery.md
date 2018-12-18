---
title: Creare un progetto in Visual Studio Tools for AI
description: Creare un progetto usando un esempio dalla raccolta di Azure Machine Learning
keywords: ai, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.devlang: multiple
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 0b45aa6b2ddfb37b99f7f1d92d4d2b205e905488
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Creare un progetto AI dalla raccolta di Azure Machine Learning in Visual Studio

Azure Machine Learning è integrato con Visual Studio Tools for AI. È possibile usarlo per inviare processi di machine learning a destinazioni di calcolo remote come macchine virtuali di Azure, cluster Spark e così via. Vedere altre informazioni su [Sperimentazione di Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

Dopo aver [installato Visual Studio Tools for AI](installation.md) è facile creare un nuovo progetto Python usando i file recipe predefiniti nella raccolta di esempi di Azure Machine Learning.

> [!NOTE] 
> Deve essere installato Azure Machine Learning Workbench. Per installarlo, vedere la [guida introduttiva all'installazione di Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) 

1. Avviare Visual Studio. Aprire **Esplora server** scegliendo il menu **AI Tools** (Strumenti AI) e quindi **Select Cluster** (Seleziona cluster).  

    ![Selezione del cluster](media\create-project-gallery\select-cluster.png)

1. Accedere alla sottoscrizione di Azure Machine Learning facendo clic con il pulsante destro del mouse sul nodo **Azure Machine Learning** in Esplora server, quindi selezionare **Accesso** e seguire le istruzioni.

    ![Accesso](media\create-project-gallery\azureml-login.png)
 
2. Selezionare **AI Tools (Strumenti AI) > Azure Machine Learning Sample Gallery (Raccolta di esempi di Azure Machine Learning)**. 
    
    ![Raccolta di esempi](media\create-project-gallery\gallery.png)

1. Per questa guida introduttiva, selezionare l'esempio "**MNIST using TensorFlow**" e fare clic su **Installa**. Specificare le informazioni seguenti:

 - **Gruppo di risorse**: gruppo di risorse di Azure in cui verranno archiviati i metadati
 - **Account**: account di sperimentazione di Azure Machine Learning
 - **Area di lavoro**: area di lavoro di Azure Machine Learning
 - **Tipo di progetto**: framework di machine learning. In questo caso scegliere **TensorFlow**
 - **Aggiungi a soluzione**: determina se aggiungere il progetto alla soluzione di Visual Studio corrente o se creare e aprire una nuova soluzione
 - **Percorso progetto**: percorso in cui salvare il codice
 - **Nome progetto**: digitare **TensorFlowMNIST**
   
![Progetto risultante quando si usa il modello di applicazione Python](media/create-project-gallery/new-AzureSampleProject.png)

1. Visual Studio crea il file di progetto (un file `.pyproj` su disco) insieme agli altri file definiti nell'esempio. Con il modello "MNIST" il progetto contiene più file.

    ![mnist](media\create-project-gallery\azml-mnist.png)

1. Inviare il processo ad Azure Machine Learning. 

    ![mnist](media\create-project-gallery\submit-azml.png)

1. Eseguire in un contenitore Docker o nel computer locale

    ![mnist](media\create-project-gallery\azml-local.png)