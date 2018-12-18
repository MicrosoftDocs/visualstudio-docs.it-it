---
title: 'Guida introduttiva: Creare un progetto Python tramite Cookiecutter in Visual Studio | Microsoft Docs'
description: Iniziare a usare rapidamente Python tramite un modello di Cookiecutter in Visual Studio.
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 67cf109b0964bcb9eca104ec138f968e273111e9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Guida rapida: creare un progetto da un modello di Cookiecutter

Dopo aver [installato il supporto di Python in Visual Studio 2017](installing-python-support-in-visual-studio.md), è facile creare un nuovo progetto da un modello Cookiecutter, inclusi quelli che vengono pubblicati in GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) offre un'interfaccia utente grafica per individuare modelli, opzioni del modello di input e creare progetti e file. Questa estensione è inclusa in Visual Studio 2017 e può essere installata separatamente nelle versioni precedenti di Visual Studio.

1. Per questa Guida rapida, è necessario installare prima la distribuzione di Python Anaconda3, che include i pacchetti Python necessari per il modello Cookiecutter illustrato di seguito. Eseguire il programma di installazione di Visual Studio, selezionare **Modifica**, espandere le opzioni per **Sviluppo Python** sul lato destro e selezionare "Anaconda3" (32 bit o 64 bit). Si noti che l'installazione potrebbe richiedere alcuni minuti a seconda della velocità di Internet, tuttavia questo è il modo più semplice per installare i pacchetti necessari.

1. Avviare Visual Studio.

1. Selezionare **File > Nuovo > From Cookiecutter...(Da Cookiecutter...)**. Questo comando apre una finestra in Visual Studio in cui è possibile esplorare i modelli. 

    ![Nuovo progetto da un modello di Cookiecutter](media/projects-from-cookiecutter1.png)

1. Selezionare il modello di "Microsoft/python-sklearn-classificazione-cookiecutter", quindi selezionare **Avanti**. (La prima volta che si usa Cookiecutter il processo potrebbe richiedere alcuni minuti).

1. Nel passaggio successivo, impostare un percorso per il nuovo progetto nel campo **Create in**, quindi selezionare **Crea**.

    ![Secondo passaggio usando Cookiecutter, impostazione delle proprietà del progetto](media/projects-from-cookiecutter2.png)

1. Una volta completato il processo, viene visualizzato il messaggio "I file sono stati creati". Selezionare il comando **Apri in Esplora soluzioni** per aprire il progetto.

1. Premere CTRL+F5 o scegliere **Debug > Avvia senza eseguire debug** per eseguire il programma. 

    ![Output del progetto del modello python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedere anche

- [Uso dell'estensione Cookiecutter](using-python-cookiecutter-templates.md)
- [Creazione di un ambiente per un interprete esistente Python](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Installazione del supporto di Python in Visual Studio 2015 e precedenti](installing-python-support-in-visual-studio.md).
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations).
